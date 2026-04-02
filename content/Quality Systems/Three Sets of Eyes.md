---
title: Three Sets of Eyes
description: How to engage the entire team in producing high-quality software
---
## Where I learned about “Three Sets of Eyes”

In 2013 I joined a company called DmgCtrl (pronounced “Damage Control”), and they prided themselves on producing attractive, high-quality mobile apps and websites on time and on budget. And they were doing so without a dedicated Quality Assurance team or professional software testers. I joined the company because I could tell that they were doing the right things the right ways -- even if they didn’t follow traditional “quality management” practices.

Their approach eventually came to be called “Three Sets of Eyes:”
1. A developer wrote the code to create a new feature or to fix a bug
2. A second developer performed code review
3. A third person (an apprentice or other developer in their case) “tried to break it”

No ticket was truly Done until three people had touched it.

## Why it works

High-quality work doesn’t come from a single act, person, or moment. It emerges from the cooperative effort of the entire team, bringing many perspectives and approaches.

**Three Sets of Eyes** isn’t a process in the most formal sense. It’s not a framework you can install and -- voila! -- quality output! Instead, it’s the distillation of a pattern that shows up again and again in teams that consistently produce software that works well and meets the needs and goals of the end user.

### The first set of eyes: The Builder

Every unit of work begins with someone building it: The architect laying out patterns and paradigms. The DevSecOps engineer establishing protocols and pipelines. The developer who implements the solution to the problem at-hand.

**The Builder** is closest to the problem, the requirements, and the intended solution. They spend a lot of time thinking through the feature or bug and determining how to implement the solution. They understand the *why* behind the code in a way that almost no one else can.

That closeness is both powerful **and** a limitation. When we live inside a problem (and our coded solution) long enough, our brain begins to fill in any gaps: We see only what the code is *supposed* to do -- and we might not see what it *actually* does.

And that’s how human brains work and think. It’s not a flaw. But it’s the main reason that one set of eyes is never enough.

### The second set of eyes: The Reviewer

The careful, methodical practice of Code (or Peer) Review developed because we all know that very limitation: The Builder can’t easily see beyond, “This is what I expect this to do.” We bring in a second perspective -- someone who wasn’t directly involved in the act of writing the code.

Good review isn’t a “hoop to jump through because them’s the rules.” It’s not a checklist to complete for bureaucratic purposes. When done well, good review is like a conversation.

A good reviewer asks:
- Is this approach sound?
- Is the code clean/clear?
- Does this meet the intent of the work described in the ticket?
- Is there a simpler or more maintainable way to do this?

And a great reviewer asks, “Does this *really* do what we think it does?”

Many bugs/defects are quashed in Code Review. Not because someone is policing quality, but because two people, working together, have strengthened the work.

#### A few thoughts about Code/Peer Review
1. If you practice Pair Programming, you may or may not need a separate review step. If the work has truly been collaborative and cooperative, you have probably asked all the questions and explored the possible approaches. However, both coders may still “feel better” if they get another set of eyes. I’ll leave it to you and your team to decide.
2. Platforms like GitHub and GitLab make the Review “conversation” normal and natural. Teams should use the review comments to enable a thorough, asynchronous “conversation” to occur between coder and reviewer.
3. When performed best, Code/Peer Review also involves light functional testing of the code. There’s no better way to be sure whether it does what it’s supposed to do.

### The Third Set of Eyes: The Tester

This is my usual bailiwick, of course, and it’s the realm of “traditional testing.” This, however, should be seen as the perspective that changes the question entirely. The tester isn’t merely asking, “Does this work?” They are also interrogating, “Will this work well for our end users in this system?” (This perspective is so central to my Philosophy of Quality that it has received its own treatment in [[Quality as Fitness for Use]].)

This is where the work encounters reality.
* Does it behave as expected?
* Can I make it behave in *unexpected, unplanned, or unpleasant* ways?
* What happens at and near the edges?
* Does it cause unanticipated side-effects in related sections of the system?
* What happens when we approach this code like a real user -- not as a technologist who understands how it “should” or “is designed” to work?

This is when we treat the work not as a technical implementation but as an experience. And this perspective is fundamentally different from the other two.

### What each set of eyes sees (that the others don’t)

Each of these perspectives is necessary because each one is incomplete on its own.

- The Builder sees intent but can miss gaps.
- The Reviewer sees structure but doesn’t usually explore behavior deeply.
- The Tester sees behavior but may not have engaged with the technical design process.

Quality emerges not because any one of these is perfect, but because the **Three Sets of Eyes** compensate for -- and ideally cooperate with -- each other.

### What can happen when one is missing

You can often tell when a team is skipping one of the steps. The problems produced point out what step was skipped:
- Without meaningful review, code debt accumulates, and parts of the system become brittle. (This is one of the reasons that I call such sections of code a “bad neighborhood.” See a fuller explanation in [[The Neighborhoods Analogy#Bad Neighborhood]].)
- Without testing, edge cases, usability issues, and unexpected behaviors and unintended consequences slip through.
- Without strong ownership at the point of creation, everything else becomes heavier, slower, and more reactive.

These aren’t surprising outcomes. They’re literally predictable. Each missing piece leaves a blind spot.

## This isn’t a pipeline. It isn’t a process. It’s an ecosystem.

It’s way too easy to implement this as a set of steps to follow or boxes to check off:

Build → Review → Test

But that doesn’t do justice to how quality emerges when the ecosystem is respected and allowed to grow.

In strong teams, these aren’t isolated steps. They’re connected through constant feedback and cooperation:
- Developers anticipate review and testing.
- Reviewers dialog with the original coders **and** think about how it will be tested.
- Testers communicate what they see and experience back to the team. And in the best teams, testers and coders sit side-by-side in pairing sessions, testing during or parallel to the coding and review process.

When done well, the lines begin to blur. Quality stops being “handed off” to the next stage. It becomes a *shared outcome of working together.*

## The not-so-hidden secret: Trust and Shared Ownership

If there’s a ”secret” here, it isn’t in these three steps. It’s what sits underneath them, connects them, and makes the whole so much greater than the sum of the parts.

People do their best work when they know
- someone else will see it
- that person will take their contribution seriously
- and the goal isn’t to “reject the failure” but to improve the product

When that trust exists, behavior changes:
- Work becomes more intentional.
- Feedback becomes more meaningful.
- Quality becomes something the team produces together -- not something “tested in” at the end.

## This isn't just about software

This pattern isn’t limited to code. You’ll find that **Three Sets of Eyes** can produce high-quality in
- Design
- Writing
- Strategy
- Communication

Create. Review. Experience.

Different domains; same dynamic.

## A seemingly simple idea that scales

**Three Sets of Eyes** is simple enough to explain in a few sentences. (I know. I’ve trained multiple teams in how to do it since I learned it.)

But when practiced consistently -- when it becomes how the team thinks and works together -- it scales into something much larger: A culture where **Quality** isn’t owned by one role or team but shared across the entire organization.

And that’s where the real results come from.

**Three Sets of Eyes** isn't about process maturity. It's about having the courage -- and the humility -- to invite someone else to look closely at your work.

---
Copyright ©2026 Jay R. Newlin. All rights reserved.
