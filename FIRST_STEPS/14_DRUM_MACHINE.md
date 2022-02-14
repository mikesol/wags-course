# Drum machine

In this last lesson, we're going to do something much less complex than the previous lessons, but it'll serve as a fun final project and a prelude of things to come.

As you probably know by now, I like functional progrmaming a lot, and I think it has the potential to revolutionize the music industry. A small but vocal group of functional programmers has been creating amazing work using functional tools like faust and tidal for over twenty years. I think we've just scratched the surface of new musical journeys made possible by functional programming, and in this lesson, I want to show one way to "think" functionally and translate it into music.

We're going to create a simple drum machine, and we're going to do so using something called a DSL. Let's start with the final result:

I'm going to click play and then start filling in this grid.

You'll hear that as I fill it in, beats fill in for instruments. For example, we hear the kick now on beats one and three.

Now we'll start to hear the closed hi-hat on 8th notes.

And I'll fill in a few other sounds to spice it up a bit.

Let's make the machine faster.

And slower again.

This drum machine looks like a spreadsheet or table, but in reality it's a functional program like all the other ones we've built before. Let's see how we put it together.

## Functions

We've seen lots of functions over the past few lessons, and in this lesson, we're going to create our own. The signature of the function will alternate between integers, which are just there for decoration and will be thrown away, and an arbitrary other type. I'll call the type of this function `Sig`.

`Sig` will be parameterized by two arguments: the input and output type.

Let's now create a function called `v` that will create a vector of a fixed length, in this case 16 elements. The elements can be of any type, which we represent with the type variable `a`. To implement the function, we'll throw away the placeholder ints, and then use the vector creation operator to create the vector, followed by `empty` to end the vector.

Let's also make a function `u` that behaves like `v` except it will propagate an arbitrary result in the vector when set to `true` an otherwise propagate nothing when set to false. We can do that by copying the implementation of `v` and then mapping over the result.
