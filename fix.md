# Fix list

## 1. Best buy cards — numbers look broken

**What you see**
- On "Which is better value?" the numbers (2, 10, 0.52, 2) sit in little boxes.
- The boxes overlap the text ("Pack A", "eggs for").
- Happens when the tap-numbers / no-calculator mode is on.

**Why**
- Tap mode wraps each number in a `<span class="tn">` (`index.html:1450`).
- The card style uses `.q .packs span` (`index.html:97`).
- That rule hits **every** span inside the cards — so the number spans get the card's border, background and padding too.

**Fix**
- Make the rule only hit the card itself, not spans inside it:

```css
.q .packs > span { ... }
```

- Or give the cards their own class (e.g. `class="pack"`) and style `.pack`.

**Check after**
- Best buy question, tap mode on — numbers only have the gold dashed underline.
- Tapping a number still adds it to the jotter.
