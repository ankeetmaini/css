# General (positioning, layout)

- Elements with a display property other than inline or block will still map to one of the two formatting contexts within normal flow. Block/inline decides the layout algorithm.
- The parent container establishes the formatting context for its children, whether they'll be treated as `block` or `inline`
 - [Block elements stack vertically even if they can fit in the same line](https://jsbin.com/rofuzofesa/1/edit?html,css,output)
 - Each block-level element generates a principal block-level box that contains descendant boxes and generated content and is also the box involved in any positioning scheme.
 > Except for table boxes [...] and replaced elements, a block-level box is also a block container box. A block container box either contains only block-level boxes or establishes an inline formatting context and thus contains only inline-level boxes.

 - Inline elements just stay together :P
 > Inline-level boxes that are not inline boxes (such as replaced inline-level elements, inline-block elements, and inline-table elements) are called atomic inline-level boxes because they participate in their inline formatting context as a single opaque box.

- Anonymous box generation is used to deal with cases where a parent element contains a mixture of inline-level and block-level child elements (in which case "anonymous block boxes" are generated) and with cases where the markup contains inline-level elements mixed with surrounding text (in which case "anonymous inline boxes" are generated), such as an em or i tag inside a paragraph of text.
> [Take a look at spec here](https://www.w3.org/TR/CSS2/visuren.html#anonymous-block-level)

- In a box formatting context, boxes are laid out vertically, and that every box's left outer edge will touch the left outer edge of the containing block (even in the presence of floats). [JSBin example](https://jsbin.com/yefehahiba/1/edit?html,css,output)

# [inline elements layout process](https://www.w3.org/TR/2011/REC-CSS2-20110607/visuren.html#inline-formatting)

# text-align
- it controls how inline-level boxes are positioned on a line box.
 - it only applies when the line box contains some unused space, and that you cannot directly control how inline-level content is placed on line boxes
 > When the total width of the inline-level boxes on a line is less than the width of the line box containing them, their horizontal distribution within the line box is determined by the 'text-align' property. If that property has the value 'justify', the user agent may stretch spaces and words in inline boxes (but not inline-table and inline-block boxes) as well.

# vertical-align
- following two properties control vertical alignment within line boxes

|Property|default|explanation|
|--------|-------|-----------|
|vertical-align|baseline|Controls the vertical alignment of boxes. Only applies to inline (and table-cell) boxes|
|line-height|normal (~1.2 times font height)|Specifies the height that is used to calculate line box height.|

- `vertical-align` controls the vertical alignment of inline boxes within line boxes - not the vertical alignment of the line boxes themselves.
- the height of inline boxes is determined by their font and their line height. Specifically, each font must define a baseline, a text-top edge and a text-bottom edge. The calculated height of the content area of an inline box is the height of the font (e.g. bottom - top) multiplied by the line-height value
  - line-height can be specified relative to the font height, or it can be set to an absolute length value, in which case the font height is no longer involved in calculating the height of the inline box.
- height of inline boxes: (baselines defined by font) top-text-edge - bottom-text-edge  * line-height
- using inline layout concepts
  - [**vertical alignment**](https://jsbin.com/tudepaguyi/1/edit?html,css,output)
  - [**anonymous box generation**](https://jsbin.com/maluqefoli/1/edit?html,css,output) problem
  
