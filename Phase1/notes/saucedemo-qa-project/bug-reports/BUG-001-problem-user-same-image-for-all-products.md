# BUG-001: [Inventory] All products show the same image for problem_user

> **Before submitting:** reproduce this yourself, fill in the environment and date, and attach screenshots to `../screenshots/`.

| Field | Value |
|---|---|
| **Status** | New |
| **Severity** | Major |
| **Priority** | P2 |
| **Reported by** | _your name_ |
| **Date** | _YYYY-MM-DD_ |
| **Related test case** | TC-08 (repeated with `problem_user`) |
| **Environment** | _Chrome xxx, Windows/macOS_, https://www.saucedemo.com |
| **User / test data** | `problem_user` / `secret_sauce` |

## Preconditions
Browser is open on the login page. No items in the cart.

## Steps to reproduce
1. Go to https://www.saucedemo.com
2. Log in with `problem_user` and `secret_sauce`
3. Look at the product images on the inventory page
4. Click any product name to open its details page

## Expected result
Each of the 6 products shows its own product image (backpack, bike light, t-shirt, jacket, onesie, red t-shirt), the same as for `standard_user`.

## Actual result
All products display the same placeholder image, so shoppers cannot tell products apart visually. The image also does not match the product name on the details page.

## Evidence
![screenshot](../screenshots/BUG-001.png)

## Notes
- Occurs every time for this user.
- Impact: in a real shop, wrong images cause returns and lost trust.
- Compare against `standard_user`, whose images are correct.
