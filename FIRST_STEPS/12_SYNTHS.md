# Synths

No DAW would be complete without a snythesizer! In this lesson, I'll show you how to make custom synths.

## Hello sine

The most basic synth we can make is a sine-wave oscillator. To do that, we'll follow the same pattern we used in the previous course on delay lines. In fact, I'll copy over that code for ease of getting started, delete what we don't need, and get a fresh start with synths. As our music will be purely snythetic for now, we no longer need a sample, so I'll use a tilde to represent a rest. Also, for now we won't be using cycles, so we can set the length to something arbitrary: I'll make it `1.0`. Lastly, we need to import a sine wave oscillator, which is called `sinOsc`.

In our mixer, we'll create two branches. The first one will send the input, which is in this case silence, to the mixer. That's an important gotchya to remember - we always need to pipe through our samples, even if they're silent. The next one will be our synth, which for now will be a very soft sine wave oscillator at 440 Hertz: we'll set it to a gain of `0.01`.

> One important thing I'd like to note is _why_ we're setting it so soft initially. Because I'm headphones, there is always the danger that I'll listen to a very loud sound I didn't intend to hear. Even if I don't have headphones, there's the potential it will be so loud that it will shock us and those around us. This can lead to very bad situations: I've seen someone startled by sound panic to get their headphones off, fall off a chair and hurt their back. I also know people that have suffered permanent hearing loss from too many incidents where they've been exposed to loud music. So, especially when working with oscillators, please start at a low volume and only ever amp it up when you're confident that the system you're building isn't too loud.

## Getting more complex

So for now, we have a single sine wave oscillator at 440 Hertz. We can build lush pads using a combination of sines, triangles, squares, sawtooths and arbitrary periodic oscillators. In general, the grittier the sound, the better it works on the low end of the spectrum because it contains lots of harmonics. Square waves, for example, work really well in the bass, whereas triangles work better on higher frequences.

Let's use a square, two triangles and two sines, all of which will be detuned slightly, and all of which will use different gain modulation.

Let's also use a bandpass filter to sweep over the middle of the spectrum.

Now we have a much more interesting synthesizer.

## Sequencing notes

One of the most fun ways to use synthesizers is sequencing notes. We can do that using normal cycle notation, inputting the notes we want. Then, we can use the `synth` function from `WAGS.Lib.Tidal.Synth` to turn this into a synthesizer. Let's do that with a major scale.

First we'll input the scale.

And then we'll add the synth. Note that we need two maps because we are mapping over a cycle and then mapping over the notes, meaning ignoring the rests. The empty record to `synth` is a set of optional parameters that we'll use to control the synth. Let's hear how it sounds!

We can make our synth more interesting by using the same methods as above. Let's use a square and a triangle wave. To create the envelope, we'll use a new function called `makePiecewiseA`. You may remember `simplePiecewise` from a previous lesson. `makePiecewiseA` is slightly more advanced in that it will make attacks more crisp. Let's make a slinky envelope that bounces up and down as it fades out.

Now, let's hear how it sounds!

## Conclusion

So there you go, using these techniques, you can create pads and synths. It's important to note that the web audio API is only as powerful as the device you're using, so very complex synths can max out older phones and computers. If you're intending to diffuse your synth to a wider audience, I'd recommend using a feature called CPU throttling in Chrome. You can enable it here, and it will simulate how your music will perform on less powerful devices.

In the next and final section, we'll change stuff up a bit by coding our own drum machine on a wagpad. In doing so, we'll see how idiomatic functional programming patterns can allow us to explore musical worlds relatively quickly and with great versatility. See you there!
