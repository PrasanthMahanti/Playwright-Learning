# 20 Test Ideas for an E-commerce App (Flipkart/Amazon/Meesho style)

## Unit tests (bottom of the pyramid)

| # | Test idea | Decision | Why |
|---|---|---|---|
| 1 | **Price calculation:** MRP, discount %, coupon, GST, shipping fee, rounding (₹499.50?) | **Automate** | Pure logic, many boundary cases, runs thousands of times |
| 2 | **COD eligibility rules:** allowed only under ₹50,000, not for certain pincodes or categories | **Automate** | Rule-based, data-driven, fast |

## API / Integration tests (middle layer)

| # | Test idea | Decision | Why |
|---|---|---|---|
| 3 | **Search API:** keyword "running shoes" returns 200, non-empty results, response under 2s | **Automate** | Stable, fast, no browser needed |
| 4 | **Pincode serviceability API:** valid, invalid, and unserviceable pincodes; delivery date estimate | **Automate** | Data-driven, many inputs |
| 5 | **Cart API:** add, update quantity, remove, max quantity limit, out-of-stock item | **Automate** | Core flow, stable contract |
| 6 | **Auth API:** wrong password, expired token, OTP retry limit | **Automate** | Security-critical, deterministic |
| 7 | **Order placed → inventory decreases** (and restores on cancellation) | **Automate** | Cross-service integration, a bug here means overselling |
| 8 | **Payment gateway failure/timeout:** mock a UPI failure, check order status and retry behavior | **Automate** | Hard to trigger manually; mocks make it repeatable |
| 9 | **Notifications:** order confirmation SMS/email triggered with correct order ID and amount | **Automate** | Check the trigger and content via API/test inbox |

## UI / E2E tests (top of the pyramid, keep few)

| # | Test idea | Decision | Why |
|---|---|---|---|
| 10 | **Happy-path purchase:** login → search → add to cart → checkout (sandbox payment) → order confirmation | **Automate** | The most critical user journey. Keep it to 1-2 E2E tests |
| 11 | **Filters and sort** on listing page (price, brand, rating) | **Hybrid** | Test the logic at API level. One UI test confirms filters actually appear and apply |

## Smoke, sanity and regression

| # | Test idea | Decision | Why |
|---|---|---|---|
| 12 | **Smoke:** after each deploy, the home page loads, login works, search works, product page opens, cart opens | **Automate** | Runs on every build in CI, minutes only |
| 13 | **Sanity:** the dev fixed a "coupon not applying on 2nd item" bug, so check coupon behavior around that area only | **Manual** (or a quick script) | Narrow, ad hoc, one-time check |
| 14 | **Regression:** return and refund flow (request return → pickup scheduled → refund initiated) | **Hybrid** | Automate the API and status changes. Physical pickup and bank credit need manual or sandbox verification |

## Non-functional tests

| # | Test idea | Decision | Why |
|---|---|---|---|
| 15 | **Performance/load:** simulate 1 lakh users on a sale day (Big Billion Days, Prime Day) | **Automate** | Humans can't generate load. Tools: JMeter, k6, Locust |
| 16 | **Security:** change another user's order ID in the URL (IDOR), try SQL injection in the search box | **Hybrid** | Automated scans catch the common issues. Skilled manual pen testing finds the creative ones |
| 17 | **Compatibility:** Chrome, Safari, Firefox, Android and iOS, small and large screens | **Hybrid** | Automate on a device cloud (BrowserStack). Manually eyeball layout glitches |

## Human-judgment tests

| # | Test idea | Decision | Why |
|---|---|---|---|
| 18 | **Usability:** is checkout confusing? Can a first-time user find the "Return" option? | **Manual** | Needs human opinion and feel |
| 19 | **Exploratory:** a brand-new feature, e.g. live shopping or video reels, still changing | **Manual** | Unstable and unscripted, so automation would break constantly |
| 20 | **Visual check:** sale-day banners, product images, text overflow in Hindi or regional languages | **Mostly manual** | Subjective. Visual regression tools (Percy, Applitools) can help partially |

---

## Summary

| Decision | Count | Tests |
|---|---|---|
| **Automate** | 11 | #1-10, #12, #15 |
| **Hybrid** | 4 | #11, #14, #16, #17 |
| **Manual** | 4 | #13, #18, #19, #20 (mostly manual) |

Notice the shape: most automation sits in **unit and API layers**, with only a **thin UI layer** (#10, #11). That's the test pyramid in practice.

## Things worth noticing

- **Test price logic (#1) at the unit level, not through the browser.** Don't test 50 discount rules via UI.
- **Mock external dependencies** like payment gateways and SMS providers. Real ones cause flakiness.
- **Sale-day performance (#15)** is one of the most valuable tests for these apps, because one outage costs crores.
- **India-specific ideas** like UPI, COD, pincode serviceability, and regional-language text make strong interview talking points.

---

**Try it yourself:** pick any 3 tests from the list and tell me which pyramid layer, which type (smoke/sanity/regression), and which tool you'd use. I'll check your answers.