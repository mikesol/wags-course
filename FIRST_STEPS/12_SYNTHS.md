# Synths

No DAW would be complete without a snythesizer! In this lesson, I'll show you how to make custom synths.

## Hello sine

The most basic synth we can make is a sine-wave oscillator. To do that, we'll follow the same pattern we used in the previous course on delay lines. In fact, I'll copy over that code for ease of getting started, delete what we don't need, and get a fresh start with synths. As our music will be purely snythetic for now, we no longer need a sample, so I'll use a tilde to represent a rest. Also, for now we won't be using cycles, so we can set the length to something arbitrary: I'll make it `1.0`. Lastly, we need to import a sine wave oscillator, which is called `sinOsc`.

In our mixer, we'll create two branches. The first one will send the input, which is in this case silence, to the mixer. That's an important gotchya to remember - we always need to pipe through our samples, even if they're silent. The next one will be our synth, which for now will be a very soft sine wave oscillator at 440 Hertz: we'll set it to a gain of `0.01`.

> One important thing I'd like to note is _why_ we're setting it so soft initially. Because I'm headphones, there is always the danger that I'll listen to a very loud sound I didn't intend to hear. Even if I don't have headphones, there's the potential it will be so loud that it will shock us and those around us. This can lead to very bad situations: I've seen someone startled by sound panic to get their headphones off, fall off a chair and hurt their back. I also know people that have suffered permanent hearing loss from too many incidents where they've been exposed to loud music. So, especially when working with oscillators, please start at a low volume and only ever amp it up when you're confident that the system you're building isn't too loud.

So for now, we have a single sine wave oscillator at 440 Hertz.
