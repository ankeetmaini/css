# float

- When an element is *floated* other content *flows around it*. It still affects the layout.
- Margins with floated elements do not collapse. <a href='https://jsbin.com/mikide/edit' target='_blank'>JSBin</a>
- The parent which contains the floating element is called *container block*.
- Floated elements generate a **block box**. Even if an inline element like `a` is floated.
- Rules which determine the final position of a floated element:
  - The floated element can't float further than its *container*. It's bound by it.
  - A floated element will stack with another element floated before it. The floated elements don't overwrite each other.
  - In case there is a floated element before the current element and the current element's top is lower than the previous element's bottom then the current floated element will not stack up with previous but will go to as right/left it can go.
  - Floated elements **don't float above.**
  - A floating element's top cannot be higher than a previous floating element's top or a block level element.
- Exceptions
  - A floated element if taller than container element can reach beyond the parent.
  - Negative margins can make the floated element show outside its container block. When that happens the floated element will most probably overwrite the content as the browser is not mandated to do a reflow for things like these.
  - **If a floated element overlaps an inline element, all content, background and border are rendered on top of the float, whereas in case of a block element only content is on top and background, border is rendered behind.**

# clear

- `clear` is used on any element that shouldn't flow around a *floated* element.
- It only applies to **block** elements.

```css
  clear: left;
  // clear: right;
  // clear: both;
```

- It worked in CSS1 and CSS2 by increasing the top margin. It also meant that any top margin given to a cleared element will effectively be ignored.
- `clearance` was introduced in CSS2.1 it was equal to the extra spacing added on top of the margin value of the cleared element.
- The best way to create a space between a floated element and a cleared one is to add a `margin-bottom` of the floated element.

# shape-outside

- Used to shape the flow of content around a float.
- Only applies to **floated elements**.
