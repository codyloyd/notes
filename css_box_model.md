#Notes about the CSS box model.
the box model is dang confusing.. so I thought I'd write some notes to see if I could get it all to stick in my head.

I feel like I am usually just guessing with the dimensions/margin and padding until it looks right.

##The Box
the elements of the box, in order are:
* width/height
* padding
* border
* margin

![graphic](https://css-tricks.com/wp-content/csstricks-uploads/thebox.png)

###width
The default width of an element depends on its display value. _Block-level elements have a default width of 100%, consuming the entire horizontal space available. Inline and inline-block elements expand and contract horizontally to accommodate their content._ Inline-level elements cannot have a fixed size, thus the width and height properties are only relevant to non-inline elements. 
###height
The default height of an element is determined by it's content.  An element will expand and contract vertically as necessary to accomodate it's content.
###margin
Margin is space _outside_ the border. 
###padding
Padding is space _inside_ the border. 
####margin and padding for inline elements...
Inline-level elements are affected a bit differently than block and inline-block elements when it comes to margins and padding. Margins only work horizontally—left and right—on inline-level elements. Padding works on all four sides of inline-level elements; however, the vertical padding—the top and bottom—may bleed into the lines above and below an element.

Margins and padding work like normal for block and inline-block elements.

####Shorthand declarations for margin and padding
margin and padding can be declared using a shorthand method instead of having to specify `margin-top`, `margin-bottom` `margin-right` and `margin-left`
the format looks like this:

```html
div {
  margin: 10px 20px 0 15px;
}
```
here.. the order of the elements is __CLOCKWISE FROM THE TOP__. In other words: 
		`top`, `right`, `bottom`, `left`.

If you only declare 2 values, they are applied to top/bottom and then right/left:

```CSS
div {
  margin: 10px 20px;
}
```
in this example, the 10px is applied to both the top and bottom, and the 20px is applied to the right and the left.

##Borders
the border falls between the margin and the padding, and is visible.. it has thickness and requires, `width` `color` and `style` to be declared.  there are several different styles, but the most common are: _solid, dotted, dashed and none._

##Box Sizing
there are a couple of options that make the box model work differently... as if it wasn't confusing enough. the default is `box-sizing: content-box`.  this option will work exactly like is explained above.
####padding box.
another option is `box-sizing: padding-box`.  this one alters the box model by including the padding _inside_ the original dimensions of the box... so any padding added will make the content of the box shrink.
####border box
similarly `box-sizing: border-box` alters the model so that any border and padding are included in the width and height of the element.. margin will still extend the box... Border box actually seems to be really helpful! _REMINDER_ __USE BORDER BOX__


