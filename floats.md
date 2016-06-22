# float

- When an element is *floated* other content *flows around it*. It only affects the `line boxes` which may be inside block elements.
- It doesn't disturb the vertical stacking of block elements at all.
- Margins with floated elements do not collapse. [JSBin](https://jsbin.com/mikide/edit)
- The parent which contains the floating element is called *container block*.
- Floated elements generate a **block box**. Even if an inline element like `a` is floated.
- Rules which determine the final position of a floated element:
  - The floated element can't float further than its *container*. It's bound by it.
  - A floated element will stack with another element floated before it. The floated elements don't overwrite each other.
  - Floats do not affect the line boxes inside elements in normal flow that establish new block formatting contexts. Instead, such elements are either placed to the side of the float, or cleared by placing them below any preceding floats. [Example](https://jsbin.com/jiduxikome/1/edit?html,css,output). It turns out that this behavior is quite useful and practically important - most CSS grid frameworks make use of floats and an overflow value other than visible for layout.
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

```
  clear: left;
  // clear: right;
  // clear: both;
```

- It worked in CSS1 and CSS2 by increasing the top margin. It also meant that any top margin given to a cleared element will effectively be ignored. Because, `margin-collapse `
- `clearance` was introduced in CSS2.1 it was equal to the extra spacing added on top of the margin value of the cleared element.
- The best way to create a space between a floated element and a cleared one is to add a `margin-bottom` of the floated element.

# clearfix

- A clearfix combines several desirable properties into one class
  - it prevents the floats within the clearfixed parent element from affecting line boxes in other elements that follow the clearfixed element
  - it causes the floats within the clearfixed parent element to be taken into account when calculating that element's height
- [Problem](https://jsbin.com/boxapeyaho/1/edit?html,css,output)
- [Solution with clearfix](https://jsbin.com/nibajabuqi/1/edit?html,css,output)
- [Solution with overflow: auto](https://jsbin.com/zokokaveku/1/edit?html,css,output)

# shape-outside

- Used to shape the flow of content around a float.
- Only applies to **floated elements**.
- Without using shapes, the content will flow around in a rectangular manner. [JSBin](https://jsbin.com/duluweq/1/edit?html,css,output)
- `shape-outside`'s value can be `none`, `<basic-shape>`, `<shape-box>` or `none`.
- `basic-shape` can be one of the following:-
  - `inset()`
  - `circle()`
  - `ellipse()`
  - `polygon()`
- `shape-box` can be one of the following:-
  - `margin-box`, content flows around the margin, **default**
  - `border-box`, content flows around the border
  - `padding-box`, content flows around the padding
  - `content-box`, content flows around the content
- The following code generates an [ellipse shape](examples/ellipse.png)
```
aside {
  float: right;
  height: 200px;
  width: 200px;
  background: cornsilk;
  padding: 10px;

  /* shape-outside */
  shape-outside: inset(2% round 50% 25%);
}
```
- A [circle](examples/circle.png) can also be generated if you were to change the `shape-outside` property to this
```
shape-outside: inset(2% round 50% 50%); // 1
shape-outside: circle(130px at 50% 50%); // 2
```
- Shapes cannot exceed their shape box, even if they seem so, the content will flow around the `shape-box`
- `shape-margin` can be used to give margins to the shape, but again, `shape-margin` too is cliped by the `shape-box`.
