---
title: The Neighborhoods Analogy
description: A mnemonic for understanding how to approach and categorize areas in your codebase/project/software/system
---
Several very wise testers (especially Myers, Sandler, and Badgett in [The Art of Software Testing](https://www.wiley.com/en-us/The+Art+of+Software+Testing%2C+3rd+Edition-p-9781119202486)) have suggested that a good analogy for software is that of a city made up of many neighborhoods (like Philadelphia has Fishtown, Bella Vista, Greys Ferry, etc.).
- This analogy can help a tester design exploratory testing sessions. 
- It’s also useful when first exploring a site or app that has been under development for a while, and you’re a new tester on the team. 
- You can use this analogy to help guide your initial conversations about what to test and how with other testers or the developers. 
- The neighborhoods can also help you to figure out the urgency or priority of bugs that you find.

## Business District

New York City has Wall Street. Software systems have their “money-making” neighborhood. For online stores, it’s the ​**Product Display Page (PDP)​**, shopping cart, payment processing, etc. For other sites or apps, it’s the main “business” that users transact with the system -- even if it has nothing to do with money or purchases.

You’ll need to spend a lot of time and energy testing the Business District. This is the part of the system that should “never” have bugs or go offline. You’ll want to discuss with the developers the unit tests that they’ve put in place around all the ​**business logic​** in the Business District. If your project is using other automated tests, they should also focus a lot of attention here.

## Historic District

Philadelphia has Old City and Independence Mall. Software systems have code that has existed for a “long” time. Some large business systems rely on ​**legacy code​** that has been around for a long time -- perhaps even many years. The old buildings in physical historic districts need lots of TLC; the same is true of old code -- it may have become brittle with time.

We don’t have to treat the Historic District of computer systems with kid gloves. Instead, we put good guardrails of tests around them (think of it like keeping an eye on Philadelphia's Independence Hall’s structural integrity with modern tools and architectural techniques). If the legacy code is part of the **System Under Test (SUT)​**, good testing may allow it to be refactored and improved over time. If it’s external to the SUT, good tests should ensure that the data coming and going over the ​**APIs** is structured as expected and that results are accurate.

## Fashion District

Think of the lights and glitz of The Strip in Las Vegas or the Champs Elysées in Paris. Yep: lots of flashy, cool-looking stuff that doesn’t mean much to the real world.

The software Fashion District is similar: It’s the part of the system that looks very cool or pretty but doesn’t really do anything. People stop by and look at it occasionally, but no one really spends much time there (including testers). For websites, it’s often the company’s "About Us" page. For mobile apps, it could be the splash screen and screens that provide a tutorial of how to use the app. Usually we don’t need a lot of testing in these areas because there isn’t too much that can break.

We can’t ignore the Fashion District completely. If a company’s "About Us" page goes offline, is unresponsive, or looks ugly, potential customers may move on to some other company. Sale lost = very unhappy stakeholder.

You should also be listening for hints that a member of the company’s upper management is very proud of the Fashion District. It’s possible that they rarely visit other parts of the site. Or they think it’s very cool to show off to people they meet. If you hear something like this, be sure to keep an eye on the Fashion District, so that folks in upper management don’t have a reason to complain about “all the bugs in this system.”

## Bad Neighborhood

Yeah, that one. Every city and town has one. So do software systems.

Often the Bad Neighborhood in software is an area where bugs have a tendency to occur...and reoccur...and keep on doing so. Or something about its architecture makes it very brittle, so any change will probably result in some kind of bug, crash, or other issue. Software Bad Neighborhoods are places that testers like to spend time and energy. The more tests we put in place to keep an eye on the Bad Neighborhood, the more likely we are to catch those ​**regressions​** that happen when someone touches the code.

**Be aware:** When cities/towns put time and energy into physical bad neighborhoods, they often convert into nicer neighborhoods. With the right care and maintenance, software bad neighborhoods can also become something very different -- perhaps a stable, relatively bug-free zone. (That’s the other reason testers like them: Our efforts can result in improving the bad neighborhood!)
