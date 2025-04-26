## 🧿 What are *Runes* in Svelte?

When you start learning Svelte (especially SvelteKit with newer versions), you might hear about something called "**Runes**."  
At first, it sounds mysterious — but don't worry!  
Runes are just a **new way of writing reactive, flexible Svelte code**.

Instead of "magic behavior" happening behind the scenes, Runes make everything **more explicit** — you can **see** what’s happening.

Think of it like this:
> ✨ *Runes are like spells you cast in your code to control how things react, render, and connect.*

---

## 🧠 Why Did Svelte Create Runes?

Before Runes, Svelte did a lot of things automatically:
- `$:` was used for reactive variables
- `<slot />` automatically pulled children into layouts
- Stores had some hidden behaviors
- Reactivity could sometimes feel "automatic but confusing"

This was easy to *use* at first but **harder to scale** or **customize** for bigger apps.

**Runes were created to:**
- Make reactivity more **predictable and visible**
- Give developers more **power and flexibility**
- Let the Svelte compiler do even better optimizations
- Set up the future of Svelte for huge apps (and even server code!)

In short:  
👉 **Runes make Svelte more powerful, while keeping it simple to learn.**

---

## 📜 A Tiny Example

**Before Runes (Classic Svelte):**

```svelte
<script>
	let count = 0;

	function increment() {
		count += 1;
	}
</script>

<button on:click={increment}>
	Count: {count}
</button>
```

Svelte automatically figured out that updating `count` should update the button.  
Cool — but kind of hidden.

---

**With Runes (New Style):**

```svelte
<script>
	let count = 0;

	function increment() {
		count += 1;
	}
</script>

<button on:click={increment}>
	Count: {count}
</button>
```

💬 **WAIT — this still looks the same!**  
That’s because Runes **aren't forced** — you can still write simple stuff simply.  
But when you want **full control** — especially in more advanced layouts or logic — Runes give you special helpers.

For example:

```svelte
<script>
	import { $state } from 'svelte';

	const count = $state(0);

	function increment() {
		count.set(count() + 1);
	}
</script>

<button on:click={increment}>
	Count: {count()}
</button>
```

Here, `count()` is a reactive value you **control explicitly** using the `$state` rune.  
No more guessing when something is reactive!

---

## 🏗️ How Runes Affect Layouts (and Slots)

In "classic" Svelte layouts, you could just write:

```svelte
<slot />
```

and it would magically pull in the page content.

**With Runes,** you do it more manually:

```svelte
<script lang="ts">
	let { children } = $props();
</script>

{@render children()}
```

- `$props()` grabs the properties coming into the component
- `{@render}` actually inserts the child content
- It's **explicit**: you choose exactly *where* and *when* child content shows up

This gives you way more control — for example, you could show different layouts for different conditions!

---

## ✨ Summary

| Classic Svelte | Svelte with Runes |
|:--------------|:------------------|
| Magic behavior | Explicit control |
| Easy but sometimes hidden | Clear and predictable |
| Great for small apps | Great for big apps and scaling |

**Runes are optional for simple cases**, but super powerful when you want to build bigger, smarter apps.

---

## 🛤️ What's Next?

Now that we understand Runes at a high level,  
we'll see them in action when we build our Layout, Navigation, and Experiments pages in SvelteKit!

---

# 🧩 Final Touch

You might want to add a **small note at the top** of the post, something like:

> **Note:** If you're following this tutorial and see `$props()`, `{@render}`, or special functions like `$state`, those are *Runes!* Don’t worry — we’ll explain everything you need step-by-step.

---
