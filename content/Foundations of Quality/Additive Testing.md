---
title: Additive Testing
description: A model for organizing tests to improve efficiency
---
Almost everyone in Software Quality Assurance eventually encounters the "test pyramid," which was first introduced by Mike Cohn in his 2009 book, [Succeeding with Agile](https://www.pearson.com/en-us/subject-catalog/p/succeeding-with-agile-software-development-using-scrum/P200000009360/9780321660565). Soon after you've been exposed to it, you'll also find all the arguments online for and against it: It's dead. It's upside-down. It doesn't have enough layers. It's outdated.

I'm not going to engage those arguments. I see the test pyramid more as a conversation starter than being the **point** of the conversation. I'll start with what I think it does to help our conversation on test management.

![[The Test Pyramid.png|An image illustrating the test pyramid, with slower UI tests at the top, faster unit tests at the bottom, and service tests in the middle]]

---
## What the test pyramid tells us

The test pyramid reminds us that:
- **Unit** tests **run quickly** and **provide fast feedback** to the developer
- **Service** (sometimes known as **Integration**) tests pull together multiple units, components, or services, also providing decently fast feedback
- UI-layer tests are **very slow, expensive to develop and maintain,** and are **designed to prevent regressions, not to indicate exactly where an issue has been introduced**

The pyramid also demonstrates that well-planned and well-organized test systems **build upon each other**. No layer is the exclusive domain of the developers or the test engineers; all members of the team should have a voice in their construction and organization.

This concept of “test systems building upon each other” is what I like to call **Additive Testing:**
- We deliberately plan, design, and build each layer upon the others, adding confidence without duplicating effort
- None of the layers is a silo, independent of the others -- or even worse, actively competing against them
- We design and build them to work together, each one contributing something unique to our understanding of the system.

---
## Coordination is key

In my approach to test management and organization, the entire team works together to design, code, and review all the layers of the test system.
- The business analysts or product managers provide the business rules that automated tests will verify (for example, verifying the rules around password complexity have been coded correctly).
- Test engineers influence all layers of testing, ensuring that the team includes negative and edge-case tests -- as well as "happy-path" tests -- in the unit and service test layers.
- Developers ensure that test engineers understand what has been tested at a lower level (like the validation of email addresses and passwords) so that the test engineers don't expend effort re-testing them at the UI layer.

### Everyone has a stake in test coverage

Too many teams assume that the goal is "100% lines of code (LOC) covered," ignoring the fact that some lines of code simply don't need an express unit (or even UI-layer) test to exercise them -- especially in modern frameworks where "line of code" doesn't directly correlate with "the system is doing something that needs to be verified."

I tend toward more practical approaches:
- Establish an achievable level of coverage (possibly 80-85%) for overall LOC
- Work toward even higher levels (perhaps 90% or more) for "critical units" -- with the entire team deciding together which sections of the system and even which units or subcomponents are "critical"
- Remember that **branch coverage** (ensuring that each branch of conditional logic is executed and verified) is critical to ensuring that you have no "unexplored paths" in your system. I recommend working to approach 100% branch coverage.

As the team works toward coverage goals, don't make the coverage statistics a quality gate. Instead, have the testing tools regularly report on the coverage and even warn when and where the goals aren't achieved. When you get close to each goal, the team should then dedicate time to achieve the goal (that is, specifically schedule test creation into your workflow) so that you *can* turn on those quality gates (especially if you can block a merge request if your coverage is too low).

---
## No one has enough system/integration tests

I know that's a bold assertion, and I'll be glad for a team to come talk with me about why they feel that they have enough tests at the **System** or **Integration** layer. But most of us know that we usually treat our UI-layer tests as "integration testing." The problem with that approach is that UI-layer tests are "too far" from the code, and you may not be easily able to pinpoint from a failed UI test exactly which system, integration, or unit has caused the error.

The typical scenario looks like this: The UI tests are so slow that we only run them overnight. Some number of them fail some nights because they received an HTTP 503 error ("service unavailable") from one of our services -- but the service itself reports that it was up and running all night. The tests told us that something failed, but not enough to know what actually happened. To be honest, the service might just as well have returned the [HTTP 418 "I'm a teapot"](https://httpstatus.com/codes/418) error.

So what should we do? We should coordinate as a team:
- Architects and tech leads identify the various internal and external interfaces that the system has
- They then work with the test engineers to research and determine which tooling works in their project to provide system/integration testing
- That working group helps the business analysts and/or project manager to educate the product owner and stakeholders on the benefits of increasing their system test coverage
- Once approved, the team dedicates some amount of time each sprint (or month or year) to build and improve their system/integration tests
- After enough coverage has been achieved, those same tests can be used as quality gates to prevent bugs and system failures from creeping into the code

### The benefits of Contract Testing

Most systems depend on one or more APIs from external systems or services. In microservice architectures, even your own components communicate this way -- effectively treating each other as external systems. This is where **Contract Testing** becomes especially valuable. It lives in that middle layer: closer to the system than unit tests, but far more precise and reliable than UI-layer tests.

Most teams try to verify these interactions through UI-layer tests or by attempting to simulate them in unit tests. Instead, contract tests focus on the agreements between systems (also often known as an API spec):

- What requests are made
- What responses are expected
- How those interactions are structured

From an **additive testing** perspective, this is exactly what we want:

- Contract tests verify interactions at the system level without duplicating what unit tests already verify internally
- They provide faster, more precise feedback than UI-layer tests when something breaks
- They help teams detect integration issues _at the boundary where they actually occur_

In other words, they add confidence exactly where many teams currently have gaps.

Teams that adopt contract testing often see fewer “mystery failures” like the ones described earlier -- where a UI test fails, but no one can immediately determine why. By testing the contracts directly, we reduce ambiguity and improve the signal we get from our tests.

Contract testing isn’t the only way to strengthen your system/integration layer, but it is one of the most effective ways to ensure that your tests are **adding value without adding redundancy**.

When Contract Testing is part of (or the entirety of) your service/integration test layer, you'll often see reduced downtime and API errors. No more wondering, "Why did we get a 503 when running the automated test suite?" No more system outages from those frustrating null references or other unexpected runtime errors.

If you want to explore Contract Testing further, you might want to:
- Read about [Contract Testing for microservices](https://www.mabl.com/blog/understanding-contract-testing-microservices-mabl?ref=blog.hunterstrategy.net)
- Listen to real-world benefits of Contract Testing as related by [Lewis Prescott of Cera Care](https://testguild.com/podcast/a399-lewis/)

---
## What about UI-layer tests?

Now we come to the top of the pyramid, and it is the smallest layer on purpose: UI-layer tests are notoriously:
- Expensive (time-consuming) to create and maintain
- Slow to execute (many teams have UI test suites that require hours to run to completion)
- By definition, uncoupled from and "unaware of" the system beneath it, reducing the ability to easily find the root cause of errors
- So slow and so distant from the underlying code that they can't often be included as quality gates in CI/CD pipelines

Don't think that I'm advocating that we shouldn't create UI-layer tests. On the contrary, I believe that they should be planned and developed (you guessed it) in coordination with the entire team, not just relegated to the domain of the automation or QA engineers:
- As mentioned above, the developers should keep the QA team well-informed of their unit tests so that the team avoids unnecessary duplication of effort
- Manual testers help determine which test cases are repetitive, difficult, or boring for them to execute regularly and accurately; those are automatically candidates for automation
- The engineers should work with the business analysts and project manager to understand which areas of the system are business-critical to ensure that they are well-covered with automation to prevent embarrassing, costly regressions

I also believe that we should all be planning UI-layer tests in advance. In some of the most successful teams that I know, the automation engineers are designing their tests alongside the development of the code that will implement the feature. If possible, UI-layer tests should not lag behind development by much more than one or two sprints. When the UI-layer tests lag too far behind development, regression testing and detection is relegated to the manual testers, whose efforts are even slower (and therefore more costly) than automation.

### A word about manual testing

Don't interpret my last sentence as some statement like, "Jay thinks that we should eliminate manual testing." That's as far from the truth as it could possibly be. I **am** saying that we **always** need manual testers, but we want to make them as efficient as possible.
- We should automate repetitive, boring functions like login, account creation, verifying links, etc.
- We should automate functionality that is based on complex rules and system interactions
- We should automate very basic checks that are time-consuming (like "Does our 'About Us' page have all the required information," or "Does our 'Privacy Policy' appear when and where required")

What we absolutely **must** do is to free our manual testers' minds to be more creative, allowing them to look for bugs and weird system interactions that automation will never find. We need them to be able to approach our system like real users will, thinking about whether the system is working well for the end users and not just meeting all the requirements (that is, is the system [[Quality as Fitness for Use|fit for use]]).

As you may know by now, my preferred approach to manual testing is known as [[Exploratory Testing]]. If there is sufficient UI-layer automation, our testers will be able to explore like users and help prevent unusual or emergent-behavior bugs from going out the door.

---
## The take-away

**Additive testing** isn’t about having more tests. It’s about having the **right tests in the right places,** each one contributing something meaningful to the overall test strategy. When the layers aren't coordinated, teams end up testing the same behavior multiple times in different ways -- adding cost without adding confidence.

To state that clearly: **Additive testing** is also about economics. Every test we write has cost: time to build, time to maintain, time to run. With well-designed, well-coordinated layers, we ensure that each test earns its keep by providing unique, actionable feedback.

When teams collaborate to plan and create tests across all the layers, testing stops being a **phase** and becomes a **system** -- one that continuously answers the only question that really matters:

> Is this product truly *fit for use?*
