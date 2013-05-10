---
layout: post
title: "BrowserLoop: Remix music in your browser"
date: 2013-05-10 08:16
comments: true
categories: [Backbone.js, Coffeescript]
---
I've just finished building a tool which let's you remix loops of my band's newest single. It's build using Backbone.js and Coffeescript, and uses HTML5 audio to play back the 'loops' which make up the track. It's pretty cool, give it a try:

### [Try BrowserLoop](http://browserloop.barcodechannel.com)
<a href="http://browserloop.barcodechannel.com"><img style="width: 100%;max-width: 800px;" src="http://dl.dropboxusercontent.com/u/2324263/BrowserLoop.png"/></a>

The app works by setting up a [Clock](https://github.com/th3james/browserLoop/blob/master/src/clock.coffee) object at the BPM of the track, which then uses setTimeout() to fire a Backbone.event for each beat, which each of the [loops then listen to](https://github.com/th3james/browserLoop/blob/master/src/views/loop_view.coffee). By default, HTML5 audio does not loop seamlessly, as there is a slightly delay when seeking to the beginning of an audio file, then restarting. To get around this, I load each audio file into 2 audio tags, and switch between them with a ~50ms overlap. This isn't always completely reliable, so there is a slider to adjust this overlay at the bottom of the app

[Check out the source code on github](https://github.com/th3james/browserLoop)

Unfortunately, mobile devices (iOS etc.) don't support pre-downloading HTML5 audio and video, which means the site doesn't work on them. This is apparently done to stop users racking up data usage on 4G, as the files are only downloaded once the user clicks play. It's is a shame, because I'd have loved to use this on the iPad!

It's also worth noting, I built this using a tool I'm developing with [@amulligan](https://twitter.com/amulligan) to make building Backbone.js apps easier, but more on that later :-)
