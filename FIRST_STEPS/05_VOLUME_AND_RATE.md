# Volume and rate

In this lesson, we're going to change the volume and rate of our samples. We'll also use a nifty feature of wags called "tags" to isolate certain samples with surgical precision.

## Programming

Before we begin, it's important to note that this is the first lesson where we're going to be diving deeper into programming. If you've been following along and are not a coder, don't worry: the concepts will be exposed one-by-one and we'll see several examples of each new concept. But it's important to mention at the outset of this lesson that we'll be writing some code, so if things feel out of reach, don't hesitate to go over certain sections a few times.

## Volume

The first thing we'll be doing is changing the volume. We'll be doing this with two functions: one called `changeVolume`, and one called `parse_`. The word function means lots of things in different contexts, but here in PureScript, the language that wags is written in, a function is conceptually quite elegant. It's something that takes an input and produces an output.

To use `changeVolume` and `parse_`, we'll have to first import them. You can see some `import` statements at the top of this file, and we'll `import` the function `changeVolume` from the module `WAGS.Lib.Tidal.Tidal`.

There are lots of little syntax things to get right here - we need to remember to add a comma between `s` and `changeVolume`. What if we forget? Let's omit the comma, press play, and see what happens. Like before, we get a red exclamation point with the following message:

```
On line 8:
  Unable to parse module:
  Unexpected token 'changeVolume'
```

So we'll always know what line to look at and we'll have a sense of where the problem is. Unfortunately, the error message isn't always ideal. For example, a clearer message could be "you forgot a comma after `s`." Many programming languages struggle to anticipate errors for everything that can go wrong because lots of things can usually go wrong. But the error messages are usually enough to know where to start looking. In this case, let's fix the error and press on.

After importing `changeVolume` and `parse_`, the next thing we'll want to do is use them. To do that, we'll go down to line 17 and after `s` we'll put `$ map (changeVolume (const 0.5)) $ parse_`. There's a lot to unpack in terms of the syntax, but let's focus on the result first. The volume will be half as loud. Let's take a listen.

We can change the volume in real-time. Let's make it very soft - `0.1`, for example.

Now, let's increase it to `1.0`.

You'll hear the volume changing in realtime for all of our samples.

Intuitively, we understand that when we change the number, the volume changes. What's much less clear is the function of the dollar signs, the word map, the word `const`, the parentheses, and the two functions `changeVolume` and `parse_`. That's what we'll take time to unpack now.

## Syntax

I've mentioned a few times that `wags` is a library in the language PureScript, so the coding language you're looking at here is PureScript. `wags` uses standard PureScript and makes no exotic modifications to the language. This means that, when you learn `wags`, you're learning PureScript and vice-versa.

In PureScript, the dollar sign is used to delay evaluation. By default, terms in PureScript are compiled eagerly - a term will consume the term after it, which produces a new term that will consume a term after that.

For example, if we write `a = add 1 2`, the add function will first consume 1 and then the result of this will consume 2 to produce to sum, or 3. If we write `b = mul 2 3`, the result of this will first consume 2 and then consume 3 to produce the product, or 6. What if we want to mix the two together? We could frist try writing `c = add 1 mul 2 3`, but you'll see this doesn't compile. Let's look at the error:

```
  Could not match type

    t0 -> t0 -> t0

  with type

    Int
```

That seems crpytic at first, but let's unpack it. We want the second argument to `add` to be a number, but instead it is receiving `mul`. `mul` is a function that takes two terms and produces a third, or in otherwords, it has the signature `t0 -> t0 -> t0`. So what the compiler is telling us is that it expects an `Int` but instead it got `mul`.

This is where the dollar sign is useful. It defers the compilation of `add` and instead compiles everything to the right of the dollar sign first. In this case, it reduces `mul 2 3` to an integer and then feeds the result to `add`. You can see that the code compiles now!

