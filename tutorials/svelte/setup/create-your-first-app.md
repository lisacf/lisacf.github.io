---
layout: default
title: "Create Your First Svelte App"
permalink: /tutorials/svelte/setup/create-your-first-app/
---

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
```
---
# Here is what you get
Open your project in your favorite editor or set up VSCode by following these instructions [Set up your Code Editor](/tutorials/svelte/editor_setup.md).

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

#  Run your my-sveltekit-tutorial app
```bash
yarn run dev --open
```
A window in your browser will open and you will see.  Or open a browser and navigate to localhost:5173

<img width="388" alt="Screenshot 2025-04-25 at 1 05 58 PM" src="https://github.com/user-attachments/assets/dc006bbe-debc-4402-b744-a9428518c9e3" />


# 🎯 What's Next?

I'm planning to:

- Build simple SvelteKit pages like `/counter`, `/mood-tracker`, and `/forms`
- Create reusable components and document them in Storybook
- Practice TypeScript inside `.svelte` files
- Explore Tailwind utility classes for fast, clean styling











