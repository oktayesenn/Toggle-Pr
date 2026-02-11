# Inbox App — `script.js` Instructions

**DOM Events & classList | Day 1 + Day 2**

---

## How This Lab Works

Open your `script.js` file — it should be empty. You will build it **feature by feature** by following the instructions below.

Every feature follows the same **3-step pattern**:

> 1. **SELECT** the element(s) you need using `document.querySelector()`
> 2. **CREATE** a function that changes something on the page
> 3. **LISTEN** for the event using `addEventListener()`

Before you start coding, always **right-click → Inspect** the element in your browser to find its ID or class name. That's how you know what to put inside `querySelector()`.

---

## DAY 1: `add()` and `remove()`

---

### Feature 1: Make "Your Inbox" turn blue on click

Right-click the "Your Inbox" heading in your browser and choose **Inspect**. Notice it has `id="heading"`.

**What is `querySelector()`?**

`document.querySelector()` grabs an element from your HTML so JavaScript can work with it. You pass it a CSS selector — just like you'd use in your stylesheet. Use `#` for IDs and `.` for classes.

**What is `classList.add()`?**

`classList.add("className")` takes a CSS class from your stylesheet and attaches it to an element. The styles apply instantly. The class `blue-text` already exists in your `style.css` — go look at it!

**What is `addEventListener()`?**

This tells the browser: "Watch this element. When the user clicks it, run this function." It takes two things: the event type (`"click"`) and the function to run.

**Now write this in your `script.js`:**

```js
// ========== Feature 1: Heading Color ==========

// STEP 1: Select the heading
const heading = document.querySelector("#heading");

// STEP 2: Create a function that adds the blue-text class
const changeFontColor = () => {
    heading.classList.add("blue-text");
};

// STEP 3: Listen for a click on the heading
heading.addEventListener("click", changeFontColor);
```

**Save your file, refresh the browser, and click "Your Inbox." It should turn blue!**

> ⚠️ **Watch out!** In `addEventListener`, do NOT put parentheses after the function name. Write `changeFontColor` — not `changeFontColor()`. With parentheses, the function runs immediately instead of waiting for the click.

> 📝 **Good to know:** The opposite of `.add()` is `.remove()`. Example: `element.classList.remove("hidden");` — you'll use this soon!

---

### 🌶️ Mild — Feature 2: Make the subtitle turn blue on click

**Goal:** When "Today is September 1st" is clicked, it should turn blue.

- **Step 1:** Inspect the subtitle text in your browser. Find its **ID**.
- **Step 2:** In `script.js`, use `document.querySelector()` to select the subtitle using the ID you just found.
- **Step 3:** Create a function that adds `"blue-text"` to the subtitle's classList.
- **Step 4:** Add an `addEventListener` on the subtitle that listens for `"click"` and calls your function.
- **Step 5:** Save, refresh, and click the subtitle to test.

```js
// ========== Feature 2: Subtitle Color ==========

const subtitle = document.querySelector("#____");  // fill in the ID

const changeSubtitleColor = () => {
    subtitle.classList.add("blue-text");
};

subtitle.addEventListener("click", changeSubtitleColor);
```

---

### 🌶️ Mild — Feature 3: Show the Reply section

**Goal:** When the "Reply" button is clicked, the hidden reply area should appear.

**How does hiding work in this project?**

Look in your `style.css` for a class called `hidden`. It sets `display: none;` which makes an element invisible. The reply section (`#reply-message`) already has this class in the HTML. To make it visible, you need to **remove** that class.

> 💡 **This feature needs TWO querySelectors!** You need to select the Reply button (the thing being clicked) AND the `#reply-message` div (the thing being changed). These are two different elements.

- **Step 1:** Inspect the "Reply" button in your browser. Find its **ID**.
- **Step 2:** In `script.js`, select **both** elements: the Reply button and `#reply-message`.
- **Step 3:** Create a function that **removes** the `"hidden"` class from `#reply-message`.
- **Step 4:** Add an `addEventListener` on the Reply button.
- **Step 5:** Save, refresh, click Reply — the reply section should appear!