Dollar signs are often used in long chains of computations so that computation happens in the right order. We can make a really long chain of dollars if we feel like it.  But for now we'll just use what we need - no use wasting excess dollars.

One thing to note is that wrapping things in parentheses has the same effect as a dollar-sign - the PureScript compiler will evaluate the inside of the parentheses before evaluating the outside.

## changeVolume

The next thing we want to look at is `changeVolume`. Intuitively, we understand with our ears that `changeVolume` changes the volume based on a number passed to it. In the web audio API, 0.0 is silent and 1.0 is full intensity, so going between the two modulates the volume. What's less obvious is what `map` and `const` are doing in there.

Let's start with `map`. In PureScript, whenever we have some sort of container, we often want to drill down into its components and apply some transformation to each of them. `map` does that. We are drilling down into the Cycle and changing the volume for _every_ element. `map` is one of the most useful functions you'll use in programming in general, and every language has its flavor of it. PureScript uses a version of `map` that's derived from a branch of mathematics called category theory, and specifically from the definition of a `Functor`. If you enjoy discovering new ideas in math, I highly encourage you to check out these articles, which are also linked in this lesson and describe the concepts quite well [1](https://medium.com/@lettier/your-easy-guide-to-monads-applicatives-functors-862048d61610)[2](https://bartoszmilewski.com/2015/01/20/functors/).

`const` is used for values that don't change. In other words, they ignore their environment. Here, `0.5` is ignoring its environment: it doesn't care what time it is, for example. It doesn't care about anything else but itself. How rude! Later on, we'll use the environment to create some cool effects, but for now we'll stay constantly at `0.5`.

## parse_

Lastly, we have a new function, `parse_`, that we've needed to introduce. This is because `changeVolume` cannot accept raw mini-notation. The mini-notation needs to be transformed into a `Cycle` before-hand, which is what `parse_` does.

## Programming

We've covered a lot of ground here - we learned about the dollar sign, `map`, `const`, and two functions from wags called `changeVolume` and `parse_`.

When you're coding, it can often be disorienting to remember the order of functions and what they do, very similar to when you're starting out with ProTools or Logic and you need to learn about all the menus, shortcuts, and dials. There are a few strategies you can use here:

1. Copy and paste. There are hundreds of examples of wags floating around the internet. A great place to start is the wags cookbook. All of these examples can be pasted into wagpad verbatim. As you read through examples, you'll build intuition about how things work.
2. The wags documentation. Documentation for wags is published on a platform called Pursuit. The documentation is vast because you can do lots of things, but for our purposes here we're interested in the module `WAGS.Lib.Tidal.Tidal`. Browsing the documentation, we see that the inputs to certain functions are the outputs of other ones, and we can assemble them like building blocs by following the types.
3. Community. The PureScript community is always willing to answer questions and is very beginner-friendly.

## Rates

To close out this lesson, let's use the same pattern we used for volume to change the rate. We'll use exactly the same syntax, except instead of `changeVolume`, we'll use `changeRate`. You'll hear that the pitch shifts up a bit. Let's shift it down lower. And now back to the normal playback rate.

To finish this lesson, we'll discover one last function - `onTag`. `onTag` is like `map` but filters for a specific tag. You can assign tags to samples by putting a semicolon after the sample followed by its tag. Let's first add some tags to the mini-notation. And then let's use `onTag` to modulate just these elements.

Using just `changeVolume`, `changeRate` and `onTag` we can make very expressive loops quite quickly that would be more difficult to work with in a traditional DAW. As an example, let's check out this example, which I live-coded for an event in December 2021.

As it's playing, I'll change the values. See if you can hear the result in the loop.

So that's the end of the lesson! You now have two powerful sliders in your arsenal - a volume slider and a rate slider. And even more importantly, you've learned some patterns that we'll use time and time again as we're making music together. In the next lesson, we'll push these ideas one step further by modulating volume and playback speed using functions of time instead of constant values.
