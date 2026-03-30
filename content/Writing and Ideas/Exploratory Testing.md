---
title: Exploratory Testing
description: A practical guide to Exploratory Testing as a software testing practice
---
## About this guide

This guide is written as an introduction to Exploratory Testing and many of the concepts related to that practice. I’ve taken a casual approach because I want you to learn in a fun way, and because you’ll probably remember these concepts better when you have a lot of analogies to compare to. The document changes voice and point of view. Sometimes it’s intentional; other times, it just happened.

Things that are in ​**boldface​** are key concepts that you might want to research and learn more about. In one or two cases, the research will reveal a joke or two that I make in the text.

Please don’t mistake this casual-ness as lack of care or concern -- I think that Exploratory Testing is one of the most effective ways for a tester to discover bugs and to learn how to set up, build, and manage automated tests for a specific project.

---
## What is Exploratory Testing?

Exploratory testing is one of many different styles or approaches to testing software. Exploratory testing is different from most other approaches because it is free-form. It treats testing as investigative discovery, empowering the tester to be an advocate for the system's user. This approach has the ultimate goal of verifying that functionality and design meet specified requirements and user expectations. 

The most significant distinction between exploratory testing and other methods of testing is that exploratory testing is less structured and more cognitive. This more fluid approach allows for the discovery of a wider range of bugs, informs further testing, and inspires potential future requirements.  

## What Exploratory Testing isn’t

Because exploratory testing is less structured than other forms, and because it relies on the testers’ knowledge and experience, it can seem like magic. Quite often testers are asked, “How did you find ​**that​**?!?!” Usually the best answer is, “I was exploring the software like a user might, and I discovered this issue.”

Exploratory testing isn’t random banging on keys, the mouse/trackpad, touchscreen, etc. Because there isn’t a set of steps that the tester is expected to follow, it can seem like the tester randomly chooses places and things to try and “gets lucky” time after time.

Since exploratory testing isn’t totally random, results are not difficult to repeat. Good testers have an innate sense of how software/systems work, and they use an open mindset in exploratory testing to allow them to follow a user’s journey without being bound to a specific set of processes or steps to follow.

---
## Exploratory Testing: A how-to guide

### The Charter

To ensure that exploratory testing isn’t completely random or totally unguided, it’s important to have a concrete goal in mind, and good exploratory testing sessions should be time-limited. These factors are the domain of the Exploratory Testing Charter.

In the strictest sessions, a test manager or senior QA engineer should create a test charter for the tester(s) to follow. At a minimum it should include

1. the Goal of the test session such as a specific user flow to explore or an ultimate task to accomplish (such as, put six items in the shopping cart)
2. if applicable, a User Persona to emulate
3. a time limit (usually not more than 10 or 15 minutes)
4. any other limitations or boundaries on the session (such as avoiding paths through the system that are totally irrelevant to the current goal or specific login/account details to ensure the proper user flow can be followed)
5. space for notes and for observations and/or outcomes

### The Session

The tester works with their assigned charter, sets a timer, and begins the journey.

1. Think for a moment how you want to approach the session.
	1. How will you achieve the goal?
	2. What interesting steps or areas of the app/site can you visit and test?
	3. What problem areas are part of this journey?

2. Start down the path, keeping the following things in mind
	1. Does this work like I expect? Like a customer would want it to work?
	2. Does this match the designs? Does it look good? Can I find the information/tools that I need?
	3. Can I accomplish my goal in the allotted time?

Throughout the session, the tester should be sure to trust their instincts. If something seems odd, they should spend a moment with it, to “tease out” a bug or design flaw. If this takes too long, that becomes a note on the charter, and they can follow up with it later.

If the tester encounters a bug or issue, they are allowed to turn off the timer in order to capture enough information -- especially the steps required to reproduce the issue -- for ​writing a bug ticket. (See my page on [[How to Write a Good Bug Ticket]]) Once they have finished that, they turn on the timer again and, if possible, resume testing through the end of the journey.

