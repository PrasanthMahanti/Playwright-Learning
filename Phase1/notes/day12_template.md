# YYYY-MM-DD: Topic name

**Time spent:** 0 min  |  **Confidence:** 1 / 2 / 3 / 4 / 5  |  **Resources:** [link]()

---

## 1. Learned

*What can I do or understand now that I couldn't before? Own words, short sentences.*

- **Why it exists:** the problem this solves
- Key idea 1, with a mini example
- Key idea 2, with a mini example

> Memory hook: an analogy or one-liner that makes it stick.

---

## 2. Confused

*Be honest. Unclear things are the most valuable part of these notes.*

- [ ] Question I couldn't answer yet
- [ ] Something that behaved unexpectedly
- [ ] A term I nodded along to but don't really get

Resolved later (add the date and the answer):

- [x] ~~Old question~~ → answer, learned on YYYY-MM-DD

---

## 3. Built

*What did I actually write or run today? Code beats theory.*

```ts
import { test, expect } from '@playwright/test';

test('example', async ({ page }) => {
  // paste the smallest version of what I built
});
```

- **Run with:** `npx playwright test <file>`
- **Result:** passed / failed, and what I saw
- **Bug I hit and how I fixed it:**
- **Repo link:** [tests/...](../tests/)

---

## 4. Explained

*Teach it to a friend who has never seen Playwright. No jargon without a definition. Aim for 3 to 5 sentences.*

> Write the explanation here.

**Test of understanding:** could I explain this without looking at Learned? If not, rewrite Learned and try again.

---

## Self-test (answer tomorrow, without looking)

1. Question?
2. Question?
3. Question?

## Next step

- One concrete thing to do in the next session

---
---

# Filled example (delete this part in real notes)

# 2026-11-05: Locators

**Time spent:** 60 min  |  **Confidence:** 3 / 5  |  **Resources:** [Playwright locators docs](https://playwright.dev/docs/locators)

## 1. Learned

- **Why it exists:** tests break when they depend on fragile things like CSS classes. Locators find elements the way a *user* would.
- `getByRole('button', { name: 'Login' })` finds the button by what it is and what it says.
- Locators **auto-wait** and retry, so I don't need `sleep()`.
- Preferred order: `getByRole` → `getByLabel` → `getByText` → `getByTestId` → CSS/XPath (last resort).

> Memory hook: locate things like a person would, not like a developer would.

## 2. Confused

- [ ] When is `getByTestId` better than `getByRole`?
- [ ] What happens when a locator matches 2 elements?
- [x] ~~Does a locator wait?~~ Yes, it waits when I act on it (click, fill), learned 2026-11-05.

## 3. Built

```ts
import { test, expect } from '@playwright/test';

test('login page loads', async ({ page }) => {
  await page.goto('https://www.saucedemo.com');
  await page.getByPlaceholder('Username').fill('standard_user');
  await page.getByPlaceholder('Password').fill('secret_sauce');
  await page.getByRole('button', { name: 'Login' }).click();
  await expect(page.getByText('Products')).toBeVisible();
});
```

- **Result:** passed
- **Bug:** first used `getByText('Login')` and it matched 2 elements. Switched to `getByRole`, which fixed it.

## 4. Explained

> A locator is Playwright's way of pointing at something on a page. Instead of saying "the third blue box," I say "the button labelled Login." That way, even if the developers change colors or layout, my test still finds it. Playwright also waits for the element to be ready before clicking, which removes most flaky-test timing problems.

## Self-test

1. Why is `getByRole` preferred over a CSS selector?
2. What does auto-waiting replace?
3. What happens if a locator matches two elements?

## Next step

- Learn `expect` assertions and when they retry
