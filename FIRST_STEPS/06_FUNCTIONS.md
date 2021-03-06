# Functions

Hi! Welcome back. In this lesson, we'll keep using `changeVolume` and `changeRate`, but we'll now use them with functions instead of constant values.

## Functional programming

Let's start off this time with just one sample from freesound.org. It'll be a gorgeous pad sound, and we'll increase the duration of our cycle so we play the whole thing. Let's take a listen.

Now, using the techniques from the last lesson, let's change the volume. We'll import the functions `changeVolume` and `parse_` and use them to change the volume. One important thing to note is that changes only apply on each new cycle, and since we're dealing with a long sound, it will get tedious to wait until a new cycle to hear our changes. So we'll be doing a bit more starting and stopping than before. In live gigs, on the other hand, I love this feature of `wags` because it allows us to prep the next cycle as the current one is playing.

I'm going to replace `const` with the following odd-looking code: `\{ sampleTime } ->`. For the time being, there's no change. But now, I'm going to import a new function called `sin` from the `Math` package. `sin` will produce a sine wave. Instead of making the volume `0.5`, let's make it `sin sampleTime` and hear what happens. Well that's kind of neat, we hear the volume going up and down following the curve of a sine wave. When the wave dips into negative territory, the underlying buffer's values flip about the `x` axis as well, but our ears don't perceive that: we just hear it getting louder again. So we hear a swelling in loudness that follows the absolute value of this curve.

Let's modify our sine wave a bit. We'll make it a function of `pi` so that its easier to work with, we'll change the frequency, we'll lower the amplitude, and we'll offset it so that it oscillates about the value `0.5`. Now what will it sound like?

As a last exercise, what if we have a sine wave modulating a sine wave? Let's plot out what that looks like in a graphing calculator. We'll use one sine wave to modulate the frequency of another sine wave. And now let's bring that back into our environment and hear what it sounds like.

This technique is often called a low-frequency oscillator, and all DAWs have the ability to use LFOs in various contexts. The power of a language like PureScript is that you can use LFOs _anywhere_. For example, Phil Freeman has made a pad that uses an LFO to modulate time itself, which is pretty wild and leads to a distribution of notes that would be really challenging in other settings. Let's listen to it.

Zooming out a bit, what we've accomplished here is that we're using the `sampleTime`, or the time a sample starts, to change the volume. Of course, you don't need to define all of these functions yourself - a lot of them are predefined in wags. Let's replace our homegrown LFO with a function called LFO that does the sample thing.

And let's listen to it.

Now, let's try out another function. This time, I'm going to use `simplePiecewise` to create a piecewise function of time.

Let's now create another piecewise function to control the rate.

We can even use the same piecewise function to modulate the rate _and_ the volume. We'll do this by storing the function in a variable called `rockstar`. And then we'll copy it in the places we use it. Because the scales won't be the same for volume and rate, we'll multiply the values and offset them differently. We do this with the `add` and `mul` functions we saw in a previous lesson as well as the function composition operator, or `<<<`, to apply these transformations.

## Composition

Let's dive a bit deeper into `<<<`, the function composition operator. Folks like me that are in functional programming tend to talk hyperbolically about every conceptual pattern as if it were the most important thing in the world, but when hard pressed, they tend to confide that composition is, in fact, the _most important_ most important thing. In simple terms, function composition applies one functino after the other. For example, `add 1 <<< mul 2` multiplies by 2 and then adds 1. Here, we use composition after the application of `rockstar`, but nothing stops us from using it before as well.

I'll write it, and before I press play, let's try to think it through. What will this composition of `mul` _before_ rockstar do to both functions. See if you can hear it in your mind's ear.

Now let's take a listen.

We heard that the volume is moving twice as fast whereas the rate is moving twice as slow.  This is because we are using composition to modulate the _input_ to the piecewise function, or time itself. In the case of volume, we're doubling time, effectively making it go twice as fast, whereas in the case of rate we're halving its speed.

The ability to have fine-grained control of time in less than ten characters is _really_ nice. I use it everywhere.

## Functions beget functions

Functional programming tends to be a bit like the movie Inception. You have a concept used inside a concept which is itself used inside a concept. So can we use a function to generate a function that will be consumed by functions? Of course we can! Check it out: I'm going to take `rockstar` and turn it into a function. Bam, now it's a function. Then, I'm going to duplicate it over our six tracks, `earth`, `wind`, `fire`, `lambert`, `hendricks`, and `ross` with different values each time. Can you hear in your mind's ear what will happen?

For each track, we've generated different piecewise functions, and we hear their inflection points alternating over time.

## Time

So far, we've been using `sampleTime`, but `wags` provides us with a lot of different times that can be used. In addition, we can use `clockTime`, which is 0 when we press play and marches forward without stopping as music continues. Let's use the same function on rate and volume but change the time and hear what happens. We can hear that, with `clockTime`, the change of rate is continuous, whereas with `sampleTime`, the rate resets to one every time the sample starts.

The versions of time you can use are:
- `littleCycleTime`, which is the time of the cycle resetting to 0 at each branch.
- `bigCycleTime`, which is the time of the cycle continuing at each branch.

Let's quickly hear those.

Continuing, we've already seen `sampleTime` and `clockTime`. Each of these has a variant that's normalized between 0 and 1. For example, `normalizedSampleTime` is 0 when the sample starts and 1 when the cycle ends.

`normalizedLittleCycleTime` and `normalizedBigCycleTime` behave the same way. There's also a `normalizedClockTime` that is between 0 and 1, where 0 is when the piece starts and 1 represents the end of time. Literally, the end of time, meaning when time immortal will cease. If you want to know when time will cease, use this value, but be warned that there may be rounding errors.

## Putting together functions

Sometimes, we'd like to add an LFO to another LFO or multiply an LFO with a piecewise function. To do this, we use the two operators `<$>` and `<*>`. I'll be going much more into what these two operators do in the second Soundly Functional course, but for this course, just know that they allow you to combine together two functions. For example, let's multiply an LFO by a piecewise function to taper it off over time.

So that's it! We've used functions of time to bring our loops to life. Let's end with a little example - it's an extract from a larger work. Let's jam by changing the functions of time and hearing what the result sounds like. I'll see y'all in the next lesson, where we'll discuss buffers.
