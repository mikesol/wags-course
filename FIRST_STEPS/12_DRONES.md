# Drones

Hi! In this lesson, I'd like to work with drones. If you're working with loop-based music, drones are a great way to keep a loop grounded. They're also ways to change intensity gradually over time, which is great for longer sets like raves. Let's dive right in.

## Hello drone

There are two drone channels called `water` and `heart`. In this section, we'll use both `water` and `heart` for two different drones, and we'll use `earth`, `wind`, and `fire` for the sample-based music on top of them. For now, we'll just use rests, but we'll fill these in later.

The easiest way to get a drone going is to use `parse`, which we've used before to create a cycle from a string, along with `c2d`, which is short for "cycle to drone." We'll import `c2d` from `WAGS.Lib.Tidal.Cycle` and add it to the `heart` channel. For my drone, I'm going to import the drones sample pack from `WAGS.Lib.Sounds.Drones` and use one called `lowdark`. You can also import your own drones using the import techniques we saw in the "bring your own sounds" lesson.

Now, when we play our pad, we hear the drone. Note that, if we update our cycles with samples, the drone continues unabated.

This allows us to change our looping cycle while maintaining a steady drone underneath.

## Modifying our drone

We can use similar effects on our drones as we do on our cycles. For our drones, we no longer have a notion of cycle time, so we can only use `clockTime`. Let's change the volume as a function of time. I'll do this with the `changeDroneVolume` function.

Let's also change the rate using `changeDroneRate`.

Finally, we can add an entire effect chain using `addDroneEffect`, `fx`, `goodbye`, `hello`, and whatever effects we want. Here, I'll use a low-pass filter.

Note that, when we modify our drone, the changes take effect immediately. This is rarely what we want. Often times, it's much nicer to have a gradual change between the current state and some future state. Let's see how to do that with the volume of a drone. The same technique is possible in principle for any parameter governing a drone, including effects.

## Gradual changes

To apply a gradual change, we'll use a function called `set` from the `Data.Lens` package and a value called `ldv`, which is short for "lens from drone to volume." We'll set this lens with a fade-in from 0 to 10 seconds. Let's hear what that sounds like.

Now, let's do the same thing, but fading out instead of fading in.

Notice the gradual change over time. Had we not faded in and out, we would have heard an abrupt change, which doesn't work well with drones.

In addition to fades, we can also have oscillators. The function `oscWarp` allows you to gradually warp an oscillator's frequency and waveshape as it goes between 0 and 1.

Now, let's change the frequency.

Again, we hear that the oscillator picks up where it left off without an abrupt transition.

Let's try one last value, this time using a filter. Note that lookback operations on filters and effects are slightly more computationally expensive, so to avoie artifacts, you'll want to limit the number or these. We'll use the same syntax for fadeIn, except we'll apply it to the effects chain using `ldt` and we'll precede our fade by a function that finds the specific filter we want to operate on - in this case, `usingSetFrequency` of the filter `myfilt`. Now, we can hear the fade of the frequency, and we can fade it down as well over time. Note that the same technique can be applied to global effects chains using `lvt` instead of `ldt`.

## Conclusion

So that's it for drones! 

In the next lesson, we'll focus on synthetic sounds, like square waves and triangle waves, to show you how to build custom synths on your pad. See you there!
