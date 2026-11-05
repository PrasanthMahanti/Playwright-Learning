# BUG-002: [Inventory] Sorting has no effect for problem_user

> **Before submitting:** reproduce this yourself, fill in the environment and date, and attach screenshots to `../screenshots/`.

| Field | Value |
|---|---|
| **Status** | New |
| **Severity** | Major |
| **Priority** | P2 |
| **Reported by** | _your name_ |
| **Date** | _YYYY-MM-DD_ |
| **Related test case** | TC-10 (repeated with `problem_user`) |
| **Environment** | _Chrome xxx, Windows/macOS_, https://www.saucedemo.com |
| **User / test data** | `problem_user` / `secret_sauce` |

## Preconditions
Logged in as `problem_user`. Inventory page is open, default order (Name A to Z).

## Steps to reproduce
1. Open the sort dropdown at the top right of the inventory page
2. Select **Price (low to high)**
3. Observe the product order
4. Repeat with **Price (high to low)** and **Name (Z to A)**

## Expected result
Products re-order to match the selected option. For **Price (low to high)**, the first product is $7.99 (Onesie) and the last is $49.99 (Fleece Jacket).

## Actual result
The dropdown shows the selected option, but the product order does not change. The list does not match the label shown in the sort control.

## Evidence
![screenshot](../screenshots/BUG-002.png)

## Notes
- Occurs for every sort option.
- Workaround: none from the UI, the user has to scan prices manually.
- `standard_user` sorts correctly, which confirms the expected behavior.