```js
// ========== Feature 3: Show Reply Section ==========

const replyBtn = document.querySelector("#____");  // Reply button ID
const replyMessage = document.querySelector("#reply-message");

const showReply = () => {
    replyMessage.classList.remove("hidden");
};

replyBtn.addEventListener("click", showReply);
```

> ✅ **Check in with your teacher after completing this feature!**

---

### 🌶️ Mild — Feature 4: Hide the Reply section

**Goal:** Both "Send Message" and "Cancel" buttons should hide the reply section.

- **Step 1:** Inspect both buttons to find their IDs.
- **Step 2:** Select both buttons with `querySelector`. (You already have `replyMessage` selected from Feature 3.)
- **Step 3:** Create a function that **adds** the `"hidden"` class back to `replyMessage`.
- **Step 4:** Add an `addEventListener` on **both** buttons. Both can call the same function!

```js
// ========== Feature 4: Hide Reply Section ==========

const sendBtn = document.querySelector("#____");
const cancelBtn = document.querySelector("#____");

const hideReply = () => {
    replyMessage.classList.add("hidden");
};

sendBtn.addEventListener("click", hideReply);
cancelBtn.addEventListener("click", hideReply);
```

> 💡 **Reuse your functions!** Notice both buttons use the same `hideReply` function. You don't need to write two separate functions when they do the same thing.

---

### 🌶️🌶️ Medium — Feature 5: The "Open" button

**Goal:** Clicking "Open" should do **three things at once**:

- a) Add the `is-read` class to `#inbox` (changes background to grey)
- b) Remove `hidden` from `#inbox-message` (shows the email content)
- c) Remove `hidden` from the "Mark as Unread" button (makes it visible)

**How do you find all these elements?** Use **Inspect** in your browser to find the IDs for the Open button, the inbox, the inbox message, and the Mark as Unread button. You'll need **four** querySelectors for this feature.

> 💡 **One function, multiple actions.** A function can have as many lines as you need. Each classList statement runs in order, one after the other. All three changes happen in the same click.

- **Step 1:** Inspect to find all 4 element IDs.
- **Step 2:** Select all 4 elements with `querySelector`.
- **Step 3:** Create one function that does all three classList changes.
- **Step 4:** Add an `addEventListener` on the Open button.

```js
// ========== Feature 5: Open Button ==========

const openBtn = document.querySelector("#____");
const inbox = document.querySelector("#inbox");
const inboxMessage = document.querySelector("#inbox-message");
const unreadBtn = document.querySelector("#____");

const openMessage = () => {
    inbox.classList.add("is-read");
    inboxMessage.classList.remove("hidden");
    unreadBtn.classList.remove("hidden");
};

openBtn.addEventListener("click", openMessage);
```

---

### 🌶️🌶️ Medium — Feature 6: Close the inbox message (X button)

**Goal:** The X button at the top-right of the inbox message should hide the message.

- **Step 1:** Inspect the X button to find its ID.
- **Step 2:** Select it with `querySelector`.
- **Step 3:** Create a function that adds `"hidden"` back to `#inbox-message`. (You already have `inboxMessage` selected!)
- **Step 4:** Add the `addEventListener`.

```js
// ========== Feature 6: Close Message (X Button) ==========

const closeBtn = document.querySelector("#____");

const closeMessage = () => {
    inboxMessage.classList.add("hidden");
};

closeBtn.addEventListener("click", closeMessage);
```

---

### 🌶️🌶️🌶️ Spicy — Feature 7: Mark as Unread

**Goal:** The "Mark as Unread" button should: hide the inbox message, turn the inbox background white again, and hide itself.

You already have `unreadBtn`, `inboxMessage`, and `inbox` selected from Feature 5. Reuse them!

- **Step 1:** Create a function that does three things:
  - Adds `"hidden"` to `inboxMessage`
  - Removes `"is-read"` from `inbox`
  - Adds `"hidden"` to `unreadBtn` (hides itself!)
