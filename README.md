# Android's Snake example modified for touch screens

## Introduction

I have been reading a lot about Android development for the past years, 
so I decided it was about time to give it  try. I downloaded:
- Eclipse Mobility, Juno release
- Android SDK

After following Android home page first steps, I created a new Android
Sample Project. I selected the Snake example from the list.

Next I connected my Samsung Galaxy Mini via USB port and clicked on Run
As -> Android Application on Eclipse. It just worked.

Well, kind of. A welcome screen prompted to press the Up key. My phone
doesn't have an Up key. What to do? Get my hands dirty, of course.

## Modifying the code

And this is one of those many occasions that you just don't need to know
how things work in order to make a little change to the code. Just looking
at the code can get you through some quick hacking.

I spotted a piece of code on SnakeView.onKeyDown() method that controlled
the initial screen and the Snake motion. Exactly what I wanted.

Then I crawled up the SnakeView class hierarchy and found android.view.View.onTouchEvent().
I copied some code from the onKeyDown() method and that's it.

The snake moves clockwise with every touch of the screen, which is quite simple.

## Packaging the application

Eclipse features a menu for packaging the application into an .apk file.
This file can then be installed via USB into the phone. It's great.

All you have to do is right click on Eclipse's project -> Android Tools -> Export
Signed Application Package. This will show a wizard to create a keystore and acertificate to
digitally sign your application, and then save the .apk file.

Finally, go to ANDROID_SDK/platform-tools/adb install file.apk

 