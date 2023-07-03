# vue-3-mastery


### Touring the Starting Code

To take a tour of the starting code, you’ll see we have an assets directory. Inside of there, there’s a directory for images. We’ve got one for blue socks, and green socks. We also have a CSS file for all of our styles.

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/4d1f414b-6bf9-4a74-88d3-5fea55dc3cad)

### Creating a Vue App

To display our data within our HTML, we’ll first have to create a Vue app. In our main.js file, we’ll create our app with:

📄main.js

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/03df8a9b-456e-4ee0-97b4-d8c157ca6b3f)

As an argument, we’re going to pass in an object and add a data property. This is going to be a function that returns another object, where we’ll store our data. In here, we’ll add product as a data item.

📄main.js

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/b8488ad8-8418-4287-8d92-5e15046d6e50)

📄index.html

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/f55c5eb5-1604-4bfd-b982-9eeeb3161b70)

### Mounting Our App
We’ve created our app, we need to mount the app that we just created, into our DOM. We’ll do that inside of a script tag, in our index.html file.

📄index.html

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/56caf9c5-de68-44a9-984c-114671542539)

### Displaying the Data

Now that we’ve created, imported and mounted out Vue app, we can now start displaying the data that lives within it.

To render the product data within the h1, we’ll write:

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/7683a6f5-8036-4bff-9a92-6347b0f44b7c)

### Understanding the Vue Instance

When we created our Vue app, we passed in the options object, which allowed us to add some optional properties to configure the application. Doing this creates our Vue instance, the heart of our Vue application, which powers everything.

📄main.js

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/35ef068c-53f4-4f7c-94dd-b032f5af88cc)

By importing this app, and mounting it to the DOM, we’ve essentially plugged the app into our DOM, giving our HTML a direct line into the app. This way, our template code can access options from the app, such as its data.


![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/e3627d95-9df1-43bc-a76e-7b5f05149417)

If you’re wondering what’s happening with this double curly brace syntax, you can imagine it like a phone, which has access to a phone within our Vue app. From our template, we’re able to ask the app, “Hey, what’s the value of product?” And the app responds, “Socks.” When the page renders, we see “Socks” display on the page.


### Vue’s Reactivity

What would happen if we changed the value of product from “Socks” to “Boots”?

📄main.js

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/7fc28faa-77be-457e-aae6-0b31a838c4ea)

Because of how Vue works, the h1’s expression that is relying upon product would automatically receive that new value, and our DOM would update to display “Boots”.

📄index.html

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/9e15b14a-91e9-430e-9fe1-e4ff2b4bc9ca)


# Attribute Binding

📄index.html

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/a8fe061d-da64-4d55-a8dd-eaf56f977847)

📄main.js



![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/5f909930-c2ca-48f3-afa2-b988626f2410)

Now we’re ready to add an img element in the template.

📄index.html

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/60731423-77d4-4350-b195-790c56a22685)


### Introducing Attribute Binding
To create a bond between an HTML element’s attribute and a value from your Vue app’s data, we’ll use a Vue directive called v-bind.

📄index.html
![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/ba97618a-917e-4e13-915c-be9424e034c0)

Conditional Rendering
📄index.html
 ![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/b18d3fc1-ee56-4b61-9d8a-af44e39b0c4f)

📄main.js
 ![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/c7ae642e-ff67-43bd-94e7-68e8b92a715a)


The v-if directive
![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/f4d7ebe4-6ba0-4055-a5a0-c77b7f145f7e)

We can add the v-if directive onto an element to render it based upon a condition, like so.
 
Now, this element will render only if inStock is truthy.
We can combine the v-if directive with its sister directive v-else to display another element as the fallback if the first condition turns out to be falsey.

📄index.html
![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/acee7dc1-28bd-4034-a804-16dd2437f809)

 
Now, if inStock is false, we’ll see “Out of Stock” gets rendered to the page.



Show and Hide
It’s worth noting that you don’t always need to pair v-if with v-else. There are plenty of use cases where you don’t need a fallback element to render. However, in these cases, it is sometimes a better option to use the v-show directive.
 ![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/74990144-6a2a-4b2e-9610-017a142d0afa)

The v-show directive is used for toggling an element’s visibility instead of adding and removing the element from the DOM entirely, like v-if does.
As you might imagine, this is a more performant option if you have something that’s toggling off and on the screen often. We can verify this by setting inStock to false and viewing the element in the browser’s Developer Tools. When v-show is used, we can see that the element is still present in the DOM, but it’s now hidden with an inline style of display: none; added to it.

 



