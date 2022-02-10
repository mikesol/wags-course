# Mini-notatoin

In our first lesson, we made a simple sampler. Let's recreate it real quick.

I'm going to navigate to `https://yap.wags.fm/p/mini-notation` and replace line 11 with `hh`. This is what it sounds like.

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

## Subdivisions

Often times, you'll want to create a subdivision within a subdivision. This can be done with square brackets. Let's go back to a subdivision of two. To split the second subdivision in half, we'll use square brackets.

This is a good time to introduce error messages. We'll start with a single square bracket, and we'll see a red exclamation point. Let's see what the error is.

> Parser found a [ without a closing ]

So now let's close our bracket, and we'll hear that it compiles and gives us the new subdivision.

The bass drum occupies the first half, and the two hi hats occupy the second half. We can subdivide even further. For example, to create thirty-second notes, or demi-semi-quavers, we can add yet another pair of brackets.

Sometimes, if you have several of the same samples in a row, typing them out can get tedious. In this case, we can use the star sign followed by the number of times to make things a bit shorter to type.

## Simultaneous notes

Sometimes, it's nice to have several voices play at the same time. For example, we may want a bass drum, a snare and a hi-hat. We do this by inserting a comma between the vocies. Let's hear an example with a bass drum on beat one, a snare on two and four, and hi-hats on all the beats.

You can have voices within subdivisions as well. Let's add a subdivision that has two voices: hi-hats and a record scratch.

One thing that's very hard in conventional DAWs but is quite easy with mini-notatoin are polyrhythms, or several rhythms superposed on each other. For example, did you ever wonder what five on seven on nine sounds like? Maybe not, but we're about to find out!

## Branching

The last part of `wags` mini-notation is the branching syntax. You open the branch with a less-than sign and close it with a greater-than sign.

Branches are useful in two scenarios:
- When you want to change up a beat by having some samples alternate; and
- When you want to create a score with measures. Each measure can be thought of as a branch of the loop.

Let's explore the first strategy, where we want a smaple to alternate between three notes. We'll start with a bass drum, and then we'll add our three notes.

Branches can contain subdivisions as well. Let's add a hi-hat to the last subdivision.

In the second strategy, we can use branches to create measures in a score. I call this top-level branching. You create the branch as the first element of the score and then fill it in with measures. In this example, I'll create four measures, each of which is subtly different. Let's hear what it sounds like.

## Voices

The underlying engine powering `yap.wags.fm` has support for six simultaneous sounds on each track. Any more than that and you're out of luck. While this is fine in most contexts, we can start to hear clipping in really dense material. To avoid clipping and to organize our cycles a bit more logically, we can use one of six track slots available. Here, I'm using `earth`, but the other ones are `wind`, `fire`, `lambert`, `hendricks` and `ross`. Named after, of course, Earth Wind and Fire, and Lambert Hendricks and Ross.

## Examples

So that's mini-notation! In summary, we have three core components:

- Sequences, which are contained in square brackets;
- Voices, which are separated by commas; and
- Branches, which are created using a less-than and greater-than sign.

Using just mini-notation, we can already go quite far. Let's hear a couple examples.

The first one is one of the first I ever made in wags. I'll navigate to it and copy and paste it into our session.

This is a good time for me to mention that one of the best ways to get started with wags is copying and pasting. You can share links with your friends or check out what the community has made. Here are a few places to catch some wags.
- On the wags discourse, which is at https://discourse.wags.fm;
- On the wagsi repo, which is at https://github.com/mikesol/wagsi; and finally
- On the PureScript discourse, where folks occassionally post questions or showcase examples.

The second one is one I made while waiting for a friend in a Starbucks. I had was on my second or third coffee by that point, so it got a bit fast.

If you make something and you'd like to share it, _please_ copy and paste it onto the wags discourse at https://discourse.wags.fm. I just created it for this course, and it's pretty lonely, so it could use your work! I'll make one now called mini-notation.

By using just the samples on `https://github.com/mikesol/wagsi/blob/main/SOUNDS.md` and these techniques, I've done entire jam sessions and mixed night-long raves with people around the world. You're now able do the same, and this is only your second lesson! In the next lessons, we'll look into how to use your own samples and how to export your work. See you soon!
