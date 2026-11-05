# BUG-003: [Checkout] Last Name field does not accept input for problem_user, blocking checkout

> **Before submitting:** reproduce this yourself, note exactly what happens in your run (the field stays empty, or the value goes into another field), fill in the environment and date, and attach screenshots to `../screenshots/`.

| Field | Value |
|---|---|
| **Status** | New |
| **Severity** | Critical |
| **Priority** | P1 |
| **Reported by** | _your name_ |
| **Date** | _YYYY-MM-DD_ |
| **Related test case** | TC-18 (repeated with `problem_user`) |
| **Environment** | _Chrome xxx, Windows/macOS_, https://www.saucedemo.com |
| **User / test data** | `problem_user` / `secret_sauce`, First `Jane`, Last `Doe`, Postal `560001` |

## Preconditions
Logged in as `problem_user` with at least one item in the cart.

## Steps to reproduce
1. Open the cart and click **Checkout**
2. Type `Jane` in **First Name**
3. Type `Doe` in **Last Name**
4. Type `560001` in **Postal Code**
5. Click **Continue**

## Expected result
All three fields keep the values typed. The user moves to "Checkout: Overview".

## Actual result
The Last Name field does not take the typed value as expected. After clicking **Continue**, an error is shown ("Last Name is required") and the user stays on the information step.

## Evidence
![screenshot](../screenshots/BUG-003.png)

## Notes
- Occurs every time for this user.
- Impact: the user cannot complete a purchase, so this blocks the revenue path (hence Critical/P1).
- Workaround: none from the UI.
- `standard_user` completes the same flow without errors.
