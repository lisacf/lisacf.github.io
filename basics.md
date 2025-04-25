Svelte is a **Declarative** framework for web apps.

Other declarative frameworks include 
- React (for web apps)
- SwiftUI (for iOS apps)
- Flutter (for cross-platform apps)

Instead of manually updating the UI when things change, you just update the state, and the framework automatically rebuilds the correct UI based on that state.

Setting up SvelteKit for learning

 % npx sv create my-sveltekit-tutorial

 Need to install the following packages:
sv@0.8.2
Ok to proceed? (y) y

┌  Welcome to the Svelte CLI! (v0.8.2)
│
◆  Which template would you like?
│  ● SvelteKit minimal (barebones scaffolding for your new app)
│  ○ SvelteKit demo
│  ○ Svelte library

| **Option**               | **Meaning**                                                  | **Should you pick it?**                    |
|:--------------------------|:-------------------------------------------------------------|:-------------------------------------------|
| **SvelteKit Minimal**      | A **blank slate** — just the basics to start building an app. No demo code, no extra pages. | ✅ **Yes! This is perfect** for your tutorial app — clean and ready to learn. |
| **SvelteKit Demo**         | Comes with a **lot of sample code** — pages, API routes, examples of how stuff works. | 🚫 **No, not for your case** — it’s more useful if you want to *study* an example, but it gets cluttered fast. |
| **SvelteKit Library**      | Creates a **reusable component library** (e.g., if you wanted to publish an npm package). | 🚫 **No, not what you need** for building an app. |

🧠 So:
👉 Pick:  SvelteKit Minimal (barebones scaffolding for your new app)
This way, you control every page you add, every component, every piece of state — exactly what you want for practicing SvelteKit concepts cleanly.

◆  Add type checking with TypeScript?
│  ● Yes, using TypeScript syntax
│  ○ Yes, using JavaScript with JSDoc comments
│  ○ No
└

| **Prompt**                               | **Options**                                         | **Which to pick?**                                  |
|:-----------------------------------------|:----------------------------------------------------|:----------------------------------------------------|
| **Add type checking with TypeScript?**   | ● Yes, using TypeScript syntax                      | ✅ **Yes! Pick this.** You want real TypeScript syntax for best learning and full typing power. |
|                                          | ○ Yes, using JavaScript with JSDoc comments          | 🚫 No, you want real `.ts` and `.svelte` files, not JSDoc tricks. |
|                                          | ○ No                                                | 🚫 Definitely no — you want TypeScript for your future word game apps. |

---

### 🧠 Quick Explanation:
- **Yes, using TypeScript syntax** → Creates `.ts` and `.svelte` files where you can write real TypeScript. Best for modern apps and learning proper typing.
- **Yes, using JSDoc comments** → Keeps `.js` files, but you add special comments to hint types. It's messier and not ideal for a clean project.
- **No** → Skips TypeScript entirely and just uses JavaScript. Not recommended if you want the extra safety and power of TypeScript, especially for future game development.

 What would you like to add to your project? (use arrow keys / space bar)
