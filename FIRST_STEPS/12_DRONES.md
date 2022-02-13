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

Note that, when we modify our drone, the changes take effect immediately. This is rarely what we want. Often times, it's much nicer to have a gradual change between the current state and some future state. To do that, we use a function called `derivative`.

## Derivative

## Conclusion

In the next lesson, we'll focus on synthetic sounds, like square wavees and triangle waves, to show you how to build custom synths on your pad. See you there!
