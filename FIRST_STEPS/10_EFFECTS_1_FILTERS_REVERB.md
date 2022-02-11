# Effects Part 1: Filters and Reverb

In the last section, we saw how to build long form works on wags from simple primitives.

In this section, we're going to add some filters and reverb.

## Filters

From my experience, I've found that filters are the secret sauce of most great music. You can have light reverb and light compression, but what will take a mix from good to amazing is how you use filters. It's also the way to create some of the most interesting and powerful effects.

As our base sound, let's find something rich in harmonics on freesound. I find that vacuum sounds are great for this, so let's grab a vacuum and add it to our session. I'll search for `@w fs vacuum`. Then I'll take this result, paste it into the sounds list, change the duration to be the duration of the sample, and play it back.

To create effects on our pad, we'll need at least four imports: `hello`, `goodbye`, `addEffect`, and `fx`. The easiest effect chain we can create is `addEffect (const $ fx $ goodbye hello)`. This is a no-op that takes the input `hello` and pipes ot to `goodbye`. So now that we have a chain, let's insert a simple highpass filter. We can write `goodbye $ highpass 2000.0 hello` and we'll hear the highpass filter kick in.

Let's create a filter that changes as a function of time. Instead of `highpass`, we'll use `bandpass`, and we'll modify the `q` parameter. To do this, we'll pass the following parameter to `bandpass`: `{ freq: 1000.0, q: calcSlope 0.0 1.0 5.0 20.0 (clockTime % 5.0) }`. We'll also need to change `const` to `{ clockTime }`, the same way that we've done for our volume and rate control. Let's hear what it sounds like.

As the `q` value gets higher, the frequency band gets narrower and we hear a tone emerging.

One very effective technique is to create a bank of bandpass filters, each with a subtly different swelling sound. So now I'm going to copy and paste my bandpass four times into a global `gain` and give each one a name, `bp0`, `bp1`, `bp2`, and `bp3`. I'll tweak each `calcSope` to have different periodicity, and I'll set the frequency at different places in the spectrum. Let's hear the result.

The web audio API provides eight different types of biquad filters: high pass, low pass, high shelf, low shelf, bandpass, notch (which is a band-reject filter), allpass (which let's all frequencies through but modifies the phase of sounds) and peaking, which is an advanced filter that can act simulatenously and bandpass and bandreject depending on the gain parameter. Wags exposes all of them. For example, we can change one of these filters to `lowpass` and another to `notch`. Let's hear the result!

## Reverb

Now, we'll move onto reverb. Reverb in web audio is done through a technique called convolution. Convolution is a mathematical operation of two signals that pass by each other in time. To our ears, the shape of one signal is printed onto another signal across its duration. In this case, we're going to take a signal that's called an impulse response and use it for the convolution.

The first thing I'll do is add my impulse response to the sounds list. I'll use an impulse response from Reverb.js, an open-source project that provides lots of amazing impulses. To actually improt the sounds, I'll use a CDN called jsdelivr. The URL for abernyte grain silo, for example, will be https://cdn.jsdelivr.net/gh/andibrae/Reverb.js/Library/AbernyteGrainSilo.wav. I'll call this sample "grain."

Let's listen to the raw sample first.

We can hear that it's a burst of noise that reverberates in a grain silo. This is the effect we're going to print onto our sound. I'll also find something a bit drier from freesound. I love the sound of speak and spells, so let's look for one. `@w fs speak n spell`, and we'll grab this one and call it "speaknspell."

To actually use the convolution, we'll replace `clockTime` with two new parameters: `buffers`, which is where our convolution sample lives, and `silence`, which is a silent sample in case our buffer fails to download. Putting it all together, we call `convolver (maybe silence _.buffer.forward (lookup "grain" buffers))`, where `lookup` is from the `Foreign.Object` package. The `forward` indicates that we want to use the convolution sample from front to back.

Let's hear what it sounds like.

There you go! Our speak n spell is in a big grain silo.

Using this technique, we can get a host of industry-grade reverbs out of the box.

## Conclusion

In this lesson, we added filters and reverb to our project. The effects don't stop there, though. In the next section, we'll look at delay lines, feedback loops, and panning. I'll also let you know where you can find documentation for these audio units.