│  ◻ prettier (formatter - https://prettier.io)
│  ◻ eslint
│  ◻ vitest
│  ◻ playwright
│  ◻ tailwindcss
│  ◻ sveltekit-adapter
│  ◻ drizzle
│  ◻ lucia
│  ◻ mdsvex
│  ◻ paraglide
│  ◻ storybook

| **Option**             | **What it is**                                                 | **Should you include it?**                          |
|:------------------------|:---------------------------------------------------------------|:----------------------------------------------------|
| `prettier`             | Code formatter for consistent style                            | ✅ **Yes** — Keeps your code clean and consistent    |
| `eslint`               | Linter to catch code issues                                     | ✅ Optional — Helpful if you want to learn clean coding practices |
| `vitest`               | Unit testing framework for Svelte apps                         | 🟡 Optional — Good for later, but not needed now     |
| `playwright`           | End-to-end testing tool (browser automation)                   | 🟡 Optional — Overkill for a tutorial app            |
| `tailwindcss`          | Utility-first CSS framework                                    | ✅ Optional — Nice for styling if you want to try it |
| `sveltekit-adapter`    | Lets you deploy your app (e.g. static, Node, Vercel)           | ✅ **Yes** — Needed to deploy, pick the one you want later |
| `drizzle`              | Type-safe database toolkit                                     | ❌ No — Not needed unless you’re using a database    |
| `lucia`                | Auth library for SvelteKit                                     | ❌ No — You don’t need login/auth for this project   |
| `mdsvex`               | Use Markdown in `.svelte` files                                | ❌ Not needed now — Cool for blogs, not your goal    |
| `paraglide`            | Internationalization (i18n) support                            | ❌ No — Not needed unless you're translating         |
| `storybook`            | UI component explorer                                          | 🟡 Optional — Useful for reusable UI, but not urgent |

◆  tailwindcss: Which plugins would you like to add?
│  ◻ typography (@tailwindcss/typography)
│  ◻ forms

| **Plugin**                          | **What it does**                                       | **Should you include it?**                      |
|:------------------------------------|:------------------------------------------------------|:------------------------------------------------|
| `typography` (@tailwindcss/typography) | Beautiful default styles for text content (headings, paragraphs, articles) | ✅ **Yes** — Super useful even in simple apps |
| `forms`                             | Better base styles for `<input>`, `<textarea>`, `<button>`, etc. | ✅ **Yes** — Especially helpful for forms in your tutorial |

### 🧠 Quick Explanation:

- **Typography plugin**:
  - Makes plain text (`<p>`, `<h1>`, etc.) look clean and elegant.
  - Especially great if you’ll show paragraphs, headers, and clues (for word games later!).

- **Forms plugin**:
  - Fixes ugly default browser form styles.
  - Makes things like text inputs, dropdowns, and buttons **much nicer** instantly.
  - You’ll probably build small forms in your tutorial app (and definitely in your word games later for theme selection, player names, etc).

◆  sveltekit-adapter: Which SvelteKit adapter would you like to use?
│  ● auto (@sveltejs/adapter-auto)
│  ○ node
│  ○ static
│  ○ vercel
│  ○ cloudflare
│  ○ netlify

| **Adapter**               | **What it does**                                                                 | **Should you pick it?**                                       |
|:--------------------------|:----------------------------------------------------------------------------------|:--------------------------------------------------------------|
| `auto`                   | Tries to detect the best adapter automatically for your environment               | ✅ **Yes!** Easiest choice for learning and local development |
| `node`                   | Targets a Node.js server (Express-style)                                         | 🟡 Optional — Only if you’re deploying to your own Node server |
| `static`                 | Exports a fully static site (like a JAMstack site)                                | 🟡 Good later if you want to host on GitHub Pages or Netlify static |
| `vercel`                 | For deploying to Vercel                                                          | ✅ Use this only if you know you’re deploying to Vercel        |
| `cloudflare`             | Optimized for Cloudflare Workers                                                 | ❌ No — niche use unless you’re already using Cloudflare Workers |
| `netlify`                | For deploying to Netlify                                                         | ✅ Use this only if you know you’re deploying to Netlify       |

### 🧠 Quick Explanation:

- **`auto`**:
  - Best for getting started — it picks the right adapter depending on where you run or deploy.
  - Perfect for tutorial apps and local development.

- **`node`**:
  - Use if you're deploying to a custom Node.js server.
  - Gives you full backend control, but you likely don’t need this now.

- **`static`**:
  - Great for sites that don’t need server logic (just HTML/CSS/JS).
  - Could be a good fit later for your word game if you want to host it on GitHub Pages or Netlify static hosting.

- **`vercel`, `netlify`, `cloudflare`**:
  - Use one of these **only if you’ve already decided where to deploy**.
  - They provide optimized builds for those platforms.
    
👉 **Pick**: `auto (@sveltejs/adapter-auto)`

## 🧩 Storybook Prompt: "What do you want to use Storybook for?"

| **Option**                           | **What it does**                                                         | **Should you include it?**                       |
|:------------------------------------|:-------------------------------------------------------------------------|:------------------------------------------------|
| `Documentation`                     | Enables MDX-based stories, auto-generates props & usage docs             | ✅ **Yes!** Great for seeing and sharing how your components work |
| `Testing`                           | Adds support for browser-based interaction and snapshot tests            | ✅ **Yes!** Lets you test how components behave without writing full apps |

### 🧠 Quick Explanation:

- **Documentation**:
  - Generates beautiful docs for your components automatically.
  - Uses MDX (Markdown + JSX-style syntax) to let you write examples, guides, and stories.
  - Super helpful for future-proofing your components and sharing them with collaborators (or your future self!).

- **Testing**:
  - Lets you simulate clicks, inputs, and behavior directly in Storybook.
  - You can run interaction tests in the browser and even automate them later.
  - Great for ensuring your components behave correctly before wiring them into a full app.

👉 **Select both**: `Documentation` and `Testing`


Once you select this the storybook setup will begin.  Once it is done you will see.
╭ 🎉 All done! ─────────────────────────────────────────────────────────────────────────────────────╮
│                                                                                                   │
│   The Storybook Test addon is now configured and you're ready to run your tests!                  │
│                                                                                                   │
│   Here are a couple of tips to get you started:                                                   │
│   • You can run tests with npx vitest --project=storybook                                         │
│   • When using the Vitest extension in your editor, all of your stories will be shown as tests!   │
│                                                                                                   │
│   Check the documentation for more information about its features and options at:                 │
│   https://storybook.js.org/docs/writing-tests/test-addon                                          │
│                                                                                                   │
╰───────────────────────────────────────────────────────────────────────────────────────────────────╯

╭──────────────────────────────────────────────────────────────────────────────╮
│                                                                              │
│   Storybook was successfully installed in your project! 🎉                   │
│   Additional features: Documentation, Testing                                │
│                                                                              │
│   To run Storybook manually, run yarn storybook. CTRL+C to stop.             │
│                                                                              │
│   Wanna know more about Storybook? Check out https://storybook.js.org/       │
│   Having trouble or want to chat? Join us at https://discord.gg/storybook/   │
│                                                                              │
╰──────────────────────────────────────────────────────────────────────────────╯
│
◆  Successfully setup add-ons
│
◆  Which package manager do you want to install dependencies with?
│  ○ None
│  ○ npm
│  ● yarn
│  ○ pnpm
│  ○ bun
│  ○ deno

| **Option**         | **What it is**                                              | **Should you pick it?**                                |
|:-------------------|:------------------------------------------------------------|:-------------------------------------------------------|
| `None`              | You’ll install everything manually later                   | 🚫 No — you want it automated for a fast start          |
| `npm`               | Node's default package manager                             | ✅ Solid, stable, widely used. Good default choice.     |
| `yarn`              | Faster alternative to npm, some nicer features (cache, etc.)| ✅ Good choice! You already have it selected — it's great for projects. |
| `pnpm`              | Super fast and disk-space efficient package manager         | 🟡 Advanced — great later, but Yarn is fine for now     |
| `bun`               | Very new ultra-fast package manager/runtime                | ❌ Too experimental for your tutorial app              |
| `deno`              | Alternative to Node.js itself                              | ❌ Not needed — you're using Node/SvelteKit, not Deno  |

### 🧠 Quick Explanation:

- **None**:
  - Skips automatic install — not recommended unless you want to manually manage everything.

- **npm**:
  - The classic. Works everywhere. Solid if you want the most compatibility.

- **yarn**:
  - Faster installs, better caching.
  - Many developers prefer it for medium/large projects.
  - **You're already selecting Yarn — that's a great choice!**

- **pnpm**:
  - Amazing for huge monorepos and massive apps.
  - Overkill for a simple tutorial app, but worth learning later.

- **bun**:
  - Super new and still evolving. Best to wait for more maturity.

- **deno**:
  - A different JavaScript runtime entirely — not relevant to a SvelteKit project.

👉 **Stick with your selection: yarn**
◇  Project next steps ─────────────────────────────────────────────────────╮
│                                                                          │
│  1: cd my-sveltekit-tutorial                                             │
│  2: git init && git add -A && git commit -m "Initial commit" (optional)  │
│  3: yarn run dev --open                                                  │
│                                                                          │
│  To close the dev server, hit Ctrl-C                                     │
│                                                                          │
│  Stuck? Visit us at https://svelte.dev/chat                              │
│                                                                          │
├──────────────────────────────────────────────────────────────────────────╯
│
└  You're all set!


# 🚀 Setting Up My SvelteKit Tutorial App (with TailwindCSS + Vitest + Storybook)

I decided to build a **SvelteKit tutorial app** to learn the core concepts of SvelteKit, TailwindCSS, Storybook, and TypeScript — and to prepare for my future word game apps.

Here’s how the setup process went!

---

## 🛠 Project Creation

I used the official SvelteKit scaffolding command:

```bash
npx sv create my-sveltekit-tutorial
```

---

## 📋 Choices During Setup

### Template Selection

| **Option**             | **Meaning**                                               | **Picked?**                          |
|:------------------------|:-----------------------------------------------------------|:-------------------------------------|
| SvelteKit Minimal       | Barebones project, no extra example code                   | ✅ **Yes, perfect for a clean start** |
| SvelteKit Demo          | Includes example pages and code                           | 🚫 No                               |
| SvelteKit Library       | For building reusable component libraries                  | 🚫 No                               |

---

### Type Checking with TypeScript

| **Option**                         | **Meaning**                                             | **Picked?**                      |
|:------------------------------------|:--------------------------------------------------------|:---------------------------------|
| Yes, using TypeScript syntax        | Full `.ts` and `.svelte` files with real TypeScript      | ✅ **Yes!** Best for learning     |
| Yes, using JSDoc comments            | JavaScript with type hints via comments                 | 🚫 No                            |
| No                                  | Plain JavaScript without typing                         | 🚫 No                            |

**Quick Explanation:**

- Using real TypeScript syntax gives stronger type checking, better developer tools, and prepares me for professional projects.

---

### Additional Tools

| **Tool**          | **What it is**                                    | **Picked?**                      |
|:------------------|:--------------------------------------------------|:---------------------------------|
| Prettier          | Code formatter                                    | ✅ Yes                           |
| ESLint            | Linter for finding bugs and enforcing best practices | ✅ Yes                          |
| TailwindCSS       | Utility-first CSS framework                      | ✅ Yes                           |
| SvelteKit Adapter | Needed for deployment                             | ✅ Yes                           |
| Vitest            | Unit testing framework                            | ✅ Yes I am a big believer in testing  |
| Playwright        | End-to-end testing                                | 🚫 No (not needed for now)       |
| Drizzle           | Database toolkit                                  | 🚫 No                            |
| Lucia             | Authentication toolkit                            | 🚫 No                            |
| Mdsvex            | Markdown inside Svelte                            | 🚫 No                            |
| Paraglide         | i18n (internationalization)                       | 🚫 No                            |
| Storybook         | UI component explorer and documentation/testing   | ✅ **Yes!** I added this to learn more about reusable UI components |

---

### TailwindCSS Plugins

| **Plugin**           | **What it does**                                         | **Picked?**                      |
|:---------------------|:----------------------------------------------------------|:---------------------------------|
| Typography           | Beautiful base styles for text                           | ✅ Yes                           |
| Forms                | Improved default styles for form inputs, buttons, etc.    | ✅ Yes                           |

**Quick Explanation:**

- These plugins make forms and text much cleaner without custom CSS.
- Perfect for tutorial apps and future word-based games.

---

### SvelteKit Adapter Selection

| **Adapter**          | **What it does**                                          | **Picked?**                      |
|:---------------------|:-----------------------------------------------------------|:---------------------------------|
| Auto                 | Automatically picks the best deployment adapter           | ✅ Yes                           |
| Node, Static, Vercel, Cloudflare, Netlify | Specific to deployment platforms | 🚫 No (will choose later if needed) |

---

### Storybook Features

| **Option**           | **What it does**                                            | **Picked?**                      |
|:---------------------|:------------------------------------------------------------|:---------------------------------|
| Documentation        | Auto-generates component docs and examples (MDX)             | ✅ Yes                           |
| Testing              | Enables fast browser-based component testing                | ✅ Yes                           |

**Quick Explanation:**

- Storybook will help me visualize, document, and test components individually.
- A fantastic tool for clean, modular development.

---

### Package Manager

| **Package Manager**  | **Why**                                                    | **Picked?**                      |
|:---------------------|:-----------------------------------------------------------|:---------------------------------|
| Yarn                 | Faster installs, efficient dependency handling              | ✅ Yes                           |
| npm, pnpm, bun, deno  | Other options not selected                                 | 🚫 No                            |

---

## 📂 Project Next Steps

After setup completed, the program showed the next steps:

```bash
1. cd my-sveltekit-tutorial
2. git init && git add -A && git commit -m "Initial commit" (optional)
3. yarn run dev --open
```

- To close the dev server: Press `Ctrl+C`
- For help: Visit [https://svelte.dev/chat](https://svelte.dev/chat)

✅ Setup complete! Ready to start coding.

---

---
# Creating a github repo for your projects
## 🔥 Quick Visual Summary:

| Step | What you do                             | Tools  |
|:-----|:----------------------------------------|:-------|
| 1    | Create project locally                  | Terminal |
| 2    | `git init`, `git add`, `git commit`      | Terminal |
| 3    | Create empty repo on GitHub              | Web browser |
| 4    | `git remote add origin`, `git push`      | Terminal |

---

### 🧠 Why this order?

- You control everything **locally** first — no GitHub mess-ups.
- Your **local history** (the clean initial commit) is preserved exactly.
- You link the GitHub repo **only after** you know your local project is ready.
- No duplicate `.git` folders, no weird "merge" prompts from a pre-filled repo.

---

### 📋 Tip: What GitHub will show you

After you create the repo, it shows a helpful guide like:

```bash
echo "# my-sveltekit-tutorial" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
git push -u origin main

Perfect — this gives an extremely clear **full project tree**! 🔥  
(And it shows why you'd definitely want to **collapse or hide `node_modules/`** in your blog post for clarity.)

---
# Here is what you get
Open your project in your favorite editor (VS Code, s
## 📁 Project Structure (Clean Overview)

Here’s the main structure of my SvelteKit tutorial project:

```
.
├── README.md
├── eslint.config.js
├── package.json
├── svelte.config.js
├── tsconfig.json
├── vite.config.ts
├── vitest-setup-client.ts
├── vitest.shims.d.ts
├── src/
│   ├── app.css
│   ├── app.d.ts
│   ├── app.html
│   ├── demo.spec.ts
│   ├── lib/
│   ├── routes/
│   │   ├── +layout.svelte
│   │   ├── +page.svelte
│   │   └── page.svelte.test.ts
│   └── stories/
├── static/
│   └── favicon.png
```

---

### 🔥 Quick Notes:

- `src/` — Your app’s source code: routes, components, styles, tests, and Storybook stories.
- `static/` — Public assets (like your `favicon.png`) served directly at the root URL.
- `svelte.config.js`, `vite.config.ts`, `tsconfig.json` — Configuration files for SvelteKit, Vite bundler, and TypeScript respectively.
- `vitest-setup-client.ts`, `vitest.shims.d.ts` — Setup files for running Vitest tests smoothly.
- `eslint.config.js` — Defines linting rules for code quality and consistency.
- `package.json` — Lists project dependencies, scripts, and project metadata.

---

## 📦 What About `node_modules/`?

The `node_modules/` folder contains all third-party packages needed for the app (SvelteKit itself, Storybook, Vitest, TailwindCSS, etc.).  
It's automatically managed by your package manager (`yarn` in this case) and **should not** be modified manually.

It’s massive (hundreds of folders!) — but it's not something you work in directly.

---
```






# 🎯 What's Next?

I'm planning to:

- Build simple SvelteKit pages like `/counter`, `/mood-tracker`, and `/forms`
- Create reusable components and document them in Storybook
- Practice TypeScript inside `.svelte` files
- Explore Tailwind utility classes for fast, clean styling
- Later — start prototyping features for my **SPELL** word game!

---

Stay tuned for my next blog post:  
📚 **"First Page, First Story: Making a Mood Tracker in SvelteKit + Storybook!"**

```

---










