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

The thing we're trying to achieve is to ingest 16 values of the same type and return some vector of another type. So `Sig` will be parameterized by two arguments: the input and output type. Using this strategy, we'll create a measure of 16 bars _and_ a drum kit with 16 instruments. We'll use the `Sig` type for both.

Let's now create a function called `v` that will create a vector of a fixed length, in this case 16 elements. The elements can be of any type, which we represent with the type variable `a`. To implement the function, we'll throw away the placeholder ints, and then use the vector creation operator to create the vector, followed by `empty` to end the vector.

Let's also make a function `u` that behaves like `v` except it will propagate an arbitrary result in the vector when set to `true` an otherwise propagate nothing when set to false. We can do that by copying the implementation of `v` and then mapping over the result.

## Machine

We're now in a place where we can make our drum machine. On every line we'll put an index followed by an instrument with a 16-beat grid. Let's start, for example, with the number 1 and the instrument `xe3`, which is a random name I gave for one of our 16 instruments. For now I'll make everything false in the vector. Because `false` is annoying to type, let's create aliases `y` for `true` and `n` for `false`.

Great, so now I have the first vector. After this, it's rinse and repeat for the other instruments. All we'll have to change is the instrument and the index name.

- `xe3`: electr 3
- `xe2`: electr 2
- `xe1`: electr 1 
- `xe0`: electr 0
- `xdk`: dink
- `xmc`: maraca
- `xcp`: clap
- `xcb`: cowbell
- `xho`: open hh
- `xhc`: closed hh
- `xsn`: snare
- `xth`: hi tom
- `xtm`: mid tom
- `xtl`: lo tom
- `xk1`: kick 1
- `xk0`: kick 0

## Putting it all together

The last thing we want to do here is interpret our structure into something that the `s` function can read. Let's assemble a single string from our structure.

To start, we'll import `toArray`, which turns our vector into an array.
Then, we'll filter out all of the vectors with nothing in them. To do this, I'll use the `filter` function to filter out what we don't want and the `fill` function to make a vector of `Nothing`.

Then, within each internal vector, I'll change all of the `Nothings` to rests (or tildes) and the strings to normal strings. We can do this using the `fromMaybe` function. We use `map` twice because we are mapping over an array and then, within the array, over each vector.

The last thing I'll do is append all of the internal sequences using empty space, which we accomplish via `intercalate`, and then append all of the external sequences also using interacalate. For the external sequences, we'll use a comma to represent superposition.

Now, we can pass `muzak` to our renderer.

When there are no compile errors and it plays, we hear nothing. This is because we've set everything to `n` in our machine. But if we start flipping some `n`-s to `y`-s, listen to what happens. Our drum machine comes to life!

## Conclusion

This is one of many ways to use functional programming to create domain-specific languages, or DSLs, to accomplish a goal: in this case, building a drum machine. Creating and interpreting DSLs is the art of functional programming, and insofar as every piece of music has its own internal language, it's also the art of composition.

Congratulations for finishing the first course in my "Soundly functional" series! In this course, over the series of fourteen lessons, we've learned to use wagpad. Because wagpad is a full-featured DAW, you can push it really far, as we saw in several examples. In the links on the course's homepage, you'll see many examples of what's possible with wagpad, from loops to full-length works.

The second course in the soundly functional series will focus more on the functional aspect, teaching patterns in functional programming through sound. Using the musical concepts in this course, we'll learn about categories, functors, monads, algebras, adjunctions, monoids, free structures, the Yoneda lemma, and much more. By the end, you'll understand these concepts through music, and you'll be able to apply them to musical creation and to lots of other disciplines. For more information on the course, please see this course's main page.

Lastly, a reminder to please post your work on discourse.wags.fm. I'm looking forward to hearing your music!

Thank you very much for being my students, and I'll see you in my next course.
