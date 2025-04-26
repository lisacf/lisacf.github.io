## Technology Stack

- **SvelteKit**  
  - File-based routing, built-in dev server & adapter support  
  - Zero-config TypeScript and environment support  
- **Vitest**  
  - Native Vite integration (used by SvelteKit)  
  - Fast in-memory unit & integration tests  
  - Works with `@testing-library/svelte` for component testing  
- **Playwright**  
  - Reliable end-to-end browser testing across Chromium, Firefox, WebKit  
  - Automates user flows (tile swapping, match detection, animations)  

> **Yes**—this combo gives a first-class developer experience and lets you drive all game logic and UI through tests from Day 1.

---

## Project Plan

| Phase                                | Goals                                                                 | Deliverables                                                                                                                                  | Testing Focus                                                                                  |
|--------------------------------------|-----------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|
| **1. Environment & Scaffolding**      | • Bootstrap SvelteKit project<br>• Configure Vitest & Playwright      | • `npx sv create match-three-game`<br>• `vitest.config.ts`, Playwright setup script                                                            | • Smoke test: “app loads” unit test<br>• Playwright “homepage renders”                          |
| **2. Core Grid Layout**              | • Render an M×N grid of tiles<br>• Style tiles (CSS/Tailwind)         | • `Grid` Svelte component<br>• Static grid snapshot                                                                                          | • Unit tests for correct cell count<br>• Snapshot tests via Vitest                               |
| **3. Tile Swap Interaction**         | • Click/drag to swap two adjacent tiles<br>• Swap animation           | • `Tile` & `Grid` event handlers<br>• Swap state machine                                                                                     | • Unit tests for swap logic (indexes, bounds)<br>• Playwright flow: “swap two tiles”            |
| **4. Match Detection & Resolution**   | • Detect 3-in-a-row (H/V)<br>• Remove matched tiles<br>• Refill logic  | • `matchEngine` module (pure functions)<br>• Refill algorithm                                                                                 | • Unit tests on `matchEngine` patterns<br>• Playwright: “make a match → tiles disappear & refill” |
| **5. Scoring & Combo Logic**          | • Base points per tile<br>• Bonuses for cascades/combos               | • `ScoreBoard` component<br>• Combo multiplier logic                                                                                         | • Unit tests for scoring rules<br>• E2E: “chain two matches → correct score”                    |
| **6. UI Polish & Animations**         | • Smooth transitions (Svelte `animate`/`transition`)<br>• Responsive  | • CSS animations, mobile breakpoints                                                                                                         | • Playwright visual checks (animation end state)<br>• Accessibility smoke tests                |
| **7. Test Coverage & CI/CD**         | • Integrate Vitest + Playwright in GitHub Actions<br>• Coverage gates | • `.github/workflows/tests.yml`<br>• Badges in README                                                                                         | • CI build passes on every PR<br>• Coverage ≥ 80%                                               |
| **8. Feature Extensions**            | • Power-ups, special tiles<br>• Level progression, themes             | • New Svelte components & logic modules                                                                                                       | • Unit tests per new feature<br>• E2E: full-game playthrough test                              |

---

## Testing Strategy

1. **Test-First Development**  
   - Write a failing test for each piece of game logic (swap, match, score)  
   - Implement just enough code to pass  
   - Refactor safely, backed by tests  

2. **Component-Level**  
   - Use Vitest + `@testing-library/svelte`  
   - Test props, events & DOM updates in isolation  

3. **Pure-Function Modules**  
   - Extract grid/match/score logic into small functions  
   - Cover edge cases: no matches, boundary swaps, chain reactions  

4. **End-to-End**  
   - Playwright scripts mirror real user behavior  
   - Automate flows: start game → swap tiles → detect match → verify score  

---

## Continuous Integration & Workflow

- **GitHub Actions**  
  - Run `vitest --coverage` on every push/PR  
  - Launch headless browser for Playwright tests  
  - Fail build on test failures or coverage drop  

