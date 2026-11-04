# playwright-learning

My learning journal for **Playwright** (TypeScript): notes, practice tests, and small projects, built in public.

The goal is not to collect tutorials. It is to write real tests, break them, fix them, and explain what I learned.

![Playwright](https://img.shields.io/badge/Playwright-TypeScript-2EAD33)
![Status](https://img.shields.io/badge/status-learning-blue)

## What's inside

- **Daily notes** using one template: Learned, Confused, Built, Explained
- **Practice tests** against public demo sites
- **Mini projects**, including an e-commerce test suite (search, cart, checkout)
- **Cheat sheet** of locators, assertions, and commands I actually use

## Project structure

```
playwright-learning/
├── notes/                 # one file per day or topic (see _template.md)
│   └── _template.md
├── tests/
│   ├── 01-basics/         # first test, locators, assertions
│   ├── 02-interactions/   # forms, dropdowns, uploads, dialogs
│   ├── 03-waiting/        # auto-wait, flaky test fixes
│   ├── 04-api/            # request fixture, API testing
│   └── 05-projects/       # e-commerce suite, POM
├── pages/                 # Page Object Model classes
├── playwright.config.ts
├── package.json
└── README.md
```

## Getting started

### Prerequisites

- [Node.js](https://nodejs.org) 18 or newer
- Git
- VS Code (optional, with the Playwright extension)

### Installation

```bash
git clone https://github.com/<your-username>/playwright-learning.git
cd playwright-learning
npm install
npx playwright install
```

`npx playwright install` downloads the browsers (Chromium, Firefox, WebKit).

## Running tests

```bash
# run everything (headless)
npx playwright test

# run one file
npx playwright test tests/01-basics/first-test.spec.ts

# watch the browser
npx playwright test --headed

# debug step by step
npx playwright test --debug

# open the HTML report
npx playwright show-report
```

Handy tools:

- `npx playwright codegen https://www.saucedemo.com` records actions into test code
- **UI mode:** `npx playwright test --ui` for a time-travel debugger

## Learning roadmap

- [ ] **Week 1: Basics.** Install, first test, `page.goto`, `expect`
- [ ] **Week 1: Locators.** `getByRole`, `getByText`, `getByLabel`, `getByTestId`
- [ ] **Week 2: Interactions.** Click, fill, select, checkbox, file upload, dialogs
- [ ] **Week 2: Auto-waiting and assertions.** Why Playwright rarely needs `sleep`
- [ ] **Week 3: Test structure.** `describe`, hooks, fixtures, tags, retries
- [ ] **Week 3: Page Object Model.** Reusable page classes
- [ ] **Week 4: API testing.** The `request` fixture, mixing API and UI
- [ ] **Week 4: CI.** Run tests with GitHub Actions
- [ ] **Project:** end-to-end suite for a Flipkart/Amazon-style demo shop

## Practice sites

| Site | Good for |
|---|---|
| [saucedemo.com](https://www.saucedemo.com) | Login, cart, checkout flow |
| [playwright.dev](https://playwright.dev) | Docs, plus a real site to practice locators |
| [the-internet.herokuapp.com](https://the-internet.herokuapp.com) | Dialogs, uploads, dynamic loading, iframes |
| [practice-automation.com](https://practice-automation.com) | Forms and varied UI elements |

## How I take notes

Every study session gets one file in `notes/`, copied from [`notes/_template.md`](notes/_template.md):

| Section | Question it answers |
|---|---|
| **Learned** | What can I do now that I couldn't before? |
| **Confused** | What still doesn't make sense? |
| **Built** | What did I actually write or run? |
| **Explained** | Can I teach it in my own words? |

If I can't fill in **Explained**, I haven't learned it yet.

## Progress log

| Date | Topic | Note |
|---|---|---|
| YYYY-MM-DD | Setup and first test | [notes/2026-11-05-setup.md](notes/2026-11-05-setup.md) |

## Resources

- [Official Playwright docs](https://playwright.dev/docs/intro)
- [Best practices guide](https://playwright.dev/docs/best-practices)
- [Playwright YouTube channel](https://www.youtube.com/@Playwrightdev)

## License

MIT
