Using Swift Code in an Objective-C Framework


I have an Objective-C framework which was written before Swift but these days I mostly write code in Swift. I want to reuse some of the Swift code in my Objective-C framework but the question is how to do that? How to add Swift code in an Objective-C framework? How to use that Swift code in an Objective-C class after adding? These are some of the questions I will answer. I wanted to share this as most of the blog posts are on adding Swift code in an Objective-C project not framework.

## Adding Swift File

First Step is to add a new Swift file in an Objective-C framework. Remember to add it in the Framework not project (Example project).

Once that gets done then you can add your Swift code in that file. For example create a view and change it's background color:

<!-- Add an image -->

Note: If it was an Objective-C project then you would have seen a popup for adding a bridging-header but in the framework you don't get this option. I wasted a lot of time in this as I read it in many forums and blog posts that you get a popup. I even created a bridging-header manually but it's not required.

## Build Settings

Next step is to change this setting: `Always Embed Swift Standard Libraries` to `Yes` in the target's build settings.
<!-- Add an image -->

After that change this setting: `Defines Modules` to `Yes` if it is `No`. It is present in the Packaging section of target's build settings.
<!-- Add an image -->

You can build the framework and the example project where you are using this project it should build successfully.

## Using Swift Code

The import statement in the objective-c file, where you using the Swift code, should be like this:

`#import <ModuleName/ModuleName-Swift.h>`

It will be same when using the Swift file outside the framework. This(`ModuleName-Swift.h`) header file contains interface for all Swift declarations.

Now you can initialize the class which you created in the Swift file.

<!-- Add an image -->

## Accessibility

Before you call the Swift code in an Objective-C file, keep in mind not everything is accessible. Swift declarations marked with the public or open modifier will be accessible.

Not all the Swift features will work. Read more on that on Apple's docs.
