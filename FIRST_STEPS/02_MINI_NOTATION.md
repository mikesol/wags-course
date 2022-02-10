# Mini-notatoin

In our first lesson, we made a simple sampler. Let's recreate it real quick.

I'm going to navigate to `https://yap.wags.fm/p/mini-notation` and replace line 10 with `hh`. This is what it sounds like.

`hh` is one of hundreds of sounds bundled with wags. It comes from the SuperDirt sample library, an open-source library of really nice samples. To see the full list of available sounds, check out `https://github.com/mikesol/wagsi/blob/main/SOUNDS.md`.

For example, on this page there is a tabla sound. Let's listen to it.

Now, let's listen to some of the other tabla sounds.

There's also a nice glitch library.

And there's some fun synthetic vocals as well.

## A brief history lesson

Mini-notation has a long, interesting history. There are many different projects that use a form of mini-notation, the most popular one being the Tidal Cycles project that coined the term. Tidal's mini-notation was heavily influenced by the work of Bernard Bell. If you have time, I'd recommend checking out his seminal essay [Time and musical structures](https://www.academia.edu/48080458/Time_and_musical_structures) - I've provided a link in this lesson.

## Loops

With mini-notation, we're going to carve up time in a novel way. We're going to fix the duration of a cycle - for example, one second, 1.5 seconds, or two seconds. When we change the duration, the cycle will get longer or shorter. Let's hear what that sounds like.

First I'll increase the duration to two seconds, and we hear that the cycle loops every two seconds.

Now I'll decrease the duration to 0.5 seconds, and we hear that the cycle loops every 0.5 seconds.

And let's go to one second, which we'll use for the next few examples.

## Sequences

We can add new elements to the cycle by adding whitespace or a newline followed by the new element. It's important to note here that adding a new element does _not_ change the duratoin of the cycle. It creates a new subdivision. In the current cycle, the subdivision is one. When I add a new element, like a bass drum, the subdivision will change to two. In other words, we are dividing our second evenly into two half-seconds, and we hear that.

You can subdivide to your heart's content! Let's get triplets. Sixteenth notes, or semi-quavers. Quintuplets. Sextuplets. And let's change some of the samples.

Of course, music is much more interesting with silence. You can insert silence by adding a tilde.

And to make things completely silent, you can just put a tilde.

## Subdivision

Often times, you'll want to create a subdivision within a subdivision. This can be done with square brackets. Let's go back to a subdivision of two. To split the second subdivision in half, we'll use square brackets.

This is a good time to introduce error messages. We'll start with a single square bracket, and we'll see a red exclamation point. Let's see what the error is.

>>> Parser found a [ without a closing ]
