# Append

One of the most traditional, time-tested, and effective ways to build up a piece of music is to put one section after another. In classical music, we use repeat. In the blues, we usually have a twelve-bar theme that repeats with variations. Pop-music has certain go-to forms like AABA. Of course, there are ways to make musical form that fall outside of this pattern - we've seen some in the last section with our random music generator, but any tool needs to be able to handle this elemental operatoin of putting one section after another.

To go on a mini-rant, I think that traditional DAWs do this really poorly. If I have a section of a song that repeats, I have to copy and paste it at a certain point, which means that from the moment it's pasted, it lives a separate life and changes from one section are not propagated to the other section without lots of plugin wizardry and finagling with settings.

In wags, smooshing together things, or appending them, is done using the standard PureScript append operation, or `<>` for short. This makes working with sections of music easier than a lot of other settings. Let's see how!

## Appending cycles
