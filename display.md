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
- **If an auto-height, normal-flow block box has only block-level children, then its default height will be the distance from the top of the topmost block-level child’s outer border edge to the bottom of the bottommost block-level child’s outer bottom border edge. Therefore, the margins of the child elements will “stick out” of the element that contains them.**
- **However, if the block-level element has either top or bottom padding, or top or bottom borders, then its height will be the distance from the top of the outer-top margin edge of its topmost child to the outer-bottom margin edge of its bottommost child** [JSBin](https://jsbin.com/sehuja/1/edit?html,output)
- Vertical margins also collapse.
