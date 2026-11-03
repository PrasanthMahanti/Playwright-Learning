# Study Notes: Test Design Basics

## 1. Test scenario vs test case

**Test scenario**: a high-level statement of *what* to test. One line, no steps.
**Test case**: a detailed description of *how* to test it: preconditions, test data, steps, expected result.

One scenario usually produces many test cases.

| | Test Scenario | Test Case |
|---|---|---|
| Level | High-level idea | Detailed and specific |
| Answers | "What to test?" | "How to test it?" |
| Contains | One-line description | ID, preconditions, data, steps, expected result, priority |
| Count | Few | Many per scenario |

**Example (login page):**
- Scenario: *Verify login with invalid credentials.*
- Test cases from it:
  - Valid email + wrong password
  - Unregistered email + valid password
  - Empty password
  - SQL injection text in the email field

**Memory trick:** the scenario is the chapter title, and the test cases are the pages inside it.

---

## 2. Positive vs negative testing

**Positive testing**: give the system *valid* input and check that it works as expected. It proves the system does what it should.

**Negative testing**: give the system *invalid, unexpected, or harmful* input and check that it handles it gracefully (clear error, no crash, no security leak). It proves the system doesn't break when misused.

| | Positive | Negative |
|---|---|---|
| Input | Valid | Invalid or unexpected |
| Goal | Confirm correct behavior | Confirm safe failure |
| Login example | Correct email + correct password | Wrong password, blank fields, `' OR '1'='1` |
| Expected outcome | Success | Proper error message, no crash |

**Important:** both are needed. A system that works with good input but crashes on bad input is not ready for real users.

---

## 3. Equivalence partitioning (EP)

**Idea:** divide all possible inputs into groups (partitions) where the system should behave the *same* way for every value in the group. Then test just **one value from each group** instead of every value.

**Why:** you can't test every possible input. EP cuts the number of tests while keeping coverage.

**Example:** a password must be 8 to 16 characters.

| Partition | Range | Valid? | Pick one test value |
|---|---|---|---|
| Too short | 0 to 7 characters | Invalid | 4 characters |
| Valid | 8 to 16 characters | Valid | 12 characters |
| Too long | 17+ characters | Invalid | 20 characters |

Three tests cover the whole input space. If 12 characters works, 10 and 14 should too, so there's no need to test them.

---

## 4. Boundary value analysis (BVA)

**Idea:** bugs love the *edges*. Developers often make off-by-one mistakes (`<` instead of `<=`). So test values **at and next to each boundary**.

**Same example:** password length 8 to 16.

The boundaries are 8 and 16. Test the value just below, on, and just above each:

| Test value | Length | Expected |
|---|---|---|
| Below lower boundary | 7 | Rejected |
| Lower boundary | 8 | Accepted |
| Just above lower boundary | 9 | Accepted |
| Just below upper boundary | 15 | Accepted |
| Upper boundary | 16 | Accepted |
| Above upper boundary | 17 | Rejected |

**Another example:** age field accepts 18 to 60.
Test: 17, 18, 19, 59, 60, 61.

---

## 5. How they work together

EP and BVA are partners:

1. **EP first:** split the input into valid and invalid groups.
2. **BVA next:** within those groups, test the edges, where bugs hide.

Then mix in positive and negative testing: valid partitions give positive tests, invalid partitions give negative tests.

**Whole picture for "age 18 to 60":**

| Technique | Values tested |
|---|---|
| EP (one per group) | 10 (invalid), 35 (valid), 70 (invalid) |
| BVA (edges) | 17, 18, 19, 59, 60, 61 |
| Positive tests | 18, 19, 35, 59, 60 |
| Negative tests | 10, 17, 61, 70, letters, blank |

---

## Quick self-test

1. What's the difference between a test scenario and a test case? Give an example of each.
2. Is entering blank fields on a login page a positive or negative test?
3. A field accepts numbers from 1 to 100. What are the three equivalence partitions?
4. For the same field, which values would BVA test?
5. Why is BVA more likely to find bugs than random values?

**Answers to check yourself:** (3) below 1, 1 to 100, above 100. (4) 0, 1, 2, 99, 100, 101.

Want me to turn this into a quiz, like last time?