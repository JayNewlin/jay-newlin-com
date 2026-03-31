---
title: Software Testing Heuristics
description: Mnemonic devices to guide and improve manual testing
---
## What is a heuristic?

According to dictionary.com:
1. stimulating interest as a means of furthering investigation
2. encouraging a person to learn, discover, understand, or solve problems on his or her own, as by experimenting, evaluating possible answers or solutions, or by trial and error

For this document, heuristics can be thought of as ​**mnemonic devices​** or experiences that the tester can draw upon to “tease out” bugs or issues. The following list of heuristics is quoted from work by Alexandra Schladebeck (on X/Twitter as @alex_schl) and her page on [Microheuristics](https://www.schladebeck.de/microheuristics/). I have expanded and adapted them a bit.

## Important Heuristics for Exploratory Testing

### The Pimple Rule: Poke it until it pops

Yeah, it’s gross. Sorry/not sorry.

Testers inherently know that every ​*thing​* on every screen is an object to fiddle with. That “Submit” button? Don’t just tap it once. Tap it six, seven, or eight times! I see a card on that screen; I’m gonna tap, long-tap, and force-tap it, so see what happens. That thing isn’t designed to handle a right-click? You can bet money that I’ll right-click on it!

The other way to think about this one is related to ​**boundary testing​**: What are the max and min values for this field? What happens when I put in something over or under those values? What about a field that can be increased by something later on (a number with up/down arrows in the field): Try to put in the next-to-last number, then press up twice.

Try putting numbers where only letters are expected. Or the other way around. Emoji are always interesting to try in long-form text fields (where the program is expecting alphanumeric input).

Login screens are always fun. There are all sorts of default usernames and passwords. What happens if you try some combination of them?

There’s no secret here. It’s just knowing that every object very well may do ​*something​* if you fiddle with it long enough.

### Ifs are iffy

For this one, it’s helpful to know where ​**branches​** occur in the software. A branch is where the computer is required to make a decision based on previous steps or data.

As a practical example: If the user who logged in is an administrator, take them directly to the admin screen; if not, take them to some other screen. This calls for some good testing: What happens when I login as each user type? Do I land on the correct screen? What if I change a user from one type to the other? Do they get the correct screen?

Another possibility is to see what happens when “none of the above” is true. It’s difficult to give a practical example, but the thinking is: If you can set up a scenario where none of the possibilities is true before getting to the branch, what will the program do? (For the technically inclined: Have the developers provided an ​**else​** clause in their ​**if​** statement?)

The reason that we test hard around such ​**conditional logic​** is because one branch or another may not be foolproof. In particular, “none of the above” is too often forgotten as one of the possibilities; developers don’t always account for it.

### Yellow is interesting

We’re all pretty familiar with the pattern of indicating a positive result with green, a negative result with red, and something in-between with yellow. All the yellow states are always worth investigating.

Questions you can think about: Why isn’t it red or green? If it’s in a transitional state (heading from red to green), what makes it become green eventually? Or go back to red again? How long will it stay yellow (this is especially good for times when you’re “Waiting…” for something to occur)? What if something goes wrong during the transition from red to green (server goes down; user logs out)?

For testers, the “in-between” may produce more interesting bugs than one extreme or the other.

### If you can touch it, it’s real (and its corollary: If it shouldn’t be there, try to touch it!)

This one is especially good for ​**CRUD​** applications/interactions (create, retrieve, update, delete).

When you create a new record, immediately try to search for it. If you find it, try to change it. While systems tend to update pretty quickly, there are often enough backend processes that are **asynchronous​** that you may find an issue if a user is “allowed” to try to work with data objects that haven’t been “completely saved.”

The corollary is pretty much the opposite: When you have deleted a record, can you still find it and try to interact with it? If you ​*can*​ find it, you can be pretty sure that you’ll uncover a pretty good bug or missing error state.

### A rose by any other name

Sometimes in software development we create things that are supposedly “really the same,” but they are actually implemented differently. Think about the many ways and places that you might search for something: If it’s called “search” in one place, “find” in another, and is just a magnifying glass in a third, what are the chances that they’re different instead of exactly the same? Similarly, if your app uses “Submit” as the ​**CTA​** (call to action) on most screens, you might encounter “OK” on one of them. Does it do the same things as “submit?” Or is it really something completely different?

### You can never go back

Navigation through an app or site is tricky to manage programmatically, and users have come to expect the ability to move backward and forward. All browsers have a built-in “Back” button. Some sites/apps provide a "Back" button of their own as well.

Since it’s tricky to manage, and there are so many possible ways to implement navigation, that means that this is a prime target for testing.

- Navigate through your site or app a ways, then hit Back. What happens? If you entered data on the “page before,” is that data still there? Do different versions of the Back button (e.g., the built-in one on the web browser vs. one added to the page by the developer) work differently?
- Now go backward and forward a few steps at a time. Does data persist from screen to screen? Can you catch a bug of any sort?
- On mobile devices, the Back concept can be especially tricky. Pay attention to your path as you move forward, then try moving backward. Especially on Android, screens you have visited are kept on the ​**navigation stack​**. It’s very possible that you can cause some very interesting issues by going back far enough and trying to interact with “old” data and re-submitting it.
- If the paths through your app/site aren’t truly linear, the “Back” concept is even more difficult to implement. Keep exploring what happens as you navigate backward and forward through the various paths that you traverse.

### Break the chain

Computers, software, apps, sites, and systems often include some sort of ​**dependency​**: One part of the system “hangs off” another, like links in a chain. You know what happens to a physical chain when you weaken, break, or remove one link. The same is true in computer systems. As you learn more about the system that you’ll be testing, you’ll learn where the chains (of data, logic flow, etc.) are. This heuristic is all about trying to break one part of the chain and seeing what effect it has on the system or other data points that depend on it.

One very practical example is an order-based system where customers exist as records and customers are associated with orders. Create a test customer who has one or more test orders. Are you allowed to delete the customer? If you do, what happens to their orders?

### Fool me once…

It’s common for some bugs or types of bugs to reoccur frequently. Sometimes it’s due to brittleness in the codebase. Other times it’s because some part of the system is architected in a way that makes bugs difficult to prevent. In any case, as a tester, if you are aware that something is subject to fail, you better make sure that you have test scenarios set up to make sure that bugs don’t get out the door and into production.

One specific example that has plagued developers since computers first were created is ​**time​**. For a while, computers were simply bad at being clocks because their ​**CPU​** was too busy to update its internal chronometer regularly enough. Often it’s because time is not as straightforward as we’d like to believe (e.g., while it’s today here in the USA, it’s already tomorrow in Australia). Here are two good articles to read about time and computer systems/software:

- [Falsehoods Programmers Believe about Time](https://infiniteundo.com/post/25326999628/falsehoods-programmers-believe-about-time)[](https://infiniteundo.com/post/25326999628/falsehoods-programmers-believe-about-time)
- [More Falsehoods Programmers Believe about Time](https://infiniteundo.com/post/25509354022/more-falsehoods-programmers-believe-about-time)