- **Branching Model**  
  - `main`: always green (protected)  
  - Feature branches → PR → CI → Code review → Merge  

- **Developer Feedback Loop**  
  - Fast Vitest watch mode (`npm run test:watch`)  
  - Periodic full-suite CI runs for end-to-end validation  

---

## Tackle your next steps—focus on CI/CD and code quality right after that initial commit, so every PR is automatically validated.

---

## 1. Add Linting & Formatting (ES Lint & Prettier were added as part of the initial setup)

## Summary

Husky is a lightweight JavaScript tool that simplifies the use of Git hooks by leveraging Git’s native `core.hooksPath` mechanism to run project-specific scripts (linters, tests, commit-message validators, etc.) automatically during Git lifecycle events like `pre-commit` and `pre-push` ([Husky](https://typicode.github.io/husky/?utm_source=chatgpt.com), [How to Use Husky and Git Hooks to Automate Actions - GitKraken](https://www.gitkraken.com/blog/husky-git-hooks?utm_source=chatgpt.com)). Installed as an NPM dev-dependency, Husky configures a `.husky/` directory in your repo and intercepts Git commands to invoke the scripts you define ([Husky - NPM](https://www.npmjs.com/package/husky?utm_source=chatgpt.com), [How husky works? - git - Stack Overflow](https://stackoverflow.com/questions/57297444/how-husky-works?utm_source=chatgpt.com)).

---

## What Is Husky?

Husky is an NPM package created by Typicode that makes managing Git hooks painless by allowing you to define hook scripts alongside your code rather than manually editing `.git/hooks/` ([Husky](https://typicode.github.io/husky/?utm_source=chatgpt.com), [Husky - NPM](https://www.npmjs.com/package/husky?utm_source=chatgpt.com)). Instead of hand-writing shell scripts in an internal Git folder, you commit a `.husky/` directory to your repo, which Husky then points Git to via `core.hooksPath` ([typicode/husky: Git hooks made easy woof! - GitHub](https://github.com/typicode/husky?utm_source=chatgpt.com)).

---

## How It Works

1. **Hook Path Redirection**  
   Husky executes `git config core.hooksPath .husky` under the hood, redirecting Git to look in `.husky/` for hook scripts instead of `.git/hooks/` ([Husky](https://typicode.github.io/husky/?utm_source=chatgpt.com), [How husky works? - git - Stack Overflow](https://stackoverflow.com/questions/57297444/how-husky-works?utm_source=chatgpt.com)).

2. **Script Invocation**  
   When you run a Git command (e.g., `git commit`), Git invokes the corresponding hook file in `.husky/`; that file contains shell commands (your lint, test, or formatting scripts) which Husky ensures are executed ([Husky](https://typicode.github.io/husky/?utm_source=chatgpt.com)).

3. **Cross-Platform Support**  
   Hooks are regular POSIX shell scripts, making them compatible across macOS, Linux, and Windows environments ([Husky](https://typicode.github.io/husky/?utm_source=chatgpt.com)).

---

## Key Features

- **Ultra-lightweight**: ~2 kB gzipped, zero dependencies.  
- **Blazing fast**: ≈1 ms per hook.  
- **Full hook support**: All 13 client-side Git hooks (e.g., `pre-commit`, `commit-msg`, `pre-push`).  
- **Cross-platform**: Works on macOS, Linux, Windows, and in GUI/CI environments.  
- **Repo-committable**: Hooks live in `.husky/` and travel with your code.  
- **Native Git integration**: Uses `core.hooksPath` for minimal overhead.  
- **Extensible**: Easily integrates with tools like lint-staged for staged file checks ([Husky](https://typicode.github.io/husky/?utm_source=chatgpt.com)).

---

## Common Use Cases

- **Pre-commit linting**  
  Run ESLint or Stylelint on staged files before each commit to enforce code style ([How to Use Husky and Git Hooks to Automate Actions - GitKraken](https://www.gitkraken.com/blog/husky-git-hooks?utm_source=chatgpt.com), [Automating Code Quality: Git Hooks, Husky, and Lint-Staged for ...](https://dev.to/hkp22/automating-code-quality-git-hooks-husky-and-lint-staged-for-streamlined-linting-formatting-5ep4?utm_source=chatgpt.com)).

- **Pre-push testing**  
  Execute unit or integration tests (`npm test`) before pushing code, preventing broken builds from reaching remote branches ([How to Use Husky and Git Hooks to Automate Actions - GitKraken](https://www.gitkraken.com/blog/husky-git-hooks?utm_source=chatgpt.com), [Automating Code Quality: Git Hooks, Husky, and Lint-Staged for ...](https://dev.to/hkp22/automating-code-quality-git-hooks-husky-and-lint-staged-for-streamlined-linting-formatting-5ep4?utm_source=chatgpt.com)).

- **Commit-message validation**  
  Enforce Conventional Commits or other message formats via a `commit-msg` hook to maintain consistent changelogs ([How to Use Husky and Git Hooks to Automate Actions - GitKraken](https://www.gitkraken.com/blog/husky-git-hooks?utm_source=chatgpt.com)).

- **Sensitive-data checks**  
  Block commits containing AP keys or debugging code by running custom scripts on `pre-commit` ([How to Add Commit Hooks to Git with Husky to Automate Code Tasks](https://www.freecodecamp.org/news/how-to-add-commit-hooks-to-git-with-husky-to-automate-code-tasks/?utm_source=chatgpt.com)).

- **Automated changelog/version bump**  
  Trigger semantic-release or `npm version` on `post-commit` or `pre-push` to streamline releases ([Creating Git Hooks Using Husky - Syntackle](https://syntackle.com/blog/creating-git-hooks-using-husky-y6LKpN/?utm_source=chatgpt.com)).

---

## Installation & Setup

Here’s how to get back to a working **pre-commit** hook now that both `husky install` and `husky add` are deprecated in v9+.

## 1. Initialize Husky Hooks  
Instead of `add`, use the new **init** flow:

1. Make sure Husky is installed as a dev-dependency:  
   ```bash
   npm install --save-dev husky
   ```  
    ([Husky - NPM](https://www.npmjs.com/package/husky?utm_source=chatgpt.com))

2. Add a **prepare** script in your `package.json` (replacing any old `postinstall`):  
   ```jsonc
   {
     "scripts": {
       "prepare": "husky"
     }
   }
   ```  
   This runs Husky after every install, setting up Git’s `core.hooksPath` ([How to migrate from husky 8 to 9 - remarkablemark](https://remarkablemark.org/blog/2024/02/04/how-to-migrate-from-husky-8-to-9/?utm_source=chatgpt.com)).

3. Run the init command:  
   ```bash
   npx husky init
   ```  
   That creates a `.husky/` folder and seeds a `pre-commit` hook that runs `npm test` by default ([Husky add command is deprecated? - node.js - Stack Overflow](https://stackoverflow.com/questions/78173983/husky-add-command-is-deprecated?utm_source=chatgpt.com), [Get started | Husky](https://typicode.github.io/husky/get-started.html?utm_source=chatgpt.com)).

---

## 2. Inspect & Customize `.husky/pre-commit`

After `npx husky init`, open **.husky/pre-commit**—it should look like:

```bash
#!/usr/bin/env sh
. "$(dirname "$0")/_/husky.sh"

npm test
```

You can add more commands (e.g., `npm run lint`) on new lines below `npm test` ([Why setting up .husky pre commit hooks are difficult? : r/node - Reddit](https://www.reddit.com/r/node/comments/1ev2h6u/why_setting_up_husky_pre_commit_hooks_are/?utm_source=chatgpt.com)).

---

## 3. Manually Creating Hooks (Alternative)

If you need a custom hook without `init`, you can create it yourself:

1. **Create** the file and make it executable:  
   ```bash
   touch .husky/pre-commit
   chmod +x .husky/pre-commit
   ```

2. **Populate** it with:

   ```bash
   #!/usr/bin/env sh
   . "$(dirname "$0")/_/husky.sh"

   npm test
   npm run lint
   ```

    ([Husky add command is deprecated? - node.js - Stack Overflow](https://stackoverflow.com/questions/78173983/husky-add-command-is-deprecated?utm_source=chatgpt.com))

---

## 4. Adding Other Hooks

For a **commit-msg** hook, skip `add` and instead:

```bash
echo "npx --no -- commitlint --edit \$1" > .husky/commit-msg
chmod +x .husky/commit-msg
```

That mirrors the SO recommendation for v9+ ([Husky add command is deprecated? - node.js - Stack Overflow](https://stackoverflow.com/questions/78173983/husky-add-command-is-deprecated?utm_source=chatgpt.com)).

---

## 5. Verify & Commit

- Run `npm install` to trigger `prepare` and ensure `.husky/` is populated ([node.js - Do we always have to run npx husky init after installing ...](https://stackoverflow.com/questions/78687395/do-we-always-have-to-run-npx-husky-init-after-installing-husky-to-get-the-hooks?utm_source=chatgpt.com)).  
- Stage and commit a file; you should see your `pre-commit` commands run automatically.  

---

## Key Benefits

- **Fast & Native**: Husky uses Git’s `core.hooksPath` for ~1 ms hook startup and works across macOS, Linux, Windows, and CI ([Husky - NPM](https://www.npmjs.com/package/husky?utm_source=chatgpt.com)).  
- **Versioned Hooks**: Committing `.husky/` shares hooks with every collaborator—no more local-only `.git/hooks/` scripts ([Husky - NPM](https://www.npmjs.com/package/husky?utm_source=chatgpt.com)).  
- **Flexibility**: You control your hook scripts directly (shell, Node, whatever you need) without extra dependencies ([How To | Husky](https://typicode.github.io/husky/how-to.html?utm_source=chatgpt.com)).

With this, you’ll have a fully working **pre-commit** hook under Husky v9+, no deprecated commands needed!

## 5. Configure lint-staged

In **package.json**, add:

```jsonc
{
  // …
  "lint-staged": {
    "*.{js,ts,svelte}": [
      "eslint --fix",
      "prettier --write"
    ]
  }
}
```

---

## 6. Verify

1. Make a change in a `.svelte` or `.ts` file that violates your ESLint/Prettier rules.  
2. `git add` that file.  
3. `git commit` ➞ Husky will invoke lint-staged, auto-fix where possible, and block the commit if there are errors.

---

That replaces the deprecated `npx husky install` with the current `npm exec husky install` workflow.

---

```markdown
---

## 🎯 Next Step: Continuous Integration (CI)

Now that you’ve wired up Husky to run `yarn test`, `yarn lint`, `yarn prettier --check .` and `yarn type-check` on every commit, the next logical step is to **codify that same pipeline in your remote CI** so every push and PR gets automatically validated—no “works on my machine” surprises.

---

### 1. Create a GitHub Actions Workflow

Add a file at `.github/workflows/ci.yml`:

```yaml
name: CI

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build-and-test:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        node-version: [18.x]
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Use Node.js ${{ matrix.node-version }}
        uses: actions/setup-node@v3
        with:
          node-version: ${{ matrix.node-version }}
          cache: 'yarn'

      - name: Install dependencies
        run: yarn install --frozen-lockfile

      - name: Run type checks
        run: yarn type-check

      - name: Run lint
        run: yarn lint

      - name: Check formatting
        run: yarn prettier --check .

      - name: Run unit & integration tests
        run: yarn test --coverage

      # Optional: run E2E tests if you’ve started writing Playwright specs
      - name: Run Playwright E2E tests
        uses: microsoft/playwright-github-action@v1
        with:
          runPlaywrightTests: true

      # Optional: upload coverage to Codecov (or another service)
      - name: Upload coverage
        uses: codecov/codecov-action@v3
        with:
          token: ${{ secrets.CODECOV_TOKEN }}
```

---

### 2. Add Badges to Your README

```markdown
[![CI](https://github.com/<you>/<repo>/actions/workflows/ci.yml/badge.svg)](https://github.com/<you>/<repo>/actions/workflows/ci.yml)
[![Coverage](https://codecov.io/gh/<you>/<repo>/branch/main/graph/badge.svg)](https://codecov.io/gh/<you>/<repo>)
```

---

### 3. Protect Your Main Branch

1. In GitHub → **Settings → Branches**  
2. Add a **branch protection rule** for `main`  
3. Require:  
   - Status checks (CI) to pass before merging  
   - A minimum coverage threshold (e.g. 80%) if using Codecov

---

### 4. Automate Dependency Updates

Enable **Dependabot** in your repo to stay on top of security patches:

- Create `.github/dependabot.yml` with:

  ```yaml
  version: 2
  updates:
    - package-ecosystem: "npm"
      directory: "/"
      schedule:
        interval: "daily"
  ```

---

## ✅ What You’ll Have

- **Local guardrails** via Husky (pre-commit)  
- **Remote enforcement** via GitHub Actions (push/PR)  
- **Visibility** with status badges  
- **Stable main** with branch protection  
- **Up-to-date deps** with Dependabot  

After this, every line of code you push is automatically linted, type-checked, formatted, tested, and reported—letting you concentrate on implementing your Match-3 game features with confidence!

---
```

## 2. GitHub Actions: CI Workflow

Create `.github/workflows/ci.yml`:

```yaml
name: CI

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  lint-and-test:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        node-version: [18.x]
    steps:
      - uses: actions/checkout@v3

      - name: Use Node.js ${{ matrix.node-version }}
        uses: actions/setup-node@v3
        with:
          node-version: ${{ matrix.node-version }}

      - name: Install dependencies
        run: npm ci

      - name: Run ESLint & Prettier check
        run: |
          npm run lint
          npm run format:check

      - name: Run unit & integration tests
        run: npm test

      - name: Run Playwright E2E tests
        uses: microsoft/playwright-github-action@v1
        with:
          runPlaywrightTests: true

      - name: Upload coverage to Codecov
        uses: codecov/codecov-action@v3
        with:
          token: ${{ secrets.CODECOV_TOKEN }}
```

- **`npm run lint`** calls ESLint.  
- **`npm run format:check`** ensures Prettier compliance.  
- **`npm test`** should run your Vitest suite (unit/integration).  
- The Playwright action spins up the browsers and runs your E2E scripts.  
- Finally, Codecov (or Coveralls) picks up your coverage report for badge metrics.

---

## 3. README Badges & Protection

In your `README.md`, add:

```markdown
[![Lint](https://github.com/<you>/<repo>/actions/workflows/ci.yml/badge.svg)](https://github.com/<you>/<repo>/actions/workflows/ci.yml)
[![Coverage](https://codecov.io/gh/<you>/<repo>/branch/main/graph/badge.svg)](https://codecov.io/gh/<you>/<repo>)
```

And in GitHub repo settings, **protect `main`** so that:
- CI passes are required before merge
- A minimum coverage threshold (e.g. 80%) is enforced

---

## 4. Dependency & Security Automation

- **Dependabot**: enable to auto-bump dependencies  
- **Secret scans**: ensure no API keys get committed  

---

### Summary

1. **Lint/Format** with ESLint + Prettier + Husky  
2. **CI Workflow** to run lint, Vitest, Playwright, coverage on every PR  
3. **Badges & Branch Protection** for visibility and stability  
4. **Automate** dependency updates with Dependabot  

With that in place, every push and PR will be automatically validated—and you can focus on building out your Match-3 game!

## Next Steps

1. **Initialize** your SvelteKit repo & install `vitest`, `@testing-library/svelte`, `playwright`.  
2. **Commit** your first “renders homepage” test—watch it fail and then pass.  
3. **Lay out** the grid component and jump into Phase 2.

Let me know if you’d like example test code snippets or CI config details!