Once the goal is accomplished, the timer runs out, or a bug blocks completion of the journey, the tester should complete the Charter and move on to the next task or session.

---
## The Neighborhoods Analogy

Several very wise testers (especially Myers, Sandler, and Badgett in [The Art of Software Testing](https://www.wiley.com/en-us/The+Art+of+Software+Testing%2C+3rd+Edition-p-9781119202486)) have suggested that a good analogy for software is that of a city made up of many neighborhoods (like Philadelphia has Fishtown, Bella Vista, Greys Ferry, etc.). This analogy can help a tester to design exploratory testing sessions. It’s also useful when first visiting a site that has been under development for a while, and you’re a new tester on the team. You can use this analogy to help guide your initial conversations about what to test and how with other testers or the developers. The neighborhoods can also help you to figure out the urgency or priority of bugs that you find.

### Business District

New York City has Wall Street. Software systems have their “money-making” neighborhood. For online stores, it’s the ​**Product Display Page (PDP)​**, shopping cart, payment processing, etc. For other sites or apps, it’s the main “business” that users transact with the system -- even if it has nothing to do with money or purchases.

You’ll need to spend a lot of time and energy testing the Business District. This is the part of the system that should “never” have bugs or go offline. You’ll want to discuss with the developers the unit tests that they’ve put in place around all the ​**business logic​** in the Business District. If your project is using other automated tests, they should also focus a lot of attention here.

### Historic District

Philadelphia has Old City and Independence Mall. Software systems have code that has existed for a “long” time. Some large business systems rely on ​**legacy code​** that has been around for a long time -- perhaps even many years. The old buildings in physical historic districts need lots of TLC; the same is true of old code -- it may have become brittle with time.

We don’t have to treat the Historic District of computer systems with kid gloves. Instead, we put good guardrails of tests around them (think of it like keeping an eye on Philadelphia's Independence Hall’s structural integrity with modern tools and architectural techniques). If the legacy code is part of the **System Under Test (SUT)​**, good testing may allow it to be refactored and improved over time. If it’s external to the SUT, good tests should ensure that the data coming and going over the ​**APIs** is structured as expected and that results are accurate.

### Fashion District

Think of the lights and glitz of The Strip in Las Vegas or the Champs Elysées in Paris. Yep: lots of flashy, cool-looking stuff that doesn’t mean much to the real world.

The software Fashion District is similar: It’s the part of the system that looks very cool or pretty but doesn’t really do anything. People stop by and look at it occasionally, but no one really spends much time there (including testers). For websites, it’s often the company’s "About Us" page. For mobile apps, it could be the splash screen and screens that provide a tutorial of how to use the app. Usually we don’t need a lot of testing in these areas because there isn’t too much that can break.

We can’t ignore the Fashion District completely. If a company’s "About Us" page goes offline, is unresponsive, or looks ugly, potential customers may move on to some other company. Sale lost = very unhappy stakeholder.

You should also be listening for hints that a member of the company’s upper management is very proud of the Fashion District. It’s possible that they rarely visit other parts of the site. Or they think it’s very cool to show off to people they meet. If you hear something like this, be sure to keep an eye on the Fashion District, so that folks in upper management don’t have a reason to complain about “all the bugs in this system.”

### Bad Neighborhood

Yeah, that one. Every city and town has one. So do software systems.

Often the Bad Neighborhood in software is an area where bugs have a tendency to occur...and reoccur...and keep on doing so. Or something about its architecture makes it very brittle, so any change will probably result in some kind of bug, crash, or other issue. Software Bad Neighborhoods are places that testers like to spend time and energy. The more tests we put in place to keep an eye on the Bad Neighborhood, the more likely we are to catch those ​**regressions​** that happen when someone touches the code.

**Be aware:** When cities/towns put time and energy into physical bad neighborhoods, they often convert into nicer neighborhoods. With the right care and maintenance, software bad neighborhoods can also become something very different -- perhaps a stable, relatively bug-free zone. (That’s the other reason testers like them: Our efforts can result in improving the bad neighborhood!)

---
## Heuristics in Exploratory Testing

### What is a heuristic?

According to dictionary.com:
1.     stimulating interest as a means of furthering investigation
2.     encouraging a person to learn, discover, understand, or solve problems on his or her own, as by experimenting, evaluating possible answers or solutions, or by trial and error

For this document, heuristics can be thought of as ​**mnemonic devices​** or experiences that the tester can draw upon to “tease out” bugs or issues. The following list of heuristics is quoted from work by Alexandra Schladebeck (on Twitter as @alex_schl) and her page on [Microheuristics](https://www.schladebeck.de/microheuristics/) I have expanded and adapted them a bit.

### Important Heuristics for Exploratory Testing

#### The Pimple Rule: Poke it until it pops

Yeah, it’s gross. Sorry/not sorry.

Testers inherently know that every ​*thing​* on every screen is an object to fiddle with. That “Submit” button? Don’t just tap it once. Tap it six, seven, or eight times! I see a card on that screen; I’m gonna tap, long-tap, and force-tap it, so see what happens. That thing isn’t designed to handle a right-click? You can bet money that I’ll right-click on it!

The other way to think about this one is related to ​**boundary testing​**: What are the max and min values for this field? What happens when I put in something over or under those values? What about a field that can be increased by something later on (a number with up/down arrows in the field): Try to put in the next-to-last number, then press up twice.

Try putting numbers where only letters are expected. Or the other way around. Emoji are always interesting to try in long-form text fields (where the program is expecting alphanumeric input).

Login screens are always fun. There are all sorts of default usernames and passwords. What happens if you try some combination of them?

There’s no secret here. It’s just knowing that every object very well may do ​*something​* if you fiddle with it long enough.

#### Ifs are iffy

For this one, it’s helpful to know where ​**branches​** occur in the software. A branch is where the computer is required to make a decision based on previous steps or data.

As a practical example: If the user who logged in is an administrator, take them directly to the admin screen; if not, take them to some other screen. This calls for some good testing: What happens when I login as each user type? Do I land on the correct screen? What if I change a user from one type to the other? Do they get the correct screen?

Another possibility is to see what happens when “none of the above” is true. It’s difficult to give a practical example, but the thinking is: If you can set up a scenario where none of the possibilities is true before getting to the branch, what will the program do? (For the technically inclined: Have the developers provided an ​**else​** clause in their ​**if​** statement?)

The reason that we test hard around such ​**conditional logic​** is because one branch or another may not be foolproof. In particular, “none of the above” is too often forgotten as one of the possibilities; developers don’t always account for it.

#### Yellow is interesting

We’re all pretty familiar with the pattern of indicating a positive result with green, a negative result with red, and something in-between with yellow. All the yellow states are always worth investigating.

Questions you can think about: Why isn’t it red or green? If it’s in a transitional state (heading from red to green), what makes it become green eventually? Or go back to red again? How long will it stay yellow (this is especially good for times when you’re “Waiting…” for something to occur)? What if something goes wrong during the transition from red to green (server goes down; user logs out)?

For testers, the “in-between” may produce more interesting bugs than one extreme or the other.

#### If you can touch it, it’s real (and its corollary: If it shouldn’t be there, try to touch it!)

This one is especially good for ​**CRUD​** applications/interactions (create, retrieve, update, delete).

When you create a new record, immediately try to search for it. If you find it, try to change it. While systems tend to update pretty quickly, there are often enough backend processes that are **asynchronous​** that you may find an issue if a user is “allowed” to try to work with data objects that haven’t been “completely saved.”

The corollary is pretty much the opposite: When you have deleted a record, can you still find it and try to interact with it? If you ​*can*​ find it, you can be pretty sure that you’ll uncover a pretty good bug or missing error state.

#### A rose by any other name

Sometimes in software development we create things that are supposedly “really the same,” but they are actually implemented differently. Think about the many ways and places that you might search for something: If it’s called “search” in one place, “find” in another, and is just a magnifying glass in a third, what are the chances that they’re different instead of exactly the same? Similarly, if your app uses “Submit” as the ​**CTA​** (call to action) on most screens, you might encounter “OK” on one of them. Does it do the same things as “submit?” Or is it really something completely different?

#### You can never go back

Navigation through an app or site is tricky to manage programmatically, and users have come to expect the ability to move backward and forward. All browsers have a built-in “Back” button. Some sites/apps provide a "Back" button of their own as well.

Since it’s tricky to manage, and there are so many possible ways to implement navigation, that means that this is a prime target for testing.

- Navigate through your site or app a ways, then hit Back. What happens? If you entered data on the “page before,” is that data still there? Do different versions of the Back button (e.g., the built-in one on the web browser vs. one added to the page by the developer) work differently?
- Now go backward and forward a few steps at a time. Does data persist from screen to screen? Can you catch a bug of any sort?
- On mobile devices, the Back concept can be especially tricky. Pay attention to your path as you move forward, then try moving backward. Especially on Android, screens you have visited are kept on the ​**navigation stack​**. It’s very possible that you can cause some very interesting issues by going back far enough and trying to interact with “old” data and re-submitting it.
- If the paths through your app/site aren’t truly linear, the “Back” concept is even more difficult to implement. Keep exploring what happens as you navigate backward and forward through the various paths that you traverse.

#### Break the chain

Computers, software, apps, sites, and systems often include some sort of ​**dependency​**: One part of the system “hangs off” another, like links in a chain. You know what happens to a physical chain when you weaken, break, or remove one link. The same is true in computer systems. As you learn more about the system that you’ll be testing, you’ll learn where the chains (of data, logic flow, etc.) are. This heuristic is all about trying to break one part of the chain and seeing what effect it has on the system or other data points that depend on it.

One very practical example is an order-based system where customers exist as records and customers are associated with orders. Create a test customer who has one or more test orders. Are you allowed to delete the customer? If you do, what happens to their orders?

#### Fool me once…

It’s common for some bugs or types of bugs to reoccur frequently. Sometimes it’s due to brittleness in the codebase. Other times it’s because some part of the system is architected in a way that makes bugs difficult to prevent. In any case, as a tester, if you are aware that something is subject to fail, you better make sure that you have test scenarios set up to make sure that bugs don’t get out the door and into production.

One specific example that has plagued developers since computers first were created is ​**time​**. For a while, computers were simply bad at being clocks because their ​**CPU​** was too busy to update its internal chronometer regularly enough. Often it’s because time is not as straightforward as we’d like to believe (e.g., while it’s today here in the USA, it’s already tomorrow in Australia). Here are two good articles to read about time and computer systems/software:

- [Falsehoods Programmers Believe about Time](https://infiniteundo.com/post/25326999628/falsehoods-programmers-believe-about-time)[](https://infiniteundo.com/post/25326999628/falsehoods-programmers-believe-about-time)
- [More Falsehoods Programmers Believe about Time](https://infiniteundo.com/post/25509354022/more-falsehoods-programmers-believe-about-time)

---
## Additional References

I have found both of these resources to be very helpful as I learned software testing.

- [Exploratory Software Testing](https://www.pearson.com/en-us/subject-catalog/p/exploratory-software-testing-tips-tricks-tours-and-techniques-to-guide-test-design/P200000009621/9780321636416)
- [The Art of Software Testing](https://www.wiley.com/en-us/The+Art+of+Software+Testing%2C+3rd+Edition-p-9781119202486)

---
**Copyright Notice:** Except where indicated otherwise, all material on this page is copyright ©2019, revised and updated 2026, by Jay R. Newlin. All rights reserved.

