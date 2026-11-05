# Sauce Demo QA Project

A manual QA project for [saucedemo.com](https://www.saucedemo.com), a sample e-commerce app. It contains a **test plan**, **20 test cases**, and **3 bug reports**, written the way a QA engineer would deliver them on a real project.

![Type](https://img.shields.io/badge/type-QA%20portfolio-blue)
![Test cases](https://img.shields.io/badge/test%20cases-20-green)
![Bugs](https://img.shields.io/badge/bugs%20reported-3-red)

## What this project shows

- Planning: scope, risk ranking, approach, entry/exit criteria
- Designing test cases: positive, negative, smoke, regression, non-functional
- Reporting defects: clear steps, expected vs actual, severity and priority
- Thinking about automation: which cases to automate first (see the test pyramid)

## Repository structure

```
saucedemo-qa-project/
├── docs/
│   └── test-plan.md                 # Part 1: the test plan
├── test-cases/
│   └── test-cases.md                # Part 2: 20 test cases
├── bug-reports/
│   ├── _bug-report-template.md
│   ├── BUG-001-problem-user-same-image-for-all-products.md
│   ├── BUG-002-problem-user-sorting-does-not-work.md
│   └── BUG-003-problem-user-cannot-enter-last-name-in-checkout.md
├── screenshots/                     # evidence for bug reports
└── README.md
```

## Quick links

| Deliverable | File |
|---|---|
| Test plan | [docs/test-plan.md](docs/test-plan.md) |
| Test cases | [test-cases/test-cases.md](test-cases/test-cases.md) |
| Bug report template | [bug-reports/_bug-report-template.md](bug-reports/_bug-report-template.md) |

## Application under test

| | |
|---|---|
| URL | https://www.saucedemo.com |
| Password for all users | `secret_sauce` |
| Users used | `standard_user`, `locked_out_user`, `problem_user`, `performance_glitch_user` |

## Test coverage

| Module | Test cases | IDs |
|---|---|---|
| Login and Logout | 7 | TC-01 to TC-07 |
| Inventory and Details | 4 | TC-08 to TC-11 |
| Cart | 4 | TC-12 to TC-15 |
| Checkout | 4 | TC-16 to TC-19 |
| Non-functional | 1 | TC-20 |
| **Total** | **20** | |

**Smoke set:** TC-01, TC-12, TC-18.

## Bugs reported

| ID | Title | Severity | Priority |
|---|---|---|---|
| [BUG-001](bug-reports/BUG-001-problem-user-same-image-for-all-products.md) | All products show the same image for `problem_user` | Major | P2 |
| [BUG-002](bug-reports/BUG-002-problem-user-sorting-does-not-work.md) | Sorting has no effect for `problem_user` | Major | P2 |
| [BUG-003](bug-reports/BUG-003-problem-user-cannot-enter-last-name-in-checkout.md) | Last Name field fails at checkout for `problem_user` | Critical | P1 |

> **Note:** `problem_user` is built by Sauce Labs with intentional faults for practice. Here those faults are reported as defects, the way they would be in a real product.

## How to use this repo

1. Read the [test plan](docs/test-plan.md) to see scope and approach.
2. Open [test-cases.md](test-cases/test-cases.md) and execute each case in the browser.
3. Update the **Status** column (Pass / Fail / Blocked).
4. For every failure, copy the bug template, fill it in, and save screenshots in `screenshots/`.
5. Update the summary tables in this README.

## Test execution summary

_Fill in after running the tests._

| Metric | Value |
|---|---|
| Date executed | |
| Browser and version | |
| Cases executed | / 20 |
| Passed | |
| Failed | |
| Blocked | |
| Bugs found | 3 |

## Next steps

- [ ] Automate the smoke set (TC-01, TC-12, TC-18) with Playwright
- [ ] Add the remaining P1 cases to the automated suite
- [ ] Run cases on Firefox and Safari and record differences
- [ ] Add a basic accessibility check (keyboard navigation, labels)

## What I learned

_Add 3-4 lines in your own words: what surprised you, what was hard, what you would do differently._

## Author

**Your Name**: [GitHub](https://github.com/your-username) · [LinkedIn](https://linkedin.com/in/your-profile)
