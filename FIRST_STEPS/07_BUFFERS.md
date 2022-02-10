# Buffers

Hi, and welcome back!

In the last lesson, we learned to work with functions of time. In this lesson, we'll apply the same technique to buffers to change where our reading starts from. This will allow us to skip around in audio files and even play them backwards.

## Buffer offset

We can change our buffer offset using the `changeBufferOffset` function, which works the same way that `changeRate` and `changeVolume` do. The major difference is that our offset will _only_ apply to the start of a sound.

In this lesson, we'll use a different pad - one that morphs quite a lot. Let's listen to the whole thing.

Using changeVolume, we can create an envelope to make the pad sound more like a synth. I'll do that using `simplePiecewise`, which we saw in the last lesson.

And we can modulate the rate using `changeRate`.

But it's a bit boring to always start at the beginning. I'll use `changeBufferOffset` to change where we start. For example, I'll start this tag at 1.0, this one at 2.0, and this tag at 3.0.

Naturally, things get more interesting once we bring functions in the mix. Let's use the same type of LFO we used in the previous lesson, except now, we'll use it to create the buffer offset. This is a great way to "drop the needle" at different points in a sound, which can create beautiful textures.

## Reversing

Messing with buffers wouldn't be complete without reversing them. Reversing is also a function of time, and like buffer offset, it only applies at the onset of a sound. For kicks, let's throw some reversing in the mix and hear how it sounds. It's pretty subtle, as the sound's profile is similar when reversed, but we can definitely hear something changing!

## Conclusion

So there you have it! This lesson was much shorter than the previous one but we increased our palette quite a lot with two new tools: buffer offset and buffer direction. This shows one of my favorite aspects of functional programming: its surface area scales fast as a function of volume. Meaning that incremental changes in the volume of your knowledge increase dramatically the surface area of what you're able to do. Here, for example, two functions open the way to entirely new musical possibilities because we are compounding on what we learned before.

In the next lesson, we'll look at how randomness can help us make generative music.
