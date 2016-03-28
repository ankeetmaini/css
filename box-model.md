# general
- [Replaced and Non-replaced elements in CSS](http://www.littlewebhut.com/css/info_nonreplaced_replaced/)
- `height` and `width` don't apply to **inline** elements.
- By default, the width of an element is defined to be the distance from the left inner edge to the right inner edge, and the height is the distance from the inner top to the inner bottom.
- This behavior can be changed using `box-sizing`
  - **content-box**: The width and height properties are measured including only the content, but not the padding, border or margin. Note: Padding, border & margin will be outside of the box.
  - **border-box**: The width and height properties include the padding and border, but not the margin. This is the box model used by Internet Explorer when the document is in Quirks mode. Note that padding and border will be inside of the box.

```
  box-sizing: content-box // OR border-box
```

- Values for `margin`, `padding` are applied in a clockwise manner. A good way to remember is is remembering **TRBL** or **TRouBLe**.

```
  padding: top right bottom left
```

# padding

- nonreplaced elements (like p, div, which have a starting, closing tag with content in between)
  - *top* and *bottom* padding don't increase the `line-height` of an inline element. But if the background is non transparent, the padding can extend below and above the element, and can overlap with other elements. [JSBin](https://jsbin.com/gafepe/1/edit?html,css,js,output)
  - *left* and *right* padding behaves normally, and doesn't overlap with other elements. [JSBin](https://jsbin.com/gafepe/2/edit?html,css,output)
  - If the inline element spans over multiple lines the *left* and *right* padding isn't applied over all slices [JSBin](https://jsbin.com/gafepe/3/edit?html,css,output), [box-decoration-break](https://developer.mozilla.org/en-US/docs/Web/CSS/box-decoration-break) can define how the padding, background etc are applied.

- replaced elements (like img, input, these don't have closing tags defined, no content)
  - padding affects `line-height` [JSBin](https://jsbin.com/gafepe/4/edit?html,css,output)

# borders
- Borders defined by *width*, *thickness* and *style*.
- default value
  - width: medium // 2 pixels approx
  - style: none, that's why we don't see borders if we don't set one explicitly
  - border-color: foreground `color` of text of element itself, if the element has no text like table, the color will be inherited from `color` of parent.
- top and bottom borders on replaced and nonreplaced elements will behave exactly as padding did. (see above section on padding)

# border-image
// TODO JSBin(https://jsbin.com/gafepe/5/edit?html,css,output)

# outlines
- Outlines are drawn just beyond the borders but are different in the following aspects
 - they don't take space and hence don't affect **layout**
 - they can be non-rectangular, when the inline element spans multiple lines
 - they can't be styled differently for *top, left, bottom and top*

# margins
- Like `padding` if given in percentage, it's calculated based on the width of the element rather than its height.
- Margins **collapse** [JSBin](https://jsbin.com/bipidu/1/edit?html,css,js,output)
- The bigger margin is kept while the other element's smaller margin is reset to 0.
- When a block element is placed inside another block element it's top and bottom margins are clipped by the containing element. [JSBin](https://jsbin.com/migeco/edit?html,css,output)
