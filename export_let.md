# 🎯 Beginner's Guide to `export let` in Svelte

As I build my SvelteKit tutorial app, I keep seeing code like this:

```svelte
<script>
  export let label;
</script>
```

At first, I wondered:  
> "Is this injecting something into the page? How does it really work?"

Here’s the **simple truth**:

---

## 📦 What Does `export let` Actually Do?

When you write `export let name;` at the top of a Svelte component:

✅ You are **creating a prop** that **the parent component** can **pass a value into**.

✅ It does **NOT automatically inject anything** by itself.

✅ It **opens a door** for values to come **into the component** when it’s used.

---

## 📚 Step-by-Step Flow

| Step | Action |
|:-----|:-------|
| 1 | In the child component, you write `export let label;`. |
| 2 | In the parent component, you use `<Button label="Click me!" />`. |
| 3 | Svelte passes the value `"Click me!"` into the child component. |
| 4 | Inside the child, `{label}` is now available to use anywhere. |
| 5 | The component renders or uses the value however it needs. |

---

## 🛠 Tiny Playground Example

Let’s create a simple Button component you can try right now!

```svelte
<!-- src/lib/components/PlaygroundButton.svelte -->

<script>
  export let label;
</script>

<button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
  {label}
</button>
```

✅ This Button **accepts a prop** called `label`.

---

Now let's use it inside a page!

```svelte
<!-- src/routes/experiment/prop-passing/+page.svelte -->

<script>
  import PlaygroundButton from '$lib/components/PlaygroundButton.svelte';
</script>

<h1 class="text-2xl font-bold mb-6">🧪 Prop Passing Playground</h1>

<PlaygroundButton />
<PlaygroundButton label="Click Me!" />
<PlaygroundButton label="Submit" />
<PlaygroundButton label="Save Changes" />
```

✅ Here, we pass **different labels** to each button!

✅ The `PlaygroundButton` component **renders whatever label** it receives.

---

## 🎨 Bonus Tip: Adding a Default Value

If you want a prop to have a **default value** (in case nothing is passed),  
you can set it directly when exporting:

```svelte
<script>
  export let label = "Default Text";
</script>
```

✅ Now if no `label` is passed, it will automatically use `"Default Text"`.

---

## 💬 Final Thoughts

- `export let` **opens a door** for passing information into components.
- You **pass props** when using components, like sending little instructions.
- Inside the component, you can **display or use** that information however you want.

Once you understand this simple idea,  
**building reusable, flexible components becomes much easier and more fun!** 🚀

---

## 🌟 Coming Next

Now that I understand how to pass props into components,  
I’ll explore how to **use slots** to pass not just simple values — but whole chunks of HTML!

Stay tuned!