- **Step 2:** Add the `addEventListener` on `unreadBtn`.

```js
// ========== Feature 7: Mark as Unread ==========

const markUnread = () => {
    inboxMessage.classList.add("hidden");
    inbox.classList.remove("is-read");
    unreadBtn.classList.add("hidden");
};

unreadBtn.addEventListener("click", markUnread);
```

---

### 🌶️🌶️🌶️ Spicy — Feature 8: Subtitle Toggle Challenge

**Goal:** Clicking the subtitle should toggle a **custom class you create** on another element. If the class is there, remove it. If not, add it.

**What is `classList.contains()`?**

`classList.contains("className")` returns `true` if the element has that class, or `false` if it doesn't. Use it inside an `if/else` to decide what to do.

- **Step 1:** In `style.css`, create your own class with visible styles (background color, border, font change, etc.).
- **Step 2:** Pick a target element on the page that you want to change.
- **Step 3:** In `script.js`, select the subtitle and the target element.
- **Step 4:** Write a function using the `if/else` pattern below.
- **Step 5:** Add the `addEventListener` on the subtitle.

```js
// ========== Feature 8: Toggle Challenge ==========

// You already have subtitle selected from Feature 2

const targetElement = document.querySelector("#____");

const toggleCustomClass = () => {
    if (targetElement.classList.contains("my-custom-class")) {
        targetElement.classList.remove("my-custom-class");
    } else {
        targetElement.classList.add("my-custom-class");
    }
};

subtitle.addEventListener("click", toggleCustomClass);
```

---

## DAY 2: `toggle()`

---

**What is `classList.toggle()`?**

`toggle()` combines `add()` and `remove()` into one method. If the class is there, it removes it. If it's missing, it adds it. One line does what `contains()` + `if/else` does in four lines.

> 💡 **Why use `toggle()` instead of add/remove?** It's cleaner and less error-prone. Instead of checking the current state yourself, you let the browser handle it. Use it whenever you want a "switch" effect — click once to turn on, click again to turn off.

---

### First: Update your heading code

Go back to your Feature 1 code at the top of `script.js`. Change `.add()` to `.toggle()`:

```js
// ========== Feature 1: Heading Color (UPDATED) ==========

const heading = document.querySelector("#heading");

const changeFontColor = () => {
    heading.classList.toggle("blue-text");  // changed from .add()
};

heading.addEventListener("click", changeFontColor);
```

Save and test — click the heading multiple times. It should switch between blue and black!

---

### 🌶️ Mild — Feature 9: Toggle the subtitle color

**Goal:** Change your subtitle code so it toggles between blue and black.

- **Step 1:** Find your Feature 2 code.
- **Step 2:** Change `.add("blue-text")` to `.toggle("blue-text")`.
- **Step 3:** Save and click the subtitle multiple times to test.

---

### 🌶️ Mild — Feature 10: Checkbox toggle

**Goal:** Clicking the checkbox should select the inbox (blue background) AND show the action buttons. Clicking again should reverse both.

- **Step 1:** Inspect the checkbox to find its ID.
- **Step 2:** Select the checkbox, `#inbox`, and the `#action-buttons` div.
- **Step 3:** Create a function that toggles `"is-selected"` on the inbox AND toggles `"hidden"` on the action buttons.
- **Step 4:** Add the `addEventListener` on the checkbox.

```js
// ========== Feature 10: Checkbox Toggle ==========

const checkbox = document.querySelector("#____");
const actionButtons = document.querySelector("#action-buttons");

const handleCheckbox = () => {
    inbox.classList.toggle("is-selected");
    actionButtons.classList.toggle("hidden");
};

checkbox.addEventListener("click", handleCheckbox);
```

---

### 🌶️🌶️ Medium — Feature 11: Delete & Undo

**Goal:** The Delete button should hide the inbox and change its text to "Undo Deletion." Clicking again should reverse everything.

**What is `innerHTML`?**

