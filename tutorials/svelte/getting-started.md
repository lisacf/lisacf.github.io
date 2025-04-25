---
layout: default
title: "Getting Started with Svelte"
permalink: /tutorials/svelte/getting-started/
---

# Getting Started with Svelte

Welcome to the world of Svelte! This guide walks you through the basics so you can build your first Svelte component in minutes.

## What Is Svelte?

Svelte is a modern JavaScript framework for building fast, reactive user interfaces. Unlike traditional frameworks, Svelte shifts work from the browser to a compile step, producing highly optimized vanilla JavaScript.

- **Zero runtime framework**: No bulky framework code shipped to the browser.
- **Reactivity baked in**: Simple assignments trigger updates.
- **Component-based**: Build UI with encapsulated, reusable components.

## Prerequisites

- Node.js (>= 14.x) and npm installed
- A terminal/command prompt
- A code editor (e.g., VS Code)

## Create a New Svelte Project

1. **Open your terminal** and run:
   ```bash
   npm create svelte@latest my-svelte-app
   ```
2. **Navigate into the project**:
   ```bash
   cd my-svelte-app
   ```
3. **Install dependencies**:
   ```bash
   npm install
   ```
4. **Start the development server**:
   ```bash
   npm run dev -- --open
   ```
   This will open `http://localhost:5173` in your browser.

## Your First Component

Open `src/routes/+page.svelte` (or `src/App.svelte`) and replace its content with:

```svelte
<script>
  let name = 'world';
</script>

<main>
  <h1>Hello {name}!</h1>
  <input bind:value={name} placeholder="Enter your name" />
</main>

<style>
  main {
    font-family: system-ui, sans-serif;
    padding: 2rem;
  }
  input {
    margin-top: 1rem;
    padding: 0.5rem;
    font-size: 1rem;
  }
</style>
```

- Type in the input box and watch the heading update in real time.

## How Reactivity Works

Svelte tracks assignments to variables. When you do `name = 'Svelte'`, it automatically updates the DOM.

```svelte
<script>
  let count = 0;
  function increment() {
    count += 1;
  }
</script>

<button on:click={increment}>
  Clicked {count} {count === 1 ? 'time' : 'times'}
</button>
```

## Next Steps

- Explore the [official tutorial](https://svelte.dev/tutorial)
- Learn about component props and events
- Dive into routing with SvelteKit

Enjoy building with Svelte! 🎉

