# 🔢 Counter Experiment — Learning Reactivity in SvelteKit

In this experiment, we build a simple **Counter** app to **see Svelte's reactivity in action**.

Reactivity is the core idea that **when your data changes, your UI updates automatically** — no need to manually tell the browser what to change.

This is the perfect first project to build after learning about reactive apps!

---

## 🛠️ Project Setup

We created a new page inside our SvelteKit app under:

```
/src/routes/experiment/counter/+page.svelte
```

This made the page available at:

```
/experiment/counter
```

We wrapped our entire app layout in a responsive `<main>` tag so that the page content stays centered and doesn't look squashed.  
(You can read more about the layout wrapper in the Concepts section.)

---

## 🧱 The Code

Here’s the full code for the counter:

```svelte
<!--
Counter Experiment
Built to demonstrate basic Svelte reactivity.
Increments and decrements a number and updates the UI automatically.
-->

<script lang="ts">
	let count = 0;
</script>

<h1 class="text-2xl font-bold mb-4">Counter Experiment</h1>

<p class="mb-4">Current count: {count}</p>

<div class="flex gap-4">
	<button class="px-4 py-2 bg-blue-500 text-white rounded" on:click={() => count += 1}>
		➕ Increment
	</button>
	<button class="px-4 py-2 bg-red-500 text-white rounded" on:click={() => count -= 1}>
		➖ Decrement
	</button>
</div>
```

✅ When the user clicks **Increment**, the `count` increases by 1.  
✅ When they click **Decrement**, the `count` decreases by 1.  
✅ The text on the page updates automatically — thanks to Svelte's reactivity!

---

## 🎯 What We Learned

- **Reactivity**: Updating the `count` variable automatically re-renders the page.
- **Event Handling**: The `on:click` directive lets us respond to user actions easily.
- **TailwindCSS**: We used Tailwind utility classes to quickly style the buttons and layout.
- **Layout Wrapping**: Using a `max-w-3xl mx-auto p-4` wrapper in our layout keeps all our pages readable and responsive.

---

## ✨ Things You Could Try Next

- Add a **Reset** button to set `count = 0`.
- Add a **maximum or minimum limit** so the counter can't go beyond certain numbers.
- Display a **special message** when `count` reaches a milestone (like 10 or -10).
- Change the **color of the number** when it goes negative!

---

## 🛤️ What's Coming Up?

Next, we'll build a **Mood Tracker Experiment** —  
which will show how to collect and display more complex reactive data!

Stay tuned!