`innerHTML` lets you read or change the text/HTML inside an element. You can use it to swap button labels dynamically.

- **Step 1:** Inspect to find the Delete button's ID.
- **Step 2:** Select it with `querySelector`.
- **Step 3:** Create a function that: toggles `"hidden"` on the inbox, AND uses an `if/else` to swap the button text.
- **Step 4:** Add the `addEventListener`.

```js
// ========== Feature 11: Delete & Undo ==========

const deleteBtn = document.querySelector("#____");

const handleDelete = () => {
    inbox.classList.toggle("hidden");

    if (deleteBtn.innerHTML === "Delete Message(s)") {
        deleteBtn.innerHTML = "Undo Deletion";
    } else {
        deleteBtn.innerHTML = "Delete Message(s)";
    }
};

deleteBtn.addEventListener("click", handleDelete);
```

> ⚠️ **`innerHTML` comparison is exact.** When you check `innerHTML === "Delete Message(s)"`, the text must match EXACTLY — including capitalization, spaces, and punctuation.

---

### 🌶️🌶️ Medium — Feature 12: Mark as Read

**Goal:** The "Mark as Read" button should: show the Mark as Unread button, deselect the inbox, turn the inbox grey, and uncheck the checkbox.

**How do you uncheck a checkbox with JavaScript?**

Checkboxes have a special property called `.checked`. Set it to `false` to uncheck it: `checkbox.checked = false;`

- **Step 1:** Inspect to find the Mark as Read button's ID.
- **Step 2:** Select it. (You already have `unreadBtn`, `inbox`, and `checkbox` selected.)
- **Step 3:** Create a function that does all four things:
  - Removes `"hidden"` from `unreadBtn`
  - Removes `"is-selected"` from `inbox`
  - Adds `"is-read"` to `inbox`
  - Sets `checkbox.checked = false;`
- **Step 4:** Add the `addEventListener`.

```js
// ========== Feature 12: Mark as Read ==========

const readBtn = document.querySelector("#____");

const markRead = () => {
    unreadBtn.classList.remove("hidden");
    inbox.classList.remove("is-selected");
    inbox.classList.add("is-read");
    checkbox.checked = false;
};

readBtn.addEventListener("click", markRead);
```

---

### 🌶️🌶️🌶️ Spicy — Feature 13: Dark Mode

**Goal:** The "Dark Mode" button should toggle a dark color scheme on the entire page.

- **Step 1:** First, go to `style.css` and create a `.dark-mode` class:

```css
/* Add this to your style.css */
.dark-mode {
    background-color: #1a1a2e;
    color: #e0e0e0;
}

/* Feel free to customize! Look up Gmail dark mode for ideas */
```

- **Step 2:** In `script.js`, select the Dark Mode button and the `<body>` element.
- **Step 3:** Create a function that toggles `"dark-mode"` on the body.
- **Step 4:** Add the `addEventListener`.

```js
// ========== Feature 13: Dark Mode ==========

const darkModeBtn = document.querySelector("#____");
const body = document.querySelector("body");

const toggleDarkMode = () => {
    body.classList.toggle("dark-mode");
};

darkModeBtn.addEventListener("click", toggleDarkMode);
```

---

## Quick Reference

| Method | What It Does |
|--------|-------------|
| `querySelector("#id")` | Grabs an element from the HTML by its CSS selector |
| `classList.add("class")` | Attaches a CSS class to the element |
| `classList.remove("class")` | Detaches a CSS class from the element |
| `classList.toggle("class")` | Adds if missing, removes if present (switch effect) |
| `classList.contains("class")` | Returns true/false — checks if the class is on the element |
| `addEventListener("click", fn)` | Runs the function `fn` when the element is clicked |
| `innerHTML = "text"` | Changes the text/HTML inside an element |
| `checkbox.checked = false` | Unchecks a checkbox |

---

> 🚀 **Remember the pattern:** SELECT → CREATE FUNCTION → LISTEN. When stuck: Inspect first, then check your selectors, then check your class names. Happy coding!