![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/ca8bbf0d-6174-4c6e-9f51-78ae326e10bf)






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

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/3af98814-daa7-4c3d-9aa9-2d7bee97ec96)
The question now is: how do we display this data as a list?
We’ll start by creating an unordered list in our index.html. On the li inside of it, we’ll add another Vue directive: v-for

📄index.html
![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/c56b69bb-927b-4a53-9bce-92d912b54ad3)
Inside the v-for expression, we wrote: detail in details. Here, details refers to the details array in our data, and detail is the alias for the current element from that array, as we’re looping through it to print out a new li.

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/d2746801-1d66-42a1-90b2-60a785c634f2)
So far so good, but how is v-for actually working?

### Product Variant Colors
📄main.js

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/68f3bf8e-d849-4dc0-a5a8-a9fb13d60570)

We now have an array that contains an object for each variant of our product. Each product variant has an id, and a color. So for our next task, we’ll print out each variant color, and use the id to help Vue keep track of our list items.


📄index.html
![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/ca7eb5dc-a9dc-4fc9-8eb9-17adbf910908)


### Key Attribute: An essential for list items

📌 By saying :key="variant.id", we’re using the shorthand for v-bind to bind the variant’s id to the key attribute. This gives each DOM element a unique key so that Vue can grasp onto the element and not lose track of it as things update within the app.
This provides some performance improvements, and later down the line, if you’re doing something like animating your elements, you’ll find that the key attribute really helps Vue effectively manage your elements as they move around the DOM.


# Event Handling
📄index.html
![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/c0988f97-e15f-4fa8-8f86-e74bd6c354b6)
📄main.js
![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/bde1b0d0-9670-4f0f-8688-6dc63bcd518d)
#### Our Goal
We want to be able to click the button and increment the value of cart.
Listening for Events
In order to know when the button is clicked, we need to be listening for events on that element, specifically click events. We can achieve this by using another Vue directive: v-on.

📄index.html

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/d20ba599-657d-4bf1-b03c-c123e1821240)

Here, we are telling v-on what type of event to listen for: a click. Inside the quotes, we place the logic (or method name) we want to run when that event happens.

If we write v-on:click="cart += 1", we’ll increment the value of cart by 1, when a click event happens.

#### Triggering a method
Because the logic cart += 1 is very simple, we could keep it in-line on the button element, like we have it. But often, we need to trigger more complex logic. In those situations, we can add a method name to fire when the event happens. So let’s do that now.

📄index.html
![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/0dbc2fd1-c6af-403d-8320-8921dcdecb20)
![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/23aecb7c-ecec-4e64-bc4c-449a771c26c0)

### Understanding v-on
Let’s take a deeper look into how this event handling is working.
![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/ad333986-5416-4359-9438-a3bd2fc11755)

By adding v-on to an element, we’re essentially giving it an ear that can listen for events. In this case, we’ve specified that we’re listening for click events. When a click happens, the addToCart method runs, which as we just saw, takes the value of cart and increments it by one.

### A shorthand for v-on
As you can imagine, listening for events on your elements is super common. Just like how v-bind had a shorthand (:), v-on has a shorthand: @

So our code could be simplified to:

📄index.html
![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/ff761983-2b6a-4a10-9ed5-e570ccad3ada)
### Another Example: Mouseover Events

Wouldn’t it be nice if, when we hovered our mouse over “green” and “blue”, we triggered an update of the image to the green and blue image, respectively? Let’s add the ability to listen for mouseover events (Vue’s term for “hover”) on these color names.

Because we want to update the image that we’re displaying when we mouse over the variant colors, I’ve added a new property to each variant object.

📄main.js

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/4a969453-68d9-4a28-bbac-0ea03edc6152)
Now each variant has an image path for the green and blue socks, respectively. We’re ready to add a listener for mouseover events on the variant color div.

📄main.js
![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/f9503cb4-e314-4526-983f-3a3e64f62228)

When a mouseover event happens, we’re triggering the updateImage method, passing in the image path of each variant. That method looks like this:

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/bc69ba8a-5c5d-4c0f-a493-273e1b9aadd8)

# Class & Style Binding
### Style Binding

