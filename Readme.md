# In case you want to apply the same style to the majority of the elements inside your page, do it by styling the body:

body {
  color: red;
}

.an-element {
  color: white;
}

# The above code will apply the text color to almost all the elements, except to the element with the class='an-element';

# COMBINATORS

Allow you to mix different selectors.

If you want to target an element depending on its parent, do this:

#parent elementToTarget(child) {
  background: black;
}

# Adjacent sibling

Asigns styles to all childs that come immediately after the parent tag

h2 + p {
  color: red;
}

<div>
  <h2>Not applied</h2>
  <p>CSS applied</p>
  <h2>Not applied</h2>
  <h3>Not applied</h3>
  <p>Not applied</p>
  <h2>Not applied</h2>
  <p>CSS applied</p>
</div>

# General sibling

-Applies to all elements that share the same parent and come after each other.
-Doesn't matter how they're placed inside their parent tag.

h2 ~ p {
  color: red;
}

<div>
  <h2>Not applied</h2>
  <p>CSS applied</p>
  <h2>Not applied</h2>
  <h3>Not applied</h3>
  <p>CSS applied</p>
</div>


# Child combinator

-Applies to all direct childs of a given parent.

div > p {
  color: red;
}

<div>
  <div>Not applied</div>
  <p>CSS applied</p>
  <div>Not applied</div>
  <article>
    <p>Not applied</p>
  </article>
  <p>CSS applied</p>    
</div>

# Descendant Combinator

-Styles all descendants.
-Doesn't matter if it's not a direct child (nested elements).

div p {
  color: red;
}

<div>
  <div>Not applied</div>
  <p>CSS applied</p>
  <div>Not applied</div>
  <article>
    <p>CSS applied</p>
  </article>
  <p>CSS applied</p>    
</div>

# BOX MODEL

From inside out:

1) Content => Can be some text or an image
2) Padding => The distance between the content and the border
3) Border => What encloses the content. From the border to the margin there's a given space
4) Margin => Space between the browser's window edges and itself

# Margin Collapsing
If you have to block elements sitting next to each other, their margins will collapse to one margin, the bigger one 'wins'.

# Block elements width

By default, the width of a block level element is 100%, this way it'll be taking up the total space posible out of its parent-container.

You can set the width of a block level element to a lower value, in order to see a change in its size.

# Block elements height

In case you want to set the height of an element to a certain size, it's better first to give its parent a set height too, if you don't do that, the parent-container will only take as much height as the elements inside it require for it to have. So, bottomline asign a set height to the container, this way the children isnide it will adjust it size depending on the container's size and also on the value you give to it.

# POSITIONING CAVEATS

An element's size grows depending on the border, and padding you set for it, since the whole element is made of content, padding, and border.

That being said, if you have a set height and width, and add the other properties, the element will add those values to its height and width, this way making the element bigger than expected.

If you want to override this behavior, you need to set, whether being with the * selector, onto the body, or even inside the element you want to keep its measures unchanged, the <box-sizing> property, and asign it the <border-box> value. This property will distribute the values you set for your height-width, padding, and border, accordingly to the current values you actually want to set to your element.

<box-sizing: border-box = height + padding + border>

# ABOUT POSITIONING INLINE-BLOCK DIFFERENT TYPE OF ELEMENTS ALIGNED HORIZONTALLY

# CALC FUNCTION
nav-bar {
width: calc(thisElementWidth - elementYouWantToBeAlignedWithWidth);
}

Let's suppose you have a title and a nav-bar you want to align. The title will have a set width, so you'll need to subtract the title's width from the nav-bar one. All this made within the width property of the nav-bar, and using the calc function as code above.

- <The white space you have between your two elements in your HTML code, will cause them to not be aligned;
- <You can place the second element right next to the first in your HTML, or you just need to asign a bigger value to the subtracting value in the calc function>

# CSS CLASSES AND ID'S

# classes 

You should use classes to group elements that will end having the same styles.

Multiple classes can be applied to the same element. If you change an element's styles within two classes, the one defined last in the css file, wil override the first one.

# Id's

Id's should be used only once in th webpage.

