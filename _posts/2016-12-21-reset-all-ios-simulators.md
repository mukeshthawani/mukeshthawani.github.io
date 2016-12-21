---
layout: post
title: How to Reset all iOS Simulators
excerpt: "When you run the app on simulator, it stores your app data and if you want to delete that data then you have to delete the app"
modified: 2016-12-21
tags: [xcode, iOS, simulator, command line]
comments: true
---

Today I was playing with UI testing on xcode to take screenshots using fastlane. Normally I don't use many simulators to run the app but to my surprise, it was present on 3-4 simulators, that means at some point in time I had tried it on all these simulators and I got to know about it when I was running the UI tests on different simulators.

When you run the app on a simulator, it stores your app data and if you want to delete that data then you have to delete the app from that simulator. It's ok to delete the app when you're trying it on one simulator but if you've to repeat that on 4-5 simulators then it is a time-consuming process. It would be better to reset all these simulators using just one command and we do have that command:

use `xcrun simctl list`
to get the list of all simulators.
<img src="/img/reset-all-simulators_1.png" alt="xcrun simctl list">

And then `xcrun simctl erase all`
to reset all the simulators i.e to remove all the data.

First quit the simulator then use this command otherwise you will get an error like this
<img src="/img/reset-all-simulators_2.png" alt="xcrun simctl erase all">

You can use this for UI testing where you want to test your app on a fresh install. So just run this command from the terminal before capturing screenshots (you can do that using fastlane).
