# Test Cases: Sauce Demo

**Application:** https://www.saucedemo.com
**Default user:** `standard_user` / `secret_sauce` (unless a case says otherwise)
**Total cases:** 20

**Legend**
- **Priority:** P1 = critical path, P2 = important, P3 = nice to have
- **Type:** Smoke, Functional, Negative, Regression, Non-functional
- **Automate?:** Yes = good Playwright candidate, No = keep manual
- **Status:** fill in after execution (Pass / Fail / Blocked). Left as `Not run` until you test.

---

## Module 1: Login and Logout

| ID | Title | Steps | Expected result | Priority | Type | Automate? | Status |
|---|---|---|---|---|---|---|---|
| TC-01 | Login with valid credentials | 1. Open the site<br>2. Enter `standard_user` and `secret_sauce`<br>3. Click **Login** | Inventory page opens with the title "Products" and 6 products | P1 | Smoke | Yes | Not run |
| TC-02 | Login with wrong password | 1. Enter `standard_user` and `wrong_pass`<br>2. Click **Login** | User stays on login page. Error: "Username and password do not match any user in this service" | P1 | Negative | Yes | Not run |
| TC-03 | Login with empty username | 1. Leave username blank<br>2. Enter `secret_sauce`<br>3. Click **Login** | Error: "Username is required" | P2 | Negative | Yes | Not run |
| TC-04 | Login with empty password | 1. Enter `standard_user`<br>2. Leave password blank<br>3. Click **Login** | Error: "Password is required" | P2 | Negative | Yes | Not run |
| TC-05 | Login as locked-out user | 1. Enter `locked_out_user` and `secret_sauce`<br>2. Click **Login** | Login is blocked. Error: "Sorry, this user has been locked out." | P1 | Negative | Yes | Not run |
| TC-06 | Access inventory page without logging in | 1. In a fresh browser session, open `/inventory.html` directly | User is not shown the products. Error says the page can only be accessed when logged in | P1 | Negative (security) | Yes | Not run |
| TC-07 | Logout | 1. Log in as `standard_user`<br>2. Open the burger menu<br>3. Click **Logout**<br>4. Press the browser Back button | Login page is shown after logout. Back button does not give access to the inventory | P1 | Functional | Yes | Not run |

## Module 2: Inventory and Product Details

| ID | Title | Steps | Expected result | Priority | Type | Automate? | Status |
|---|---|---|---|---|---|---|---|
| TC-08 | Product list displays correctly | 1. Log in<br>2. Review the inventory page | 6 products shown. Each has an image, name, description, price, and **Add to cart** button. Each product has its own image | P2 | Functional | Yes | Not run |
| TC-09 | Sort by Name (Z to A) | 1. Log in<br>2. Choose **Name (Z to A)** in the sort dropdown | Products are ordered Z to A. First is "Test.allTheThings() T-Shirt (Red)", last is "Sauce Labs Backpack" | P2 | Functional | Yes | Not run |
| TC-10 | Sort by Price (low to high) | 1. Log in<br>2. Choose **Price (low to high)** | First product is $7.99 (Onesie), last is $49.99 (Fleece Jacket). Prices are in ascending order | P2 | Functional | Yes | Not run |
| TC-11 | Open product details page | 1. Log in<br>2. Click the name "Sauce Labs Backpack"<br>3. Click **Back to products** | Details page shows the same name, description, and price ($29.99) as the list. Back button returns to inventory | P2 | Functional | Yes | Not run |

## Module 3: Cart

| ID | Title | Steps | Expected result | Priority | Type | Automate? | Status |
|---|---|---|---|---|---|---|---|
| TC-12 | Add a single item to cart | 1. Log in<br>2. Click **Add to cart** on Sauce Labs Backpack | Button changes to **Remove**. Cart badge shows 1 | P1 | Smoke | Yes | Not run |
| TC-13 | Add multiple items to cart | 1. Add Backpack, Bike Light, and Bolt T-Shirt<br>2. Click the cart icon | Badge shows 3. Cart lists the 3 items with correct names, prices ($29.99, $9.99, $15.99), and quantity 1 | P1 | Functional | Yes | Not run |
| TC-14 | Remove an item from the cart page | 1. Add 2 items<br>2. Open the cart<br>3. Click **Remove** on one item | Item disappears from the list. Badge decreases to 1 | P2 | Functional | Yes | Not run |
| TC-15 | Cart keeps items after navigating away | 1. Add 1 item<br>2. Open the cart<br>3. Click **Continue Shopping**<br>4. Open the cart again | Item is still in the cart. Badge still shows 1 | P2 | Regression | Yes | Not run |

## Module 4: Checkout

| ID | Title | Steps | Expected result | Priority | Type | Automate? | Status |
|---|---|---|---|---|---|---|---|
| TC-16 | Checkout with missing first name | 1. Add an item and click **Checkout**<br>2. Leave First Name blank, enter last name and postal code<br>3. Click **Continue** | Error: "First Name is required". User stays on the same step | P2 | Negative | Yes | Not run |
| TC-17 | Order overview totals and tax | 1. Add Backpack ($29.99) and Bike Light ($9.99)<br>2. Checkout with valid details<br>3. Check the overview | Item total $39.98. Tax $3.20 (8%). Total $43.18 | P1 | Functional | Yes | Not run |
| TC-18 | Complete an order (happy path) | 1. Add an item<br>2. Checkout with `Jane`, `Doe`, `560001`<br>3. Click **Continue**, then **Finish** | Confirmation page shows "Thank you for your order!". Cart is empty and badge is gone | P1 | Smoke | Yes | Not run |
| TC-19 | Cancel checkout | 1. Add an item and start checkout<br>2. Click **Cancel** on the information page | User returns to the cart. Item is still there | P3 | Functional | Yes | Not run |

## Module 5: Non-functional

| ID | Title | Steps | Expected result | Priority | Type | Automate? | Status |
|---|---|---|---|---|---|---|---|
| TC-20 | Login speed for performance_glitch_user | 1. Enter `performance_glitch_user` and `secret_sauce`<br>2. Click **Login** and time how long until the inventory page appears | Inventory loads within the accepted threshold of 3 seconds | P3 | Non-functional | Yes (timing assertion) | Not run |

---

## Special-user runs

These cases must also be repeated with `problem_user`, because that account has built-in faults:

| Repeat case | Why |
|---|---|
| TC-08 | Product images |
| TC-09, TC-10 | Sorting |
| TC-12, TC-14 | Add and remove buttons |
| TC-16, TC-18 | Checkout form fields |

Failures found are documented in [`bug-reports/`](../bug-reports/).

## Coverage summary

| Module | Cases | P1 | Automate |
|---|---|---|---|
| Login and Logout | 7 | 5 | 7 |
| Inventory and Details | 4 | 0 | 4 |
| Cart | 4 | 2 | 4 |
| Checkout | 4 | 2 | 4 |
| Non-functional | 1 | 0 | 1 |
| **Total** | **20** | **9** | **20** |

**Automation note:** all 20 are automatable. Start with the smoke trio (TC-01, TC-12, TC-18), then add the P1 negatives. Keep the suite small since every test here runs through the UI.
