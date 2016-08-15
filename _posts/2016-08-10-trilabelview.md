---
layout: post
title: TriLabelView - A triangle shaped corner label view for iOS written in Swift.
excerpt: "You can use this view when you specifically want to show any item which is different or it has some different property"
modified: 2016-08-10
tags: [iOS, UI]
comments: true
pinned: true
---


I started this project last month and idea about this came up when I was checking some design related repositories on Github. This is very similar to <a href=" https://github.com/tholman/github-corners">Github Corners</a> but here text is displayed on corner label.

So you can use this in the  table view or collection view or any other view when you specifically want to show any item which is different or it has some different property. One particular use case will be when you have added some new items to your collection and you want your user to notice it then this will be a good way to do so.

You can customise this label view according to your use like changing background color or text color. You can update the size using the `lengthPercentage` property which basically is the x percent of parent view's height or width depending upon which is minimum between them. You can also update the position where it is getting displayed like `topRight` or `bottomLeft`.

There are some other properties which you can customise. You can use it from the storyboard or from code both work fine.
You can check the demo app which I have created with this library on Github.

<img src="/img/trilabelview-screenshot.png" alt="Screenshot">

You can check the repository <a href="https://github.com/mukeshthawani/TriLabelView">here</a>. 😎
