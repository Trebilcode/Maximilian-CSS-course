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