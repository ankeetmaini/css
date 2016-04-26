# transforms
 - By convention, positive x values go to the right, and negative values go to the left. Similarly, positive y values go downward along the y-axis, while negative values go upward along the y-axis.
 - z axis is the one that “sticks out” of the display and runs straight through your head. In a theoretical sense, that is. Positive z values are closer to you, and negative z values are further away from you. In this regard, it’s exactly like the z-index property.
 - **bounding box**: for any element being affected by CSS, this is the border box; that is, the outermost edge of the element’s border. That means that any outlines and margins are ignored for the purposes of calculating the bounding box.
 - all transformed elements (i.e., elements with transform set to a value other than none) have their own stacking context.
 - While the scaled element may be much smaller or larger than it was before the transform was applied, the actual space on the page that the element occupies remains the same as before the transform was applied
 - e.g. `#example {transform: rotate(30deg) skewX(-25deg) scaleY(2);}`, [first-to-last processing order]
 - when you have a series of transform functions, all of them must be properly formatted; that is, they must be valid. If even one function is invalid, it renders the entire value invalid
 - transforms are not applied to “atomic inline-level” boxes (spans, hyperlinks, and so on)
  - a span (or any inline-level box) that breaks across multiple lines. If you rotate it, what happens? Does each line box rotate with respect to itself, or should all the line boxes be rotated as a single group? There’s no clear answer, and the debate continues, so for now you can’t directly transform inline-level boxes.

## transform functions
 - Google search (scale|scaleX|scaleY|scaleZ|scale3d, translate|translateX|translateY|translateZ|translate3d, rotate|rotateX|rotateY|rotateZ, skew|skewX|skewY)

## transform-origin
 - lets you modify the origin for transformations of an element. [More info here](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-origin)
