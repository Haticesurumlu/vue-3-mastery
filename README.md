# vue-3-mastery


### Touring the Starting Code

To take a tour of the starting code, you’ll see we have an assets directory. Inside of there, there’s a directory for images. We’ve got one for blue socks, and green socks. We also have a CSS file for all of our styles.


### Creating a Vue App

To display our data within our HTML, we’ll first have to create a Vue app. In our main.js file, we’ll create our app with:

📄main.js


As an argument, we’re going to pass in an object and add a data property. This is going to be a function that returns another object, where we’ll store our data. In here, we’ll add product as a data item.

📄main.js


📄index.html


### Mounting Our App
We’ve created our app, we need to mount the app that we just created, into our DOM. We’ll do that inside of a script tag, in our index.html file.

📄index.html


### Displaying the Data

Now that we’ve created, imported and mounted out Vue app, we can now start displaying the data that lives within it.

To render the product data within the h1, we’ll write:

### Understanding the Vue Instance

When we created our Vue app, we passed in the options object, which allowed us to add some optional properties to configure the application. Doing this creates our Vue instance, the heart of our Vue application, which powers everything.

📄main.js


By importing this app, and mounting it to the DOM, we’ve essentially plugged the app into our DOM, giving our HTML a direct line into the app. This way, our template code can access options from the app, such as its data.



If you’re wondering what’s happening with this double curly brace syntax, you can imagine it like a phone, which has access to a phone within our Vue app. From our template, we’re able to ask the app, “Hey, what’s the value of product?” And the app responds, “Socks.” When the page renders, we see “Socks” display on the page.


### Vue’s Reactivity

What would happen if we changed the value of product from “Socks” to “Boots”?

📄main.js


Because of how Vue works, the h1’s expression that is relying upon product would automatically receive that new value, and our DOM would update to display “Boots”.

📄index.html



# Attribute Binding

📄index.html


📄main.js




Now we’re ready to add an img element in the template.

📄index.html



### Introducing Attribute Binding
To create a bond between an HTML element’s attribute and a value from your Vue app’s data, we’ll use a Vue directive called v-bind.

📄index.html

Conditional Rendering
📄index.html

📄main.js



The v-if directive


We can add the v-if directive onto an element to render it based upon a condition, like so.
 
Now, this element will render only if inStock is truthy.
We can combine the v-if directive with its sister directive v-else to display another element as the fallback if the first condition turns out to be falsey.

📄index.html

 
Now, if inStock is false, we’ll see “Out of Stock” gets rendered to the page.



Show and Hide
It’s worth noting that you don’t always need to pair v-if with v-else. There are plenty of use cases where you don’t need a fallback element to render. However, in these cases, it is sometimes a better option to use the v-show directive.

The v-show directive is used for toggling an element’s visibility instead of adding and removing the element from the DOM entirely, like v-if does.
As you might imagine, this is a more performant option if you have something that’s toggling off and on the screen often. We can verify this by setting inStock to false and viewing the element in the browser’s Developer Tools. When v-show is used, we can see that the element is still present in the DOM, but it’s now hidden with an inline style of display: none; added to it.

 









Chained Conditional Logic

📄main.js
 

📄index.html
 

📄index.html
 

### List Rendering
#### Our Goal
Render HTML lists from an array in our data.

Looping through data arrays
In the starting code, we now have an array of details.


📄main.js

The question now is: how do we display this data as a list?
We’ll start by creating an unordered list in our index.html. On the li inside of it, we’ll add another Vue directive: v-for

📄index.html
Inside the v-for expression, we wrote: detail in details. Here, details refers to the details array in our data, and detail is the alias for the current element from that array, as we’re looping through it to print out a new li.

So far so good, but how is v-for actually working?

### Product Variant Colors
📄main.js


We now have an array that contains an object for each variant of our product. Each product variant has an id, and a color. So for our next task, we’ll print out each variant color, and use the id to help Vue keep track of our list items.


📄index.html


### Key Attribute: An essential for list items

📌 By saying :key="variant.id", we’re using the shorthand for v-bind to bind the variant’s id to the key attribute. This gives each DOM element a unique key so that Vue can grasp onto the element and not lose track of it as things update within the app.
This provides some performance improvements, and later down the line, if you’re doing something like animating your elements, you’ll find that the key attribute really helps Vue effectively manage your elements as they move around the DOM.


