--- 
title: "Everyone's having fun vibe coding but me"
date:   2025-06-10 09:00:00 -0500
excerpt: "Everyone's talking about 'vibe coding' with LLMs, but as a tech lead building Flogger, I found it didn't match my development style. While exploring Swift and WatchOS development, I discovered that LLMs work better as conversational partners than code generators. Here's what I learned about finding the right balance between AI assistance and hands-on coding."
images:
  hero: "/uploads/blog/2025-06-11/vibing.png"
---

## But I don't want to learn Swift right now!

As a backend developer, my first impulse when launching the MVP build of [Flogger](/2025/05/29/the_idea.html) was to create the API.  That's where a lot of the fun stuff happens! I'm using an LLM to route the user's commands to the proper handlers so that when you say, "Glass of water," or "Feeling pretty optimistic this morning," it'll know to log 8 ounces of water or a positive mood.  I'm reading about data analytics algorithms like k-means clustering: assuming a suitable amount of data (lots of "ifs" in there), I should be able to predict the effect of a sleepless night, or the recovery time after a hard workout with proper (or improper) hydration.

Before I can really do any of that, though, I need to know that I can build a front end application which meets my needs.  Because I am interested in app response time and performance, I'm looking into native iOS and WatchOS.  This means learning Swift.  I don't want to learn Swift right now.  "Maybe," I thought, "this is a good opportunity to check out this 'Vibe Coding' thing that folks are talking about these days."

## Peep the vibes

So I use an LLM on a daily basis in my work.  My current weapon of choice is GitHub Copilot in my IDE, usually running some flavor of Anthropic LLM.  I cannot overstate the boost that the LLM has given me over these past [two](two) years or so.  I don't really have it generate code for me, rather I have a long-running conversation with it about the decisions I make.  "What do you think about this approach?" "Can you spot any edge cases in this logic here?" "Will you please take a look at this PR before I request code review?" 

Times when I have asked the LLM to generate a solution for me have always left me wondering if I had just wasted my time in a novel way, as opposed to how I would normally do it - struggling through documentation and (possibly outdated) blog posts.  If I don't know enough about the solution it is proposing, I end up spinning around in circles: passing the error message in, getting some "fix," getting new error messages, passing those back to the LLM, then getting a "fix" which reproduces the original error.  Around and around we go.

Vibe Coding, as I understand it currently, has evolved from the original tweet which prescribed the above approach.  Modern Prompt Engineers, they say, operate something like a Technical Product Manager.  They create a detailed brief, outlining each step of the work to be implemented, pass that over to the LLM, and iterate as before.  Apparently you can get pretty fancy with it, creating semi-autonomous "agents" who can run through the insanity looping on your behalf.

As I said before, I was excited to work on all the fun back-end stuff, but I didn't want to get out over my skis.  I knew I needed a proof of concept (POC) before I headed out into the backend jungle with my machete.  Maybe this would be a good time to try out this "Structured (Disciplined? Focused?) Vibe Coding"

## A WatchOS Proof of Concept

Flogger belongs in a category of apps you could call "Life Improvement Apps," and they come in lots of flavors.  You've got trackers for hydration, nutrition, habits, mood, menstrual cycle, exercise, medication... if there's something you think you ought to be doing, or something you ought to be improving on, there's an app which aims to help you achieve your goals.  To me, one of the most interesting things about the apps in this space is if you are doing it right you are interacting with the app with a high _frequency_ but with a _minimal total use time_.  After all, the point is to exercise more, right? Not to spend hours scrolling through your exercise app.  Sort of the opposite of every other app out there.

Flogger subscribes to the same philosophy:  In order for the user to see the benefit provided by all the data analytics and fancy algorithms, the user needs to log their data.  A lot of it.  This is the primary goal of the front end application.  By adopting a voice-first and wearable-first approach, Flogger aims to reduce the friction to do that.  Ideally, you'd just call out, "Hey Siri, I drank a glass of water," or, "Hey Siri, I took my blood pressure meds," and get on with your life.

With that in mind, I set about writing some requirements for a WatchOS and iOS POC:
- Apps written in native Swift (for minimal startup time)
- User must issue a command through Siri
- App must work while the phone is locked (not really a problem with watch apps)
- App should fire off a POST request to an API, supplying the user's command
- (not part of this POC) on the API side, we'll take that command, give it to the LLM, determine we need to record a mood entry or whatever

Seems pretty straightforward.  I put on my Product Manager hat and fleshed out the list a bit, going into some more detail.  I poked around on the Apple dev site, grabbed some documentation and added that to the design document as well.  I pasted it into Google's AI Studio and got... well, I basically got exactly the same experience that I had had before.  Depending on my place in the loop, the app sortof worked, or it didn't build, or it seemed to work but the Siri integration wouldn't work.  Despair.  I so desperately wanted to return to the API work.  I wasn't ready to dive into tutorial hell.  "Welcome to the wonderful world of iOS development."  But if I wasn't certain that I could do the thing I wanted to do, what even was the point in doing any of it?  Is this just a waste of time?  I took my dog Max for a walk.

## Build your own tutorial

Ok so to get straight to the point, now is the time I need to learn some Swift.  Need to stop fighting it and embrace it.  It occurred to me that one of the pain points of learning a new programming language as an experienced software developer is that it can be hard to bootstrap an application which only gives you what you're going to need.  Even if it was in a broken state, the llm-generated code could identify the topics I needed to explore first: microphone permissions, Siri Intents, entitlements, etc.  I could use the LLM in the way I was used to: by having a conversation.  "Tell me about App Groups in iOS development."  This, combined with some of Apple's WWDC videos and sample code, was enough to get me limping across the finish line.  I made a rough POC. You can check out the [GitHub Repo](https://github.com/ACME-Software-Solutions/SiriLogger) if you are interested (it's not interesting).

## A failure and a success

Vibe Coding let me down.  That's ok and honestly I never really wanted to love it in the first place.  I didn't become a software developer in order to do the job of a product manager.  I've heard some folks breathlessly describing this new agentic vibe coding thing as something like being a conductor of an orchestra, or a military general and their army, fill in the metaphor.  I don't know, I'm skeptical.  Maybe if I made my living building and shipping bootstrapped SaaS apps and my focus was more on shipping, maybe it would appeal.  In my day to day work as a tech lead, I'm not thinking of my fellow developers as "force multipliers" or something.  It's not all about me, and it's not even all about shipping, if I'm honest about it.  Funnily, it's about the vibes.  Different vibes: bouncing ideas off people, joining forces (and interests) with people who have different lived experiences, you get the point.

I haven't ruled out vibe coding as a strategy for solo projects.  It's possible that I just went about it in the wrong way.  What's more likely is that I just haven't found the right use case yet.  I *do* want to learn Swift, but I also have a limited amount of free time, and I gravitate naturally to areas that I'm already confident I could quickly make progress on. In those cases, I really enjoy writing the code needed to make it work - I mean, it's my favorite thing, why would I want to turn it over to a machine?  For me, it doesn't really work in arenas that I'm not familiar with (Swift, for example), and I just spin my wheels a bunch and I get frustrated.  I just come back to my main use case: as a way to talk through my decision making process.  So what, I couldn't wave a magic wand and ask for Gemini to write a working proof of concept.  I what I *did* come away with was a good place to start.  I got my POC running and hitting the API.  A weight off my mind, I was able to focus on the API MVP, which is now nearly done.  Know what that means?  It's time to learn some Swift.

