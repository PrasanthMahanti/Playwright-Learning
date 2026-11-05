# Test Plan: Sauce Demo (saucedemo.com)

| | |
|---|---|
| **Document version** | 1.0 |
| **Date** | 2026-11-04 |
| **Author** | _your name_ |
| **Application under test** | Sauce Demo, https://www.saucedemo.com |
| **Status** | Draft for practice |

---

## 1. Introduction and objective

Sauce Demo is a sample e-commerce web app made by Sauce Labs for practicing test automation and QA. A user logs in, browses six products, adds them to a cart, and completes a three-step checkout.

**Objective of this test effort:**
- Verify that the core shopping flow (login, browse, cart, checkout) works as expected.
- Find defects, especially in the special "problem" user accounts.
- Produce reusable test cases and clear bug reports.
- Identify which tests are good candidates for automation (Playwright).

## 2. Scope

### In scope
| Area | Includes |
|---|---|
| Authentication | Login (valid, invalid, empty, locked-out), logout, direct URL access |
| Inventory | Product list, product details, sorting |
| Cart | Add, remove, badge count, persistence |
| Checkout | Customer info form validation, order overview (totals and tax), order completion, cancel |
| Menu | Burger menu items (All Items, About, Logout, Reset App State) |
| User types | standard_user, locked_out_user, problem_user, performance_glitch_user |
| Browsers | Chrome, Firefox, Safari/WebKit (latest versions) |

### Out of scope
- Real payment processing (the app has none)
- Load, stress, and penetration testing
- Native mobile apps
- Full accessibility audit (only basic keyboard and label checks if time allows)
- Backend/API testing (the site is a front-end demo with no public API)

## 3. Features and risk ranking

| Feature | Risk | Reason |
|---|---|---|
| Checkout | **High** | Revenue path. If it fails, no sales |
| Login | **High** | Gate to everything, security-relevant |
| Cart | **High** | Feeds checkout, totals must be right |
| Inventory and sorting | Medium | Affects discovery, not purchase directly |
| Product details | Medium | Wrong info misleads buyers |
| Burger menu | Low | Supporting navigation |

Higher risk means more test cases, tested earlier and automated first.

## 4. Test approach

| Activity | How |
|---|---|
| **Functional testing** | Manual execution of the 20 scripted test cases in `test-cases/` |
| **Exploratory testing** | 60-minute timeboxed sessions per user type. Charter: "explore checkout as problem_user to discover failures" |
| **Negative testing** | Empty fields, wrong credentials, direct URL access, locked user |
| **Regression** | Re-run all cases after each fix |
| **Smoke** | TC-01, TC-12, TC-18 (login, add to cart, complete order) after every new deploy |
| **Automation (later)** | Smoke and stable regression cases with Playwright. One UI test per critical flow. The test pyramid applies: this app has only a UI layer, so keep the suite small |

**Techniques used:** equivalence partitioning (valid vs invalid login), rule checks (tax = 8%), state transition (cart empty → has items → order placed), error guessing (special users).

## 5. Test environment

| Item | Value |
|---|---|
| URL | https://www.saucedemo.com |
| Browsers | Chrome, Firefox, Safari (WebKit), latest stable |
| OS | Windows 11 / macOS (any) |
| Viewports | Desktop 1920x1080, mobile 375x667 (visual check only) |
| Tools | Browser DevTools, Playwright (optional), Git/GitHub |

## 6. Test data

**Password for all users:** `secret_sauce`

| Username | Expected behavior |
|---|---|
| `standard_user` | Normal, works as designed |
| `locked_out_user` | Login is blocked with an error |
| `problem_user` | Built-in UI and function faults (images, sorting, forms) |
| `performance_glitch_user` | Login is deliberately slow |

**Products:**

| Product | Price |
|---|---|
| Sauce Labs Backpack | $29.99 |
| Sauce Labs Bike Light | $9.99 |
| Sauce Labs Bolt T-Shirt | $15.99 |
| Sauce Labs Fleece Jacket | $49.99 |
| Sauce Labs Onesie | $7.99 |
| Test.allTheThings() T-Shirt (Red) | $15.99 |

**Checkout form data:** First name `Jane`, last name `Doe`, postal code `560001`.

## 7. Entry and exit criteria

**Entry (can start testing when):**
- Site is reachable and the login page loads
- Test plan and test cases are reviewed
- Test data (users) is available

**Exit (testing is done when):**
- All 20 test cases have been executed at least once
- All P1 cases pass on `standard_user`, or failures are logged as bugs
- No open Critical bugs without a decision
- All bugs are documented with steps, expected and actual results

## 8. Suspension and resumption

- **Suspend** if the site is down or login is broken for all users.
- **Resume** once the site is reachable and a smoke run passes.

## 9. Defect management

| Severity (impact on the product) | Meaning | Example |
|---|---|---|
| **Critical** | Blocks a core flow, no workaround | Cannot complete checkout |
| **Major** | Feature broken, workaround exists | Sorting does nothing |
| **Minor** | Small functional issue | Wrong error text |
| **Trivial** | Cosmetic | Misaligned icon |

| Priority (how soon to fix) | Meaning |
|---|---|
| **P1** | Fix immediately |
| **P2** | Fix in this release |
| **P3** | Fix when possible |

**Lifecycle:** New → Assigned → In Progress → Fixed → Retest → Closed (or Reopened).

Each bug report includes: ID, title, severity, priority, environment, steps to reproduce, expected result, actual result, evidence (screenshot), and the related test case.

## 10. Risks and mitigations

| Risk | Mitigation |
|---|---|
| Demo site changes or goes down | Record dates and browser versions, keep screenshots as evidence |
| Special users behave differently over time | Re-verify each bug before reporting |
| Browser differences cause inconsistent results | Note browser and version on every result |
| Limited time | Execute High-risk areas first |

## 11. Deliverables

- This test plan (`docs/test-plan.md`)
- Test cases (`test-cases/test-cases.md`)
- Bug reports (`bug-reports/`)
- Screenshots (`screenshots/`)
- Test summary in the README

## 12. Metrics to report

- Test cases planned vs executed
- Pass / fail / blocked count
- Bugs by severity
- Pass rate per module

## 13. Assumptions

- Special users (such as `problem_user`) are built with intentional faults. For this practice project those faults are treated as defects, as they would be if found in a real product.
- Expected results are based on standard e-commerce behavior and the visible behavior of `standard_user`.
