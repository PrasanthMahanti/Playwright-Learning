# Manual vs Automation: When to Use Which

**The core idea**

Manual testing means a person uses the product the way a real user would, clicking, typing, and observing. Automation means writing scripts or tools that run those checks by themselves. Neither is better overall. They solve different problems, and good teams use both.

**Use manual testing when...**

- **The feature is new or changing often.** Writing scripts for something that will change next week wastes effort. A human can adapt instantly.
- **You need human judgment.** Does the layout look right? Is the wording confusing? Does the flow feel natural? Scripts can check that a button exists, but not whether it feels good to use.
- **You're exploring.** Exploratory testing, where you poke around without a fixed plan, finds surprising bugs that no one thought to write a test for.
- **The test will only run once or twice.** If the setup takes longer than just doing it by hand, don't automate it.
- **The check is hard to script**, such as visual design, accessibility feel, or complex real-world scenarios.

**Use automation when...**

- **The same check runs again and again.** Regression tests (making sure old features still work after new changes) are the classic example.
- **The feature is stable.** Once behavior settles, scripts pay off.
- **You need speed and scale.** A script can run hundreds of checks in minutes, on multiple browsers and devices, at 3 a.m. with no one watching.
- **The task is repetitive or error-prone for humans**, such as filling the same form with 200 different data sets, or comparing large amounts of output.
- **You want fast feedback.** Automated tests inside a build pipeline tell developers within minutes if they broke something.

**Quick comparison**

| | Manual | Automation |
|---|---|---|
| Best for | New, changing, visual, exploratory | Stable, repetitive, large-scale |
| Upfront cost | Low | High (writing and setting up) |
| Cost over time | Grows with every run | Drops with every run |
| Finds | Unexpected and usability issues | Regressions and known failures |
| Weakness | Slow, tiring, inconsistent | Brittle, needs maintenance, blind to the unexpected |

**A simple rule of thumb**

Ask three questions: *Will I run this many times? Is the behavior stable? Is the answer clearly pass or fail?* If all three are yes, automate it. If not, test it by hand.

**Common mistakes**

- Trying to automate everything. Maintaining a huge, flaky test suite can cost more than it saves.
- Automating too early, before the feature settles.
- Never automating, so every release needs days of repetitive re-checking.

**Bottom line**

Start manual to learn how the product behaves and to find new problems. Automate what proves itself repetitive and stable. Automation protects what you already know works, and manual testing discovers what you don't yet know.


# Study Notes: Software Testing Basics

## 1. What is software testing?

Software testing is the process of checking that a product does what it should, and doesn't do what it shouldn't, before real users find the problems.

**Goals:**
- Find bugs early (cheaper to fix early than after release)
- Confirm the software meets requirements
- Build confidence in quality
- Reduce risk (money loss, security issues, bad user experience)

**Key ideas:**
- Testing shows that bugs *exist*, never that there are *none*.
- **Verification**: "Are we building the product right?" (does it follow the spec)
- **Validation**: "Are we building the right product?" (does it meet user needs)
- **Bug/defect**: a mismatch between expected and actual behavior.

---

## 2. SDLC vs STLC

**SDLC (Software Development Life Cycle)** is the whole journey of building software.

1. Requirement gathering
2. Design
3. Development (coding)
4. Testing
5. Deployment
6. Maintenance

Common models: Waterfall (step by step), Agile (short cycles called sprints), V-model (each dev phase paired with a test phase).

**STLC (Software Testing Life Cycle)** is the journey of the *testing work itself*, which sits inside the SDLC.

1. Requirement analysis (what needs testing?)
2. Test planning (scope, tools, schedule, who does what)
3. Test case design (write the steps and expected results)
4. Test environment setup
5. Test execution (run tests, log bugs)
6. Test closure (report, lessons learned)

| | SDLC | STLC |
|---|---|---|
| Covers | Entire software creation | Only testing activities |
| Goal | Deliver working software | Make sure it's quality software |
| Relationship | The big picture | A part within it |

**Memory trick:** SDLC builds the house. STLC inspects the house.

---

## 3. Manual vs automation testing

| | Manual | Automation |
|---|---|---|
| Who runs it | A person | Scripts/tools |
| Best for | New features, usability, exploring | Regression, repetitive, large-scale |
| Upfront cost | Low | High |
| Long-run cost | Grows each run | Shrinks each run |
| Weakness | Slow, inconsistent | Brittle, blind to the unexpected |

**Rule of thumb:** automate what is repeated, stable, and clearly pass/fail. Test everything else by hand.

**Common tools to recognize:** Selenium, Playwright, Cypress (web UI); Appium (mobile); Postman, REST Assured (APIs); JUnit, TestNG, pytest (test frameworks); Jenkins, GitHub Actions (running tests automatically in pipelines).

---

## 4. What an automation engineer / SDET does

**Automation engineer:** writes and maintains automated tests, usually for the UI and APIs, often using existing tools and frameworks.

**SDET (Software Development Engineer in Test):** a hybrid of developer and tester. Does everything above plus builds the testing infrastructure itself.

**Typical responsibilities:**
- Design and build test automation frameworks
- Write automated UI, API, and sometimes performance tests
- Integrate tests into CI/CD pipelines
- Review code and testability of the product
- Analyze failures and find root causes
- Work with developers and manual testers to decide what to automate
- Maintain tests so they stay reliable (fix flaky tests)

**Skills needed:**
- A programming language (Java, Python, JavaScript/TypeScript are common)
- Testing fundamentals (test design, types of testing)
- Web basics: HTTP, status codes, HTML/CSS/DOM, DevTools (what you've been practicing)
- API testing, SQL basics, Git
- CI/CD concepts

**Automation engineer vs SDET (rough difference):**
- Automation engineer: focuses on *using* tools to automate tests
- SDET: more coding-heavy, builds frameworks and tools, thinks like a developer

*(Titles vary by company, so the line between them is often blurry.)*

---

## Quick self-test

1. What's the difference between verification and validation?
2. Where does STLC fit relative to SDLC?
3. Name one test that should be automated and one that should stay manual.
4. What does an SDET do that a pure manual tester doesn't?

Want me to turn these into a quiz, or go deeper on any section?