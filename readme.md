# Emergency Service Directory — README

This small project implements an **Emergency Service Directory** with a navbar, hero, cards, and a call history panel. It is built with **HTML, CSS, and vanilla JavaScript** only (no frameworks).

## How to Run
Just open `index.html` in any browser. All assets are local.

---

## Answers to the Required Questions

### 1) Difference between `getElementById`, `getElementsByClassName`, and `querySelector` / `querySelectorAll`

- **`getElementById(id)`**: Returns **one** element that has the exact `id`. It’s fast and specific. If the id doesn’t exist, it returns `null`.

- **`getElementsByClassName(className)`**: Returns a **live HTMLCollection** of all elements with that class. It updates automatically if the DOM changes. You usually convert it to an array before using array methods.

- **`querySelector(cssSelector)`**: Returns the **first** element that matches a **CSS selector** (e.g., `#nav .item[data-x="1"]`). Very flexible.

- **`querySelectorAll(cssSelector)`**: Returns a **static NodeList** of **all** elements that match the CSS selector. It does **not** auto-update if the DOM changes (you must call it again).

### 2) How to create and insert a new element into the DOM

```js
const li = document.createElement('li');      // 1) create
li.textContent = 'New item';                  // 2) configure
li.classList.add('todo');                     // 3) style/attributes
document.querySelector('#list').append(li);   // 4) insert into the DOM
```
Other useful insertion APIs: `prepend`, `before`, `after`, `replaceWith`, and `insertAdjacentHTML(position, html)`.

### 3) What is Event Bubbling and how does it work?

**Event bubbling** means that when an event happens on an element (like a button), the event **travels upward** through its ancestors: button → card → section → document. Each ancestor can listen for the same event type. This is the default phase for most events in browsers. You can stop bubbling with `event.stopPropagation()`.

### 4) What is Event Delegation? Why is it useful?

**Event delegation** is a pattern where you **attach one listener to a parent** element and handle events for **child elements** by checking `event.target` (or `closest(...)`). It’s useful because:

- You add **fewer listeners** (better performance and memory).
- It **works for future elements** added dynamically (no need to re-bind).
- Cleaner code for lists, tables, and grids.

Example:
```js
document.querySelector('#list').addEventListener('click', (e) => {
  const item = e.target.closest('.todo');
  if (!item) return;
  // handle click for any .todo inside #list, even future ones
});
```

### 5) Difference between `preventDefault()` and `stopPropagation()`

- **`preventDefault()`**: Stops the **default browser action** (e.g., prevent a link from navigating, stop form submission).
- **`stopPropagation()`**: Stops the **event from bubbling** to parent elements (ancestors). They solve different problems and can be used together if needed.

---

## Notes on Features Implemented

- **Navbar counters**: Heart, coins (start at 100), copy count.
- **Hero**: Full-width gradient, logo, title, slogan.
- **Cards**: Minimum of 6 cards with icon, name (Bangla context), English name, hotline, badge, heart, and actions.
- **Heart**: Clicking any heart increases the total heart count.
- **Copy**: Copies the hotline number to the clipboard and increases the copy counter.
- **Call**: Shows an alert with service & number, deducts 20 coins (if possible), and appends an entry to **Call History** with the **local date & time**.
- **Call History**: Has a Clear button to remove all entries.
- **Responsive**: Cards stack on small screens; history moves below the grid.

---

## Folder Structure
```
emergency-service-directory/
├─ index.html
└─ assets/
   └─ logo.png
```

Enjoy building! ✨
