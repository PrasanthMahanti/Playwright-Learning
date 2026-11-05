# Notes: Saucedemo QA Project

Written in your **Learned · Confused · Built · Explained** format. The "Confused" and "Explained" sections are my guesses at your gaps, so edit them to match what you actually found unclear.

**Date:** 2026-11-05 | **Topic:** Test plan, test cases, bug reports, Git push

---

## 1. Learned

### Test plan
- **Why it exists:** so the team agrees on what will be tested, how, and when to stop, *before* testing starts.
- **Key parts:** scope (in and out), approach, environment, test data, entry and exit criteria, risks, deliverables.
- **Scope has two sides.** "Out of scope" matters as much as "in scope" because it sets expectations. *Example: no load testing on saucedemo.*
- **Risk-based testing:** test the money path first. Checkout and login are High risk, the burger menu is Low.
- **Entry criteria** = when you can start. **Exit criteria** = when you can stop.

### Test case
- **Anatomy:** ID, title, preconditions, steps, expected result, priority, type.
- **Good test cases are:** one purpose each, specific, repeatable by someone else, and have a clear expected result.
- **Weak:** "Check checkout works."
- **Strong:** "Add Backpack and Bike Light, checkout, verify total is $43.18."
- **Positive vs negative:** TC-01 (valid login) vs TC-02 to TC-05 (wrong password, empty fields, locked user).
- **Calculate expected results yourself.** $39.98 × 8% = $3.1984, which rounds to $3.20, so total $43.18.

### Bug report
- **Anatomy:** title, severity, priority, environment, steps, expected, actual, evidence.
- **Severity** = how bad the impact is (technical). **Priority** = how soon to fix (business).
- **Examples:**
  - Cannot complete checkout → Critical severity, P1 priority
  - Wrong images → Major severity, P2 priority
- **A good bug report lets a developer reproduce the bug without asking you anything.**
- **Title formula:** `[Module] What is wrong, for whom`

### Git and GitHub
- **Flow:** `git init` → `git add .` → `git commit` → `git remote add` → `git push`.
- Git is on your machine. GitHub is the online copy.
- Don't tick "Add README" on GitHub if you already have one locally, or the push is rejected.

> **Memory hook:** *The plan says what to test, test cases say how, bug reports say what broke, Git shows it to the world.*

---

## 2. Confused

- [ ] **Severity vs priority.** Can a bug be low severity but high priority? *(Yes. A typo in the company logo is cosmetic but urgent for the brand.)*
- [ ] **Smoke vs sanity vs regression** within *this* project: which cases belong to which?
- [ ] **How many test cases are enough?** Why 20 and not 50?
- [ ] **Why does `problem_user` count as a bug?** It's built to be faulty. *(Treat it as a real product: if users saw this, it'd be a defect.)*
- [ ] **What if I can't reproduce a bug every time?** *(Report it with frequency, e.g. "3 out of 5 attempts".)*

---

## 3. Built

| Deliverable | File | Size |
|---|---|---|
| Test plan | `docs/test-plan.md` | 13 sections |
| Test cases | `test-cases/test-cases.md` | 20 cases, 5 modules |
| Bug reports | `bug-reports/` | 3 bugs and 1 template |
| README | `README.md` | coverage, bugs, execution summary |

- **Smoke set:** TC-01, TC-12, TC-18
- **Bugs:** BUG-001 (images), BUG-002 (sorting), BUG-003 (checkout, Critical)
- **Commands used:**

```bash
git init
git add .
git commit -m "message"
git push -u origin main
```

- **Still to do:** run the tests, fill in Status, add screenshots, push to GitHub.

---

## 4. Explained

> A test plan is a short document that says what we're going to test, what we're not, and how we'll know we're done. Test cases are the step-by-step checks: do this, expect that. When a check fails, I write a bug report so clear that a developer can reproduce it without talking to me. Severity says how bad the bug is, priority says how soon it must be fixed. Finally I put everything in a Git repo and push it to GitHub so others can see my work.

**Test of understanding:** can you explain severity vs priority with *your own* example, not mine?

---

## Quick comparison tables

| | Test plan | Test case | Bug report |
|---|---|---|---|
| **Answers** | What, how, when, who | Did this one thing work? | What broke and how to see it |
| **Written** | Before testing | Before executing | After a failure |
| **Size** | 1 per project | Many | One per defect |

| | Severity | Priority |
|---|---|---|
| **Means** | Impact on the product | Urgency of the fix |
| **Set by** | QA | Product/business |
| **Example** | Checkout broken = Critical | Fix before launch = P1 |

---

## Self-test (answer without scrolling up)

1. What's the difference between entry and exit criteria?
2. Why is checkout ranked High risk?
3. Write the expected result for adding Fleece Jacket ($49.99) alone: item total, tax, total.
4. Give one example of low severity but high priority.
5. What are the 3 most important parts of a bug report?
6. Why shouldn't you tick "Add README" when creating a repo you'll push to?

**Answers:** (1) Entry = when testing can begin, exit = when it can stop. (2) It's the revenue path, so a failure means no sales. (3) $49.99, tax $4.00 (49.99 × 0.08 = 3.9992), total $53.99. (4) A typo or wrong logo on the home page. (5) Steps to reproduce, expected result, actual result. (6) The remote then has a commit your local repo doesn't, so the push is rejected.

---

## Next step
Run the 20 test cases, then update the **Confused** section with what you resolved.

Want me to save this as a `.md` file for your `notes/` folder?