# Event Handling
📄index.html
📄main.js
#### Our Goal
We want to be able to click the button and increment the value of cart.
Listening for Events
In order to know when the button is clicked, we need to be listening for events on that element, specifically click events. We can achieve this by using another Vue directive: v-on.

📄index.html


Here, we are telling v-on what type of event to listen for: a click. Inside the quotes, we place the logic (or method name) we want to run when that event happens.

If we write v-on:click="cart += 1", we’ll increment the value of cart by 1, when a click event happens.

#### Triggering a method
Because the logic cart += 1 is very simple, we could keep it in-line on the button element, like we have it. But often, we need to trigger more complex logic. In those situations, we can add a method name to fire when the event happens. So let’s do that now.

📄index.html


### Understanding v-on
Let’s take a deeper look into how this event handling is working.

By adding v-on to an element, we’re essentially giving it an ear that can listen for events. In this case, we’ve specified that we’re listening for click events. When a click happens, the addToCart method runs, which as we just saw, takes the value of cart and increments it by one.

### A shorthand for v-on
As you can imagine, listening for events on your elements is super common. Just like how v-bind had a shorthand (:), v-on has a shorthand: @

So our code could be simplified to:

📄index.html
### Another Example: Mouseover Events

Wouldn’t it be nice if, when we hovered our mouse over “green” and “blue”, we triggered an update of the image to the green and blue image, respectively? Let’s add the ability to listen for mouseover events (Vue’s term for “hover”) on these color names.

Because we want to update the image that we’re displaying when we mouse over the variant colors, I’ve added a new property to each variant object.

📄main.js

Now each variant has an image path for the green and blue socks, respectively. We’re ready to add a listener for mouseover events on the variant color div.

📄main.js

When a mouseover event happens, we’re triggering the updateImage method, passing in the image path of each variant. That method looks like this:


# Class & Style Binding
### Style Binding

📌 Let’s create green and blue circles that we can hover on. We can achieve this by using style binding.
First, to style our divs like circles, we’ll we need to add a new class .color-circle to the variant div.

📄index.html


📄styles.css

Now that we’ve got that out of the way, we can move on to the actual style binding. Just like it sounds, we want to bind styles to the variant divs. We do so by using v-bind (or its shorthand: :) on the style attribute, and binding a style object to it.

📄index.html


Here, we’re setting the divs’ backgroundColor equal to the variant.color. So instead of printing out those strings, “green” and “blue”, we’re using them to set the background color of our circles.


😍 Cool! Now let’s understand, on a deeper level, how this is all working.

### Understanding Style Binding

📄index.html


That style object has the CSS property of backgroundColor, and we’re setting that equal to whatever the variant color is at the time of that v-for iteration.

In the first iteration, variant.color is "green"

Vue takes that information and converts it into the code:style="{ backgroundColor: green }"

Then prints out a green background circle.


### Camel vs Kebab
📌 There are some important things to consider when using style binding like this.

Inside of this expression, remember that this style object is all JavaScript. That’s why I used camelCase in the property name. If I had said background-color, that - would’ve been interpreted as a minus sign. But we’re not doing any math here. We’re setting a CSS property name.

So since we’re in this JavaScript object, we have to use camelCased unless we want to use ‘kebab-cased’ in quotes to avoid the mathematical misinterpretation, like so:

✔ Both options will work, as long as you remember your quotation marks.

### Style Binding: Objects
Sometimes you might want to add a bunch of styles to an element, but adding them all in-line could get messy. In these situations, we can bind to an entire style object that lives within our data.


### Class Binding
Let's disable the Add to Cart button when inStock is false AND make the button appear disabled, using class binding.
To get this started, we’ll use the shorthand for v-bind on the disabled attribute to add that attribute whenever our product is not in stock.

📄index.html


Now, whenever inStock is false and we click the Add to Cart button, nothing will happen since it’s disabled. But the button still appears active, which is misleading to our users. So let’s use class binding to add a disabledButton class as well, whenever inStock is false.

