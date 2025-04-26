# 📚 Concept: Understanding Props in Svelte

Props are how we pass information into a Svelte component to make it flexible and reusable.

---

# 💡 Beginner Tip: What is a Prop?

A **prop** (short for property) is like a note you pass into a component telling it what it should display or how it should behave.

> 📚 [See deeper explanation: Understanding Components, Props, Slots, and Children](/concepts/components-props-slots-etc.md)

---

# 🛠 Experiment: Build a Button That Accepts a Label

Let's create a `PlaygroundButton.svelte` component that accepts a `label` prop and displays it inside a button.

```svelte
<script>
  export let label;
</script>

<button>{label}</button>
```

---

# 🧪 Tiny Challenge: Try a Button Without Passing a Label

- Use your `PlaygroundButton` without passing a `label` prop.
- Then try passing different labels.
- What happens? Why?

✅ Try both:

```svelte
<PlaygroundButton /> <!-- No label -->
<PlaygroundButton label="Submit" />
```

---

# 💡 Beginner Tip: Giving Props a Default Value

If you want the button to still work nicely without a label passed in,  
you can give it a default:

```svelte
<script>
  export let label = "Default Button Text";
</script>
```

✅ Now the button will show "Default Button Text" if no label is passed!

---

# 🖼 Visual Aid: How Prop Passing Works

```plaintext
Parent Page
   ⬇️ (passes prop)
<Button label="Click me!" />

Button.svelte
   ⬇️ (receives prop)
Displays {label}
```

---

# 🚀 Project Build: Prop Playground Page

Let's add a new route `/experiment/prop-passing` to try out multiple buttons  
with different labels!

✅ This builds our project and gives us a live space to play with props!

---

# 🎯 Final Summary

| Concept | What You Learned |
|:--------|:-----------------|
| 📚 Props | Passing data into components |
| 🛠 Experiment | Building a prop-accepting button |
| 🧪 Tiny Challenge | Testing default values |
| 🖼 Visual Aid | Seeing prop flow |
| 🚀 Project Build | Adding an experiment page |

---
