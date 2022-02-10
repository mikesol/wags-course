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

After importing `changeVolume` and `parse_`, the next thing we'll want to do is use them. To do that, we'll go down to line 17.