📌 Let’s create green and blue circles that we can hover on. We can achieve this by using style binding.
First, to style our divs like circles, we’ll we need to add a new class .color-circle to the variant div.

📄index.html

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/4acac33e-d013-4fe6-a849-f79771fe9cae)

📄styles.css

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/28c967a3-605d-4b03-b430-6e68977732c4)
Now that we’ve got that out of the way, we can move on to the actual style binding. Just like it sounds, we want to bind styles to the variant divs. We do so by using v-bind (or its shorthand: :) on the style attribute, and binding a style object to it.

📄index.html

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/1ccfa33b-0865-4c91-b700-af86921851a5)

Here, we’re setting the divs’ backgroundColor equal to the variant.color. So instead of printing out those strings, “green” and “blue”, we’re using them to set the background color of our circles.

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/bb44e413-1c4f-420c-be14-23c25239e55a)

😍 Cool! Now let’s understand, on a deeper level, how this is all working.

### Understanding Style Binding

📄index.html

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/cef1cea5-2a3d-49e5-bd9e-7ad04beecec7)

That style object has the CSS property of backgroundColor, and we’re setting that equal to whatever the variant color is at the time of that v-for iteration.

In the first iteration, variant.color is "green"

Vue takes that information and converts it into the code:style="{ backgroundColor: green }"

Then prints out a green background circle.

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/d542a43a-2bf0-40e4-8a49-05e00c2f8a7c)

### Camel vs Kebab
📌 There are some important things to consider when using style binding like this.
![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/8ca33622-7192-489c-a1d7-e972c2490efc)

Inside of this expression, remember that this style object is all JavaScript. That’s why I used camelCase in the property name. If I had said background-color, that - would’ve been interpreted as a minus sign. But we’re not doing any math here. We’re setting a CSS property name.

So since we’re in this JavaScript object, we have to use camelCased unless we want to use ‘kebab-cased’ in quotes to avoid the mathematical misinterpretation, like so:
![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/5913dc72-f0b7-4717-93c9-3a16bde466c6)

✔ Both options will work, as long as you remember your quotation marks.

### Style Binding: Objects
Sometimes you might want to add a bunch of styles to an element, but adding them all in-line could get messy. In these situations, we can bind to an entire style object that lives within our data.

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/e5c13487-68fe-4a68-8ecd-384a77171920)

### Class Binding
Let's disable the Add to Cart button when inStock is false AND make the button appear disabled, using class binding.
To get this started, we’ll use the shorthand for v-bind on the disabled attribute to add that attribute whenever our product is not in stock.

📄index.html

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/1aa4315b-ba15-4ab6-a31e-68ff5cd35958)

Now, whenever inStock is false and we click the Add to Cart button, nothing will happen since it’s disabled. But the button still appears active, which is misleading to our users. So let’s use class binding to add a disabledButton class as well, whenever inStock is false.

You’ll see in our CSS file that we already have this disabledButton class, which sets the background-color to gray and makes the cursor not-allowed.


📄styles.css

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/cdbf7df6-e28b-4265-9f76-fd6dd231ba67)

To apply this class conditionally, based on the value of inStock, we’ll use the shorthand for v-bind on the class attribute, and use an expression that adds the disabledButton class (or not) whenever !inStock.

📄index.html

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/7e4b5ccb-b41b-4ce7-8136-bb43c2b47044)

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/93ddb07e-db53-453b-a9a1-33cf633095b3)

### Multiple Class Names
When getting started with class binding, there are some things to note. For example, what happens when we already have an existing class and we want to conditionally add another class based on a data value?

For example, if we already have the color-circle class on this div, and we conditionally add the active class, how will this look?

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/27f71ef3-d2ea-421e-9733-7ad9b1775b12)


Those classes are going to be combined like so:

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/c1233bd3-a83f-4326-97c6-ebd988d7f26f)


### Ternary Operators

A helpful tool that class binding gives us is the ability to use in-line ternary operators to add different classes based upon a condition.

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/433d9288-93a6-46b4-bd1a-98cad96cefc7)


# Computed Properties
### Our Goal
Update both the variant image AND whether it’s in stock or not, using computed properties.
### A Simple Computed Property
📄main.js


![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/96ab0ab1-f20d-4594-9dbf-487b4c80da1d)
What if we wanted to combine the brand and the product, in our template? We could do that within an expression like so:
📄index.html


![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/a681d9a7-dd3d-4483-81bc-27be82e02481)

