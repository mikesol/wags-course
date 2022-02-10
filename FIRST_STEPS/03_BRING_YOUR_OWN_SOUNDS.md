# Bring your own sounds

Very quickly when working with wags, you'll want to import your own sounds. There are a few ways to do that, and this lesson will cover them. I'll do it all from a pad called `byos`, for "bring your own sounds."

## Chat

The first way is to use the chat window to interact with wagbot. Wagbot can be called by typing `@w`. In this lesosn, we'll search FreeSound for some new sounds using the `fs` directive. So let's find a kick drum. We'll time `@w fs kick`. You can see that we get lots of options back. We'll choose one at random and copy the URL.

Now, I'll place this URL in the array with the `"hello"` sound. Let's call it `"myKick"`. Sounds can be named with a combinations of uppercase letters, lowercase letters and numbers. Make sure to put `myKick` in quotation marks. This is called a `String` in PureScript, the programming language used in wags. We use the forward-slash back-slash as a separator before the URL, followed by the URL in quotation marks.

One important thing to note: the file format matters here. If you're using Firefox or Chrome, you can play `ogg` files without any issue. However, Safari doesn't support them yet, so you'll have to change `ogg` to `mp3`. `ogg` files sound better than MP3 files in general, so it's up to you if you want to have Safari support at the expense of slightly-worse-sounding samples.

Now, let's listen to `myKick`. We hear the sound from FreeSound.

If we want to change it, we can paste in a different URL.

If we want to keep both of them, we can create two sounds: let's say `myKick1` and `myKick2`.

We can develop a whole kit this way. Let's get a snare. A hi-hat. A clap. And, of course, a cowbell.

You can search for exotic sounds as well. I'll search for alien and use one of the shorter sounds, let's see what comes out!

## Import

You can import sounds by clicking on the import sound button and then using one of the import options. I'll use drag and drop from sounds made by Eliot Lipp & Michna in Samples Unlimited. You can purchase these from samplesunlimited.com - I really like their work.

We'll see that there's a chat message with the URLs of the uploaded sounds. Let's call them `su0`, `su1` and `su2` for samples unlimited. Now, we can hear what they sound like.

One important thing to note is, if you're using samples that aren't open source, make sure to either keep your pad private or to check the terms and conditions of the sample library you're using. While the URL of the uploaded samples is unguessable, once it's in a pad, anyone can download the sample.

## Recording

The last way we can get samples into our pad, and my personal favorite, is recording them. I have all sorts of kitchenware and toys around the house that I use for material. This toy is great, for example. I'll click on record, do a little jam session, and then click **Stop recording**. Then, I'll edit the sound and click upload. Just like before, a URL will come up for both a WAV and an MP3. I'll use the MP3 for faster downloads.

While the Web Audio API is quite powerful, it is still lacking in its recording capacities. For example, if you're recording from multiple microphones or if you want to use a very high sample rate, this is not yet powerful. So, for one-off samples and licks, using wags is great. Otherwise, I'd recommend using a desktop recording tool like Audacity and then using the Import functionality to upload the file.

## Wrapping up

So that's how to get sounds into your pad! One last thing I'd like to mention is that, if you're jamming with friends or live-coding a set, all of this can be done on the fly. I'll fire up my pad, grab a sound from freesound, add it to my sounds, and add it to the pad. The same goes for import and recording. This is a really powerful technique, and I encourage you to make use of it during your own jams!

In the next lesson, we'll go over how to export your pad to an audio file.
