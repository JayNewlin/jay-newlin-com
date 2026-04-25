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

### What Exploratory Testing isn’t

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
## Additional References

I have found both of these resources to be very helpful as I learned software testing.

- [Exploratory Software Testing](https://www.pearson.com/en-us/subject-catalog/p/exploratory-software-testing-tips-tricks-tours-and-techniques-to-guide-test-design/P200000009621/9780321636416)
- [The Art of Software Testing](https://www.wiley.com/en-us/The+Art+of+Software+Testing%2C+3rd+Edition-p-9781119202486)


