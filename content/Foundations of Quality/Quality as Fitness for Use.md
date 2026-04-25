---
title: Quality as Fitness for Use
description: My Philosophy of Quality in one powerful, short phrase
---
## What is “Quality?”

Many people have attempted to answer this question. There are plenty of books written about many aspects of quality, quality management, and quality assurance. One of the simplest definitions was offered by Joseph M. Juran, a management consultant, in his 1951 *Quality Control Handbook*: “Quality \[is] ‘fitness for use.’” It’s a deceptively simple phrase—and it carries almost everything we need to understand about quality.

## Fitness

“Fitness” means that the product (software in our case) meets the specified requirements. Juran was a manufacturing expert, so he was thinking about requirements based on size, shape, design, component materials, how the product is manufactured and put together, etc. 

If you're purchasing a case for your phone, you expect it to fit properly. That's "fitness:" The case's dimensions can be measured with a ruler, caliper, protractor, etc. The materials and construction help you to know what sorts of protection it can provide.

Software also has requirements. Consider a login screen consisting of two fields: email address and password. 
- Email addresses must conform to specific patterns of letters, numbers, and certain (but not all) special characters.
- The same applies to passwords: We can determine what we consider to be a strong enough password and specify it: minimum and maximum character count, how many uppercase and lowercase letters, how many digits, how many (and which) special characters.

"Fitness" in software development is fairly easy to test because we can write clear tests that determine whether it conforms to the written requirements. Some of these are scripted manual tests. Most of them should be automated as unit, integration, and UI-layer tests.

But -- and it's a big one -- meeting the requirements alone doesn't mean that we've achieved true *quality.*

## Fitness ...for use

“Fitness for use” builds on fitness by shifting our focus to the end user. The product should not only meet the specified requirements, but it should also meet the user's other -- often unwritten -- expectations. Requirements are absolutely necessary -- but they are never sufficient.

Think about your phone case: It may fit your phone, but if keeping the phone in your pocket causes the finish to degrade or discolor, you'll be disappointed. It may be fit, but you'll be displeased with its overall quality.

Not only should software work as specified, but it should also work in such a way that an end user will actually want to use it. This means that we need to take into account some general expectations and paradigms that may be unwritten:
- There's no rule that says that our login screen must have username above the password, but if you place them the opposite way, users will be very displeased with the most basic interaction in your system.
- We have a fairly universal paradigm that the "logout" button or link on most websites is in the top right of the screen. Believe me, I know at least one site where it's in the top left, and I always find it jarring to try to logout.

Testing "fitness for use" in software can't always be done with scripts and automation. We always want real people actually interacting with the system in the ways that end users might. We want them to think about the overall "look and feel" of the system. This is exactly where [[Exploratory Testing]] becomes indispensable.

## Conclusion

When we design, build, and test software for its _fitness for use,_ we’re not just meeting requirements -- we’re creating software that people will actually use, trust, and value.

