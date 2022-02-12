# Effects Part 2: Delay and feedback

In the last section, we went over filterrs and reverb. Wags is a full-featured DAW, so you can do nearly anything that you can do in GarageBand or Ableton. In this section, we'll look how to create a flange with variable delay, how to create a feedback loop, and how to pan the sound. I'll also let you know where the documentation for all this lives so you can discover what effects are available and how you can import your own custom effects.

## Flange

Every now and then, we all need a good flange. So let's make one! A flange is an effect where we stack the same sound several times over with short delay lines. It's a subtle art - if the delay is too long then it stops sounding like a flange, and if there is no variation it gets old real quick. So we're tasked with the challenge of building a world-class flange. Let's get to it!

The first thing I'll do is search freesound for a speech. The nice thing about speaking is that you can really hear the flange shine. So I'll type `@w fs speech` and here are a couple speeches. I'll grab this one and store it in "mySpeech."

Now, let's set the duration to the duration of the speech and listen to it.

The actor sounds great, so it'll be fun to flange.

Now, we're going to use the same technique from the previous video where we use the functions `addEffect`, `fx`, `hello`, and `goodbye`. I'm also going to import `delay` and `lfo`. In a previous lesson we had rolled our own LFO using a sine wave, and this one is exactly the same but with a more lfo-y syntax.

The first thing I'll do is add two delay lines, one with a delay of `0.04` seconds and one with a delay of `0.05` seconds.

Already we hear our flange! But we can do better. Let's make one of these delay lines variable to create Der Uberflanger. We'll use an LFO that alternates around the `0.06` second mark with an amplitude of `0.03` seconds and a frequency of one second. Let's hear how it sounds.

Wow, that's flangy!

Here's a quick pro-tip. When you're doing these sorts of effect manipulations, the browser can sometimes miss a rendering deadline, which results in odd clicks and bloops. Thankfully we haven't heard any yet, but I find that if you delay the control rate parameter as well, you can avoid any issues without sacrificing the timing too much. It works perfectly in an effect like this, where a few milliseconds delay doesn't change our perception of the sound. So I'll import `ff` and then use it on my lfo.

Of course, nothing says we need to be tasteful. I can jack up the frequency and we'll get something that stops sounding like a flange and starts sounding like a pitch shift.

The more you work with audio, the more you'll realize that small parameter changes can lead to completely different results. This is especially true when working with poles and zeros in filters, which are extremely sensitive. But it's also true with delay, as we heard here.

## Feedback

Another fun thing we can do with delay is create an echo effect. To do this, though, we'll need a feedback loop. As an opening salvo, let's listen to this version of happy birthday, which uses delay + feedback on the melody.

Let's create a similar effect from scratch! We can use the same setup we have for our flange, but tweak it a little to get out echo.

Any feedback loop requires a signal to feed-back into itself. To do this, we'll use a new term called `ref`. At the point of feedback, we'll refer to the node being fed back using `ref`.

Let's create that node and call it `mymix`. For now it'll just be a small wrapper around our delay lines. We'll also get rid of the delay line with the lfo to simplify things a bit.

Now, in our delay line, we'll insert a `gain` node and a `highpass` filter. They'll both serve to attenuate the echo. Lastly, we'll refer to the source - namely `mymix`, at the end of the tree by pointing to it using `ref`.

And there you have it, we've got our echo line. Of course, we can spice stuff up a bit using functions of time. Let's add a few!

## Pan

Adding `pan` is relatively straightforward: we import `pan` and add it to a node just as we did with `delay`, `highpass` and `gain`. Let's hear how that sounds on this mix.

That's quite nice, we have the main voice in the center and the echo swirling around us.

## Other effects

Now you may be wondering - where can I learn more about what effects are available? Look no further than the documentation! If you navigate to `https://pursuit.purescript.org/packages/purescript-wags/docs/WAGS.Change.Optionals`, you'll see everything that's available, which is almost the whole web audio API.  You can also browse the web audio API documentation at `https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API`. There are compressors, waveshapers, oscillators, analyzers and microphones. There's even an API for custom audio nodes.

In the second part of this course, we'll learn how to use some of the more advanced features of the web audio API, like custom nodes. In the next lesson, I'd like to focus on synthetic sounds, like square wavees and triangle waves, to show you how to build custom synths on your pad. See you there!
