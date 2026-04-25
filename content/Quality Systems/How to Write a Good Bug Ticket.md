---
title: How to Write a Good Bug Ticket
description: A clear guide to writing good, actionable bug tickets -- every time
---
## Purpose

This document is designed to act as a handbook or guideline for those who write bug tickets (cards, issue reports, etc.). It contains helpful information to ensure that your bug tickets are actionable when a software developer is assigned to work on them.

## What is a bug?

A bug is any failure of the software to meet stated and documented acceptance criteria. Bugs will be identified by validating functionality and design against the final approved specifications (requirements and acceptance criteria). Any request that is outside the approved functional and design specifications -- even refinement of existing functionality -- should be thought of and treated as a “new feature.” These items will be placed in the backlog and will be properly estimated and planned in future development sprints as directed and as project prioritization and scope allows.

## Reporting
  
Where the bugs are reported can vary by product and team. It could be in a backlog tracking system such as Pivotal Tracker, JIRA, or a spreadsheet or kanban board. Users of Pivotal Tracker should take advantage of the Bug Report template in the Description field. Regardless of where the bugs are logged, the same information and format is recommended as outlined below. 

### Getting ready to write the bug ticket

It is extremely important to prepare for writing the ticket ​**before​** you actually write it. The steps of preparation include:

- Duplicate the error (that is, make it happen again). This is imperative. Many times you’ll encounter something odd, but it isn’t repeatable. Only when you can describe how to make the issue occur consistently can a developer address it.
- Search your backlog tracking system for an existing ticket. It’s possible that someone else already reported the issue that you’re encountering. Duplicate tickets can cause confusion or (at worst) duplication of effort. If a ticket already exists, review it; you might be able to add details or a comment that will help to improve that ticket.
- Carefully document the steps necessary to make the bug happen​ -- especially “odd” steps or​ gestures that you need to do.
- Take screenshots of interesting or significant outcomes. If the behavior calls for it, take a video instead of screenshots.
- Copy ​**exactly​** any and all error messages that you receive​ -- especially those in the Console or​ other logging system.
- Be clear in your own mind what you expect to happen. Research story tickets, requirements documents, or designs for necessary details.

### Name the bug appropriately

The title or Short Description of the ticket should be short and clear. It should include the user type and/or name of the page and a very brief description of the issue.

	Example format: `Casual User > Home Page > Typo`

### Fill out all relevant ticket information

#### Describe the problem

- Include the specific screen/location for clarity and attach screenshots and/or video.
- Include the user role(s) who experience the bug​ (e.g. occurs for a casual user, not authenticated user).
- Include browsers/devices and testing environments in which the error was found. This can be especially important during development of a new project. Did it occur on the staging (pre-production site) or on the site that’s currently in production? Or both?
- Include error messages, if any. If possible, please provide a screenshot of the error message.

#### Include steps to reproduce

- If the bug is in a well-known feature/function/screen, it’s okay to write something like, “On the Payment Screen, the credit card number field won’t accept 16 digits.”
- If it’s a lesser-known feature, be sure to include the steps necessary to get to that point.
- If specific data is important, include that information (e.g. “The Billing State must be California”).
- Mention strange steps/gestures/actions (e.g. “Triple-click the Submit button”).

#### Describe the Expected behavior

- That is, what **should** have happened instead of the bug behavior/output?
- Reference approved documents such as designs, functional requirements, etc. to confirm what the expected behavior should be. ​You won’t insult anyone by stating the obvious.
- Include attachments, screenshots, etc. as needed to ensure the expected behavior/solution is clear.

#### Assign an accurate priority

The following chart describes the common priorities available in most bug-tracking systems.

| Priority | Description                                                                                                                                                                                                                                                   |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Blocker  | A major use case (e.g., buying a product, signing up for email announcements, logging in, etc.) is not working at all.<br><br>--OR--<br><br>Significant parts of testing are impossible because of this issue.                                                |
| Critical | A major use case or business practice or set of tests is significantly hampered by this issue.                                                                                                                                                                |
| Major    | It will be important to address this issue during the next Sprint because it has significant impact on parts of the system or testing scenarios. It is possible that there will be a workaround for Major issues, but the workaround is not optimal practice. |
| Minor    | This issue should be addressed before go-live or may be deferred to the next version of the software. There may be a reasonable workaround for Minor issues that, while not ideal, is a valid option.                                                         |
| Trivial  | - Minor styling (color, font, alignment) issues that would improve the overall look-and-feel of the site/app. <br>- Functional inconveniences that do not affect major parts of the system. <br>- Trivial issues never block business practices or testing.   |

### Review your ticket

This is especially wise if you are new to writing bug tickets. Even if you’re an expert, it never hurts to spend a moment to review your ticket.

1. If the bug is difficult to replicate, follow your own steps and make sure that you can make it happen by doing so.
2. It’s a good idea to “QA” your own ticket:
	1. Does it make sense to you when you re-read it?
	2. Is everything spelled correctly, and are you using good grammar?
	3. Did you remember to attach screenshots/video and to record error messages?