They're also good for linking to a specific part of your page, so you just create an id for any part within the webpage you want to scroll or visit, and ten asign an anchor tag with the href pointing to the id you created:

<a href="#main-section"></a>

<section id="main-section"></section>

# !IMPORTANT

You can use it to override any property.

# :NOT() PSEUDOCLASS

If you add this pseudoclass, what's inside the parenthesis, indicates the opposite of what you want to style.

<a:not(.active){color: red;
}>

In the code above, all <a> tags that don't have the active class, will have a red text color.

# FLOAT

Takes the element out of the document flow, this meaning if you asign float to an element, other elements will take its place.

We can keep the floating element space by adding a div with a class right after the element we want to float and with css you style it with:

.myClass {
  clear: clear-both;
}



# POSITIONING

There are various ways to style an element depending on what you want to acomplish, but there's one in particular that's set as default <Static>.

You can apply the position property to any element,no matter if it is a block or inline one.

When working with positioning you can use the 
# TOP, RIGHT, BOTTOM AND LEFT PROPERTIES.

They work just as the margin and padding ones, but they depend on the viewport (the size of the current browser's window).

# Position: fixed

It will take out the element from the document flow, so now it will be above every other elements. It depends on the viewport.

# Position: absolute

Regarding the document flow, it will also take the element out of it, but the elements positioning will depend:

If the element has an ancestor that has also a position applied, it will get positioned relative to that element.

If it has no ancestors with the position property, it will be positioned relative to the html element.

# Position: relative

It won't take the element out of the docuemtn flow. It will move it (top, right etc) from its current position to the one you're specifing in your styles.

# Position: sticky

It'll act as a mix between fixed and relative. When you're scrolling, the element will scroll up to a set (by you) distance and it will start being fixed when its border its over. Then, when the element is at the last of its parent's element position, it will scroll as usual.


# Z-index

This will make elements to stack on top of each other depending on the value you assign to it. The element with the higher value will be on top of the others (with lesser value).

Note: the default value of all elements is 0, and will only work if the position property is applied.

# Overflow: hidden

If you don't want for your element to be visible when its outside its parent (it was moved), you can use this property.

Note: when applying this only to the body, you'll notice it won't work, 'cause it transfers the property to the html element (a CSS default behavior). So what you need to do is to apply the property to the body and the html element as well,this way you'll be able to move the body's child and hide it when overflowing if you want.


# IMAGES AND BACKGROUNDS

# Background-size: {width, height, cover, contain}

It can be set to px or percentages. When you set the width to 100% and add no height value, it will try to adjust the image to its container's size.

# cover

Automatically sets the image to fill its container.

# cover

it ensures that the image its completely shown, but the image will not be adjusted to its container.

# Background-position: {x-axis, y-axis}

You decide how much of the image size to crop: from the left to right and top to bottom. 

# Styling images

Whenever you add an image to the page, it will be added with its original size. Also if the image is in a container, it doesn't matter if the container's size is changed, the image will still be the same size.

You need to select the image and then change its size. Also, if you set the image's container size and then apply a height of 100% to the first, it won't work. This is because the container is an inline element, so if you want to use percentages with your image's style, you need to apply the inline-block or inline properties.

# Linear Gradients

<Are treated like images>
<You can use directions and degrees>
<It allows you to use as many colors as you want>
<By setting a percentage after the color-choice, you can choose where the color is going to vanish>

# background-image: 
<linear-gradient ({direction [degrees]} | {color 1} {percentage} | {color2} {percentage}) >
<linear-gradient (to left top, red, blue) >

the above linear-gradient style will start a red gradient from the bottom-right part  of its container and will end at the left top with a blue color. 

# Radial gradient

<It's initially an ellipse>
<Set its first argument as 'circle', to get a circle>
<With the at keyword followed by top, right... you can set the gradient's initial position>
<After the circle keyword, you can define radial-gradient's size, with percentages>
<Once you've set the size, you can define the x and y axis position, with percentages (left to right, top to bottom)>

# background-image: 
<radial-gradient ({direction [degrees]} | {color 1} {percentage} | {color2}) >



# FILTERS


<Change the visual appearance of an element>




