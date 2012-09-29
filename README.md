# Android's Snake example modified for touch screens

## Introduction

I have been reading a lot about Android development for the past years, 
so I decided it was about time to give it  try. I downloaded:

- Eclipse Mobility, Juno release (http://www.eclipse.org/downloads/)
- Android SDK (http://developer.android.com/sdk/index.html)

After following Android home page first steps, I created a new Android
Sample Project. I selected the Snake example from the list.

Next I connected my Samsung Galaxy Mini via USB port and clicked on Run
As -> Android Application on Eclipse. It just worked.

Well, kind of. A welcome screen prompted to press the Up key. My phone
doesn't have an Up key. What to do? Get my hands dirty, of course.

## Packaging the application

Eclipse features a menu for packaging the application into an .apk file.
This file can then be installed via USB into the phone. It's great.

All you have to do is right click on Eclipse's project -> Android Tools -> Export
Signed Application Package. This will show a wizard to create a keystore and acertificate to
digitally sign your application, and then save the .apk file.

Finally, go to ANDROID_SDK/platform-tools/adb install file.apk

## Version 1.0: Making it work with touchscreens

And this is one of those many occasions that you just don't need to know
how things work in order to make a little change to the code. Just looking
at the code can get you through some quick hacking.

I spotted a piece of code on SnakeView.onKeyDown() method that controlled
the initial screen and the Snake motion. Exactly what I wanted.

Then I crawled up the SnakeView class hierarchy and found android.view.View.onTouchEvent().
I copied some code from the onKeyDown() method and that's it.

The snake moves clockwise with every touch of the screen, which is quite simple.

## Version 2.0: Extracting the game core from the Android stuff

I was so excited that I thought it would be fun to code the snake game from
the ground up doing test driven development (TDD) and then integrate that core
to make it work in Android.

You'll notice a "libs" folder with the game core JAR file in it. You can find the source
code at https://github.com/mefernandez/snake-game-code-kata.

The process for integrating both projects is quite simple but I find it very interesting.
At first, I didn't know where to start, or how to do this integration. So I followed a
rule consistently throughout the process: Comment every line that smells like code logic. 

First thing, I realized that the _SnakeView_ class contained the code I wanted to replace.
I began commenting out every single line of code dealing with the game's logic.
The key point is not caring much for breaking the code. If the code line does game logic,
just comment it out. 

Though it may seem a naive way of integrating the game core, it actually worked quite well!

In this version I left the commented code for you to see the integration process. 
The comments begin with TODO. I'll remove these in the next versions.
