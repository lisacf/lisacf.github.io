# 🛠 Setting Up Your Editor for SvelteKit: A Beginner's Guide

When you're learning a new framework like **SvelteKit**, your choice of editor can make a **huge difference** in how smooth, fun, and efficient your experience is.

In this post, I'll show you:

- The best editor to start with
- Must-have extensions for SvelteKit development
- Bonus tips to make your setup even better!

---

## ✨ Best Editor for Learning SvelteKit

The best place to start is **Visual Studio Code (VS Code)**.

- Free
- Fast
- Huge extension marketplace
- Excellent Svelte, TypeScript, TailwindCSS, Storybook, and Vitest support
- Beginner-friendly but powerful enough to grow with you

🔗 Download it here: [https://code.visualstudio.com/](https://code.visualstudio.com/)

---

## 📦 Essential VS Code Extensions for SvelteKit

After installing VS Code, you'll want to add a few key extensions to supercharge your setup.

Here’s my **starter pack**:

| **Extension**                  | **What it does**                                          |
|:--------------------------------|:----------------------------------------------------------|
| **Svelte for VS Code**           | Syntax highlighting, error checking, auto-completion for `.svelte` files. |
| **TailwindCSS IntelliSense**     | Smart completions and color previews for Tailwind classes. |
| **Prettier - Code Formatter**    | Automatically formats your code cleanly on save. |
| **ESLint**                       | Highlights errors and enforces best coding practices. |
| **Storybook Snippets**            | Quick scaffolding for your Storybook stories. |
| **Vitest Extension** *(optional)*| Lets you run Vitest unit tests directly inside VS Code. |

🔎 You can install these from the **Extensions** tab (`Ctrl + Shift + X`) inside VS Code.

---

## 🛠 Recommended VS Code Settings for SvelteKit

To make your experience even smoother, I recommend tweaking your **VS Code settings** slightly.

Here’s a basic `settings.json` starter you can use:

```json
{
  "editor.formatOnSave": true,
  "editor.tabSize": 2,
  "files.autoSave": "onWindowChange",
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true,
    "source.organizeImports": true
  },
  "eslint.validate": ["javascript", "typescript", "svelte"],
  "tailwindCSS.includeLanguages": {
    "svelte": "html"
  },
  "prettier.enableDebugLogs": false,
  "svelte.plugin.typescript.enable": true
}
