#Notes on Floats and Positioning
this should be a pretty big deal.. It's the thing I think I struggle with the most at this point...
The main articles this information comes from are here:
- [css-floats](http://alistapart.com/article/css-floats-101)
- [positioning](http://alistapart.com/article/css-positioning-101)
##CSS FLOATinG
a float is a box that is shifted to either the left or the right, and that lets text/otherstuff flow along it's side.

floats shift to the side of their parent element.. you can tell a it to `float: inherit` too which should make it do the same type of floating it's parent does.  the default value of this parameter is `float: none` (duh)

>####normal flow
>important to remember how the flow is supposed to work: In the normal flow, each block element `(div, p, h1, etc.)` stacks on top of each other vertically, from the top of the viewport down. Floated elements are first laid out according to the normal flow, then taken out of the normal flow and sent as far to the right or left (depending on which value is applied) of the parent element. In other words, they go from stacking on top of each other to sitting next to each other, given that there is enough room in the parent element for each floated element to sit.

when floating multiple things, they all end up right next to each other (this breaks out of normal flow) and if there are more things than fit on one line they will wrap to a newline
### clear
problem though.. floated things are removed from the normal flow.. so non-floated things act as if they aren't even there and will render ontop or underneath the floated things... the solution to this is the `clear` property.
`clear` can take the following values: `left, right, both, inherit and none`. If an object is set to `clear: left` it's top edge must sit below any element that is floated left, and likewise for the other options.
####order matters...
things that are floated should almost always be first in your html... otherwise strange things could happen.
####collapsing
collapsing is when a parent element that contains any number of floated elements doesn't expand to completely surround those elements.  This happens because floated elements are considered OUTSIDE of the normal flow.. so if a float is declared AFter another item, the container box will conform to the first item, and the float will be left hanging outside it.
- one option to fix collapsing is to put something with a `clear` property after the floated item.
- another option: There is a method that allows a parent element to clear itself of any floated elements inside it. It uses a CSS property called overflow with a value of hidden. Note that the overflow property was not intended for this type of use, and could cause some issues such as hiding content or causing unwanted scrollbars to appear. 
- Another method which gives similar results with fewer caveats uses the pseudo selector `:after`:

```css
#container:after {
	content: ".";
	display: block;
	height: 0;
	clear: both;
	visibility: hidden;
}
```
- doing this creates a new pseudo-block after everything else in the container and makes it hidden
- lastly.. if you float the parent container, it will recognize it's floated children and resize itself accordingly.

##POSITIONING