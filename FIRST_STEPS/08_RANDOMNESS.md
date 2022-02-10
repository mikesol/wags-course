# Randomness

Hi, and welcome back!

So far, we've only been working with loop-based music. In the next lesson, we'll start to widen our loops and eventually turn them into full-length works. However, in this section, we'll stay in loop-land but give us a killer tool to make them more dynamic: randomness.

For this lesson, I've loaded a bank of piano samples. Let's hear a sequence using them.

You can see that I've added a slight envelope to make the sound a bit more artificial and electronic, but otherwise the samples are unadultured piano sounds.

So far, so good - there's nothing in here you haven't seen in a previous lesson. But now, I'm going to use a not-so-secret-weapon - randomness - to give our sequence a bit more texture.

Let's start with volume: currently, everything is at an even volume, which is kinda boring. Let's liven it up by using `initialEntropy` in `changeVolume`. Initial entropy can be brought in from the environment just like `sampleTime` or `clockTime`. It will always be betwen 0 and 1 and will always stay the same over the course of the sample. This last point is important - true entropy would change every time we read it, which we don't want, as it will result in way too much jumping around. Instead, we want a single entropic value at the beginning of our sample and we want it to hold for the sample's duration. Initial entropy will do that.

Now, let's use entropy combined with clock time to change the loop itself. To do this, we'll use `changeSampleF`, which allow us to change the sample as a function of time.

...

And voila! We have a loop that will change gradually over time in some ways, abruptly in others, and can go on for hours. In the next lesson, we'll look at a strategy for making our works a bit longer using a concept called the `Semigroup` and a function called `append`.
