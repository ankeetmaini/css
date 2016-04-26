# display
- this property is used to change the display of elements
- changing the display doesn't change the meaning of elements, so a `span` *block* can't enclose `p`

# horizontal formatting: block elements
- *center* => to center block elements, give a width and margin `auto`
- if all width and margin are made `auto`, then margins are set to 0, and width expands to take the full space of containing block.
- **holy equation** => margin-left + border-left + padding-left + width + padding-right + border-right + margin-right = width of container
- If `margin-right` is explicitly set to a value which does not satisfy the above equation, the `margin-right` will be **reset** automatically to satisfy the LHS and RHS.
- Only margins can be negative, not borders, padding and width.
- **In case of replaced block elements width: auto calculates the intrinsic width not full.**
- *If width of a replaced element is changed, the height too is scaled, vice-versa is also true. Unless both are mentioned explicitly.*

# vertical formatting: block elements
- Same as horizontal formatting except the variables are a little changed.
- margin-top + border-top + padding-top + height + padding-bottom + border-bottom + margin-bottom = height of block box's containing box
- **If an auto-height, normal-flow block box has only block-level children, then its default height will be the distance from the top of the topmost block-level child’s outer border edge to the bottom of the bottommost block-level child’s outer bottom border edge. Therefore, the margins of the child elements will “stick out” of the element that contains them.** (Border to Border)
- **However, if the block-level element has either top or bottom padding, or top or bottom borders, then its height will be the distance from the top of the outer-top margin edge of its topmost child to the outer-bottom margin edge of its bottommost child** [JSBin](https://jsbin.com/sehuja/1/edit?html,output)
- Vertical margins also collapse.

# inline elements
## Layout process for text contained by an inline element
 - find `font-size` and `line-height`
 - get the `leading` = `line-height` - `font-size`, divide it by 2 and apply to the top and bottom of the `em box`
 - add margins, borders and padding if applicable
 - determine the vertical offset, and see the value of `vertical-align` property

## Layout process for text **NOT** contained by an inline element (inline nonreplaced elements)
 - for each letter, an `em` box is created with height equal to `font-size`
 - then `line-height` is considered and the difference of it with `font-size` is applied equally to the top and bottom of the `em` box, whether positive or negative. The resultant box is called an **inline box**.
 - all inline boxes are then joined to get a `line box`. (there can be multiple inline boxes if anonymous text is mixed with some inline tags, like "Hey I am <strong>awesome</strong>")
 - `vertical-align` controls the alignment of `inline-box` and `line-box`
 - **line-height** can be given a plain number, which the browser then takes as a scaling factor w.r.t `font-size`. With this, individual inline elements that affect line-height
  > Another solution—possibly the simplest of all—is to set the styles such that lines are no taller than absolutely necessary to hold their content. This is where we might use a line-height of 1.0. This value will multiply itself by every font-size to get the same value as the font-size of every element.

## Box properties for inline elements
 - Padding, margins, borders **do not** affect `line-height` at all.
 - Border depends on the `font-size` rather than `line-height`. So the *border* surrounds the `content-area` of the inline element.
 - In case of padding and borders, the borders will be pushed out from the text, but again, no changes in the `line-height` thus the layout.
 - **breaking behaviour**: inline nonreplaced elements are treated as a single line broken down, with margin (left|right) and padding (left|right) applied.
  - this is the default behaviour and can be changed by `box-decoration-break` whose default value is `slice`
  - `clone` makes each broken element to be treated as a new line, so margins, paddings are applied to each element, not just to the start and ending.
  - the entirety of the **replaced element**—content, margins, borders, and padding—is used to define the element’s inline box. e.g. <img> tag
  - When positioning <img> (replaced inline elements) the height of the image has got no bearing in the vertical alignment of the image [JSBin](https://jsbin.com/jihoresobu/edit?html,css,output)
  - Margins, paddings and borders of a replaced inline element **affect** `line box height`. [JSBin](https://jsbin.com/jihoresobu/5/edit?html,css,output)
  - Replaced elements to not have baselines, their bottom-outer-margin-edge lies on the baseline when no `vertical-align` property is given.

## display: inline-block
  - it's laid out as a replaced inline element, like img.
  - This means the bottom of the inline-block element will rest on the baseline of the text line by default and will not linebreak within itself.
  - Inside the inline-block element, the content is formatted as though the element were block-level. The properties width and height apply to it (and thus so does box-sizing), as they do to any block-level or inline replaced element, and those properties will increase the height of the line if they are taller than the surrounding content.
