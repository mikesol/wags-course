# Append

One of the most time-tested and effective ways to build up a piece of music is to put one section after another. In classical music, we use repeat. In the blues, we usually have a twelve-bar theme that repeats with variations. Pop-music has certain go-to forms like AABA. Of course, there are ways to make musical form that fall outside of this pattern - we've seen some in the last section with our random music generator, but any tool needs to be able to handle this elemental operatoin of putting one section after another.

To go on a mini-rant, I think that traditional DAWs do this really poorly. If I have a section of a song that repeats, I have to copy and paste it at a certain point, which means that from the moment it's pasted, it lives a separate life and changes from one section are not propagated to the other section without lots of plugin wizardry and finagling with settings.

In wags, there are a few different wags to smoosh things together depending on how you'd like the smooshing to go. This session's pad will be on https://yap.wags.fm/p/append. Let's get to it!

## Appending strings and symbols

The simplest type of appending we can do is of strings. We do that with the append operator, which looks like this: `<>`.

Let's append two strings and hear what they sound like, making sure to put whitespace between them.

We can append whole sequences of strings using a function called `intercalate`.

You may notice that we're no longer working with symbols. This has some added flexibility, but comes at the cost of the sound completely cutting out if there is a syntax error.

Using symbols is safer because we'll get nicer errors, but it's a bit less ergonomic to append them. We have to use a class called Append, but otherwise, the process is quite similar.

And as you can see, when there's an error, we get a better message and the music goes on.

## Appending cycles

While appending strings is a quick way to start, it is much less powerful than appending several several cycles. Let's see how to do that.

Let's start by creating some cycles using the `parse` function from before. We'll create a simple cycle with four bass drums followed by one with four hi-hats.

We can append cycles in several ways. Using the `i` function will allow us to create internal cycles within the larger cycle.

Using the `x` function will allow us to superpose them.

And using the `b` function will allow us to branch the audio.

Switching this quickly between different musical combinations is really hard in conventional DAWs, whereas code makes it easy.

## Making sequential music

Cycles are great for loop-based music, but what if we want to make something closer to a score?

We can accomplish that with the `mseq` function. `mseq` takes a non-empty sequence of notes with onset points and turns them into a score.

I'll import `mseq` as well as a function called `nl`, the tuple operator `/\`, and an operator `:|`, which is how we create a non-empty data structure in PureScript. `nl` is short for "note lazy" because it's a way to input notes for lazy people, like me.

Let's make a sequence of four samples. In this case, we can use four of the `notes` from the SuperDirt library. I'll make their onsets at 0.0, 0.333, 0.4, and 0.9. This irregular subdivision would be challenging in cycles notation but is easy in with sequences. Let's make the entire sequence a second long and hear what it sounds like.

We can modulate the volume and rate quite easily as well using `v` and `r`.

One fun trick with sequences is interlacing values. To do that, let's use the `NonEmptyArray` library, which we'll import as `NEA`.

Let's create a sequence of notes.

And a sequence of glitches.

We'll make both of them `NonEmptyArray`-s, which gives them some super powers. They become something called monads, which allows us to use something called `do` notation. I'm going to briefly do something more advanced just to give you a sense of the powerful algorithms that `do` notation allows for.

Let's start a `do` bloc with the word `do`. I'll pull one value from the first sequence, one from the second, then return them mixed together. Then, I'll map over the structure with an index using a function called `mapWithIndex`, which I'll import.

Let's use a cosine function to warp our mapping, which will distribute the notes quite densely towards the beginning and end of the sequence but sparsely towards the end.

Now, let's listen to the result!

## Sequencing futures

The last thing we'll do is append entire futures. This is a great way to combine sections of music into larger works. For those using wags as a composition environment, appending futures is a _must_. It's what allows us to work with logical sections of a piece of music.

Let's create three different futures. We can audition each one.  Here's future 1.

And here's future 2.

And here's future 3.

I call this type `AFuture` because it represents what comes next, aka the future. The term is a nod to the idea of a comonad, a powerful concept in functional programming that I'll get into during the deeper dive section of this course. For the time being, though, know that `AFuture` represents everything that will happen: rate changes, volume changes, and as we'll soon see, effects.

Now, let's combine the futures. Combining futures is as easy as combining strings. You just use `append`.

If you don't like the order of the future, no problem, just change it.

You can even create different combinations of futures and then smoosh them together too.

This gives us a way to solo out little parts of music while building up a larger whole.

## Conclusion

So there you go - we've seen how to smoosh together stuff in wags, from strings to symbols to cycles to the entire future. Now that we have killer sequences of music, let's add some effects like filters, reverb and delays in the next section. See you there!
