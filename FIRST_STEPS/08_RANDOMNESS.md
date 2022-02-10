# Randomness

Hi, and welcome back!

So far, we've only been working with loop-based music. In the next lesson, we'll start to widen our loops and eventually turn them into full-length works. However, in this section, we'll stay in loop-land but give us a killer tool to make them more dynamic: randomness.

For this lesson, I've loaded a bank of piano samples. Let's hear a sequence using them.

You can see that I've added a slight envelope to make the sound a bit more artificial and electronic, but otherwise the samples are unadultured piano sounds.

So far, so good - there's nothing in here you haven't seen in a previous lesson. But now, I'm going to use a not-so-secret-weapon - randomness - to give our sequence a bit more texture.

Let's start with volume: currently, everything is at an even volume, which is kinda boring. Let's liven it up by using `initialEntropy` in `changeVolume`. Initial entropy can be brought in from the environment just like `sampleTime` or `clockTime`. It will always be betwen 0 and 1 and will always stay the same over the course of the sample. This last point is important - true entropy would change every time we read it, which we don't want, as it will result in way too much jumping around. Instead, we want a single entropic value at the beginning of our sample and we want it to hold for the sample's duration. Initial entropy will do that.

Now, let's use entropy combined with clock time to change the loop itself. To do this, we'll use `changeSampleF`, which allow us to change the sample as a function of time.

We'll set up 10 functions - one for each note, and we'll add a default implementation for each one that returns a single sample as a function of clock time. There are a couple things to note here: we're modulating clock time in a loop - in this case, 120 seconds; and we're using guards for the first time. Guards allow us to suscinctly express different conditional branches to take, and we'll fill in the conditions shortly.

The last thing we need to do is to create a `preload` array. The wagpad engine scans music to download all of the samples before they start playing, but when you are choosing the samples as a functino of time, there's no way to know exactly what will play. So, we preload all of the samples. Luckily, because the samples follow a consistent naming pattern, we can use the `range` function to generate an array of numbers and the `map` function to convert them to strings.

When we press play, we should get back the same exact result we had before.

Now, let's refine each guard with different material. I'll fill them in improvising various harmonic sequences.

Let's see how they sound!

Lastly, and back to the subject of this lesson, let's work in some randomness! For certain slots, we'll use `initialEntropy` to change the note. We'll hear the difference immediately.

Now that we have our loop, the challenge is finding the right balance of graudal and abrupt changes to make it beautiful and musical. I hope you have fun extending it!

We have a loop that will change gradually over time in some ways, abruptly in others, and can go on for hours. In the next lesson, we'll look at a strategy for making our works a bit longer using a concept called the `Semigroup` and a function called `append`.
