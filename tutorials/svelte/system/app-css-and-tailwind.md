---
layout: default
title: "app.css in TailwindCSS Projects"
permalink: /tutorials/svelte/system/app-css-and-tailwind/
---
# 🎨 Understanding `app.css` in TailwindCSS Projects

When I first started building my SvelteKit tutorial app, I noticed that there was already an `app.css` file set up for me.

At first, I wondered:
> **"What is this file doing, and how does it relate to TailwindCSS?"**

Here's what I learned — and it made everything about styling much clearer!

---

## 📂 What is `app.css` For?

In a SvelteKit + TailwindCSS project:

- `app.css` is the **main stylesheet** that loads Tailwind's styles into your app.
- It **sets up** the base, components, utilities, and any **extra plugins** you use (like typography or form styles).
- It's also where you can add **any global custom CSS** you want — if needed.

**Important!**  
> 🛠 `app.css` gets **imported inside the project’s layout file** (`+layout.svelte`), so that it automatically affects all your pages.  
If you missed it, check out my earlier post about layouts here: [Understanding Layouts in SvelteKit](/understanding-layout)

---

## 🧠 What My `app.css` Contains

Here’s the default content:

```css
@import 'tailwindcss';
@plugin '@tailwindcss/forms';
@plugin '@tailwindcss/typography';
```

### 🔍 What each line does:

| Line | Meaning |
|:-----|:--------|
| `@import 'tailwindcss';` | Pulls in **all** of Tailwind’s base styles, components, and utilities. |
| `@plugin '@tailwindcss/forms';` | Adds prettier, more accessible default styles for form elements like `<input>`, `<textarea>`, etc. |
| `@plugin '@tailwindcss/typography';` | Adds beautiful styling for rich text (perfect for blog posts, articles, etc.). |

✅ This setup **automatically prepares everything** I need to start using Tailwind classes inside my `.svelte` files.

---

## 🛠 How Tailwind Works with `app.css`

Once `app.css` is imported through the layout, TailwindCSS lets me:

- Use utility classes like `bg-gray-100`, `text-center`, `rounded-xl` directly in my components.
- Style my app **without writing a lot of raw CSS manually**.
- Keep my global styles clean and minimal.

---

## 🎨 Example: Using Tailwind Inside a Svelte Component

Because `app.css` loaded Tailwind, I can now style something like this:

```svelte
<button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
  Click Me
</button>
```

✅ No extra CSS needed.  
✅ Everything stays inside my Svelte files.

---

## 🧹 Can I Still Add Custom Global CSS?

Yes!

If I ever need to, I can simply add more rules to `app.css` **after** the Tailwind imports.

Example:

```css
@import 'tailwindcss';
@plugin '@tailwindcss/forms';
@plugin '@tailwindcss/typography';

/* Custom global styles */
body {
  @apply bg-gray-50 text-gray-900;
}
```

✅ You can even use Tailwind’s `@apply` directive inside your custom CSS for consistency.

---

## 💬 Final Thoughts

- `app.css` acts like the **bridge** between Tailwind and my project.
- I **write my styles inside component markup** using Tailwind classes.
- I **only add global CSS** to `app.css` if I have a special reason (like setting a background or font globally).

Understanding this setup made me feel way more confident using Tailwind in my SvelteKit app —  
and it keeps my styling **organized**, **scalable**, and **easy to manage**. 🚀

---

## 🌟 Coming Next

Now that I understand how Tailwind hooks into my project, I'm ready to start **styling my experiment homepage into a beautiful responsive grid** — and learning more about utility-first CSS magic!

Stay tuned!
