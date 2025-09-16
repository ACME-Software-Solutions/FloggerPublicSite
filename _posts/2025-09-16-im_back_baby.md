---
title: "Hacking Up an iOS App"
date: 2025-09-16 09:00:00 -0500
excerpt: "After a summer break, diving back into development by building an iOS app for Flogger - a life logging tool. Learning Swift by doing, focusing on HealthKit integration and basic data collection."
images:
  hero: "/uploads/blog/2025-09-16/im_back.png"
---
## Or, "Escaping Tutorial Hell by Just Doing It"

### I'm back, baby!

It's been a **heck of a summer** and it feels like I've not had a spare moment to dedicate to a side project.  Excuses, excuses.  I've not stopped thinking about this project all summer, and I'm super excited to jump back in with both feet.  I'm unapologetically committed to writing the client apps in Swift.  

I know that conventional wisdom says you should cast the widest net, especially when starting an indie project.  I dunno.  I guess I'm more interested in *learning* than *delivering*.  I mean, I **do** want to finish this project, to get it out into the wild and see how people use it, but I'm less interested in maximizing.  More about the journey than the destination, maybe?  A focus on craft?

#### I don't know how to write an iOS app, so I'm going to write an iOS app

It's a bit intimidating, really, and it's an easy trap to fall into: do [One Hundred Days of Swift](https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://www.hackingwithswift.com/100&ved=2ahUKEwjQy_Wf-N2PAxUWJNAFHZ02It0QFnoECA0QAQ&usg=AOvVaw3Fq0kbxX9_DRO2c0xSRGA6) or maybe go through a [book](https://books.apple.com/us/book/the-swift-programming-language-swift-5-7/id881256329) or [two](https://books.apple.com/us/book/develop-in-swift-explorations/id1511184149).  Hold up, don't get me wrong.  I mean no disrespect at all.  It's just that I don't have time to dedicate a hundred days to doing exercises.  I'll just catch as catch can.  I'm **100 percent certain** I will end up with a **terrible** app that I'll probably end up rewriting entirely, but the idea is it'll teach me what I need to learn.

#### The MVP: What is Flogger? What will the iOS app do?

Flogger aims to be a one stop life logging tool.  It should allow you to quickly record lots of things during the day: your current mood, any physical symptoms you might be having, water intake, etc.  It'll also bring in other HealthKit information, like your sleep, exercise and other activity, etc.  The idea is that it puts all the pieces together for you, and gives you some advice on how to plan out your day, maybe tweak your habits ever so slightly.

The iOS app's main purpose is to aggregate a lot of that data collection, in a single place which is easy for you to quickly record, "I drank 20oz water," or "Feeling sluggish," or, "My shoulder is really hurting today".  Eventually, we'll want to allow the user to record this stuff just using their voice.  For the MVP, we'll stick to a more traditional app interface, and we'll not implement any new data types - just stick to the HealthKit stuff.

Fundamentally, here's what the app has to do:

1. Retrieve a list of capabilities from the server.  Initially these will be basic HealthKit data types, but in the future, we'll add some custom ones.  For MVP, we'll choose 3 data types: **water intake**, **state of mind**, and **alcohol consumption**.
2. Allow the user to record one of the above 3 data types.
3. Display some sort of history, by data type and by a calendar view

#### How am I gonna do it?

I have only the vaguest idea at this point.  I went through Apple's [Scrumdinger tutorial](https://developer.apple.com/tutorials/app-dev-training/getting-started-with-scrumdinger), so that, in combination with [Gemini CLI](https://github.com/google-gemini/gemini-cli) to help me understand when things break should get me most of the way there.  

Wish me luck!