You’ll see in our CSS file that we already have this disabledButton class, which sets the background-color to gray and makes the cursor not-allowed.


📄styles.css


To apply this class conditionally, based on the value of inStock, we’ll use the shorthand for v-bind on the class attribute, and use an expression that adds the disabledButton class (or not) whenever !inStock.

📄index.html



### Multiple Class Names
When getting started with class binding, there are some things to note. For example, what happens when we already have an existing class and we want to conditionally add another class based on a data value?

For example, if we already have the color-circle class on this div, and we conditionally add the active class, how will this look?



Those classes are going to be combined like so:



### Ternary Operators

A helpful tool that class binding gives us is the ability to use in-line ternary operators to add different classes based upon a condition.



# Computed Properties
### Our Goal
Update both the variant image AND whether it’s in stock or not, using computed properties.
### A Simple Computed Property
📄main.js


What if we wanted to combine the brand and the product, in our template? We could do that within an expression like so:
📄index.html




If we checked this out in the browser, we’d see “Vue mastery Socks” displayed. But wouldn’t it be neat if, instead of handling this logic in the inner HTML, our app had the ability to compute that value for us? For example, taking the brand and the product, adding them together, and returning that new value.

😍 Computed properties are exactly like they sound: properties we can add to a Vue app that compute values for us. They help us keep computational logic out of the template and give us performance improvements that we’ll cover soon. For now, let’s turn this simple example into a computed property. We’ll alter the h1’s expression like so:

📄index.html


Now, title is the name of a computed property that we’ll create now. First, we’ll add the computed option to the app, just below our methods, then create the title property.

📄main.js



If we check out the browser, we’ll still see “Vue Mastery Socks” displayed, except now we’ve abstracted that computational logic out of the template and contained it neatly on the options object.

But how exactly are computed properties working? Let’s take a deeper look.

### Think of them like a Calculator
I like to think of computed properties kind of like a calculator, because they calculate or compute values for us. This computational calculator takes our values, brand and product, adds them together, and gives us the result.

Like I mentioned earlier, computed properties provide us a performance improvement. This is because they cache the calculated value. The value ('Vue Mastery Socks') gets stored away and only updates when it needs to, when one of its dependencies change. For example, if the brand were to change from 'Vue Mastery' to 'Node Mastery', our computed property would receive that new brand dependency, then recalculate and return the new value: 'Node Mastery Socks'

### Computing Image & Quantity
Heading back into our code, let’s add a new quantity property to our variant objects.

📄main.js


Notice how the green socks have a quantity of 50 while the blue socks have 0. In other words, the green socks are in stock and the blue socks are out of stock. However, we’re currently displaying “In stock” or “Out of stock” based on the inStock data value, which no longer reflects the truth about our product and its variant quantities. So we’ll want to create a computed property we can use to display “In stock” or “Out of stock” based on these new quantities.

To get started, remember how we updated the variant image, based on which variant color is moused over? Instead of that mouseover event triggering the updateImage() method, we’re going to have it trigger a new method called updateVariant().

📄index.html


Notice how we’re passing in the index of the currently hovered-on variant: updateVariant(index). We got access to that index by adding it as a second parameter in our v-for directive:

v-for="(variant, index) in variants"

Why are we passing in the index? We’re going to use it to tell our app which variant is currently hovered on, so it can use that information to trigger the updating of both the image AND whether that variant is in stock or not.

We’ll add a new data property to our app, which will be updated to equal that index
📄main.js


Our updateVariant() method will set the selectedVariant’s value equal to the index of the currently hovered-on variant.

📄main.js

Now, we’ve implemented a way for our app to know which product variant is being engaged with, and we’re able to use that information to trigger the computing of which image to show and whether to show “In stock” or “Out of stock”, based on which variant the user is moused over.

We’re now ready to delete image and inStock from our data, and replace those with computed properties of the same names.

📄main.js



So how do we grab the variant image and quantity? That will look like this:

📄main.js


We’re targeting the first or second element of our variants array based off the selectedVariant, which is either 0 or 1, depending on which variant color circle is hovered on. Then we just use dot notation to grab the image off that variant.

The logic for computing inStock is nearly identical:

📄main.js



Now inStock is no longer a data property; it’s the new computed property.



