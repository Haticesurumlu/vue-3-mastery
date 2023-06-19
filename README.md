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
 
Now, if inStock is false, we’ll see “Out of Stock” gets rendered to the page.



Show and Hide
It’s worth noting that you don’t always need to pair v-if with v-else. There are plenty of use cases where you don’t need a fallback element to render. However, in these cases, it is sometimes a better option to use the v-show directive.
 
The v-show directive is used for toggling an element’s visibility instead of adding and removing the element from the DOM entirely, like v-if does.
As you might imagine, this is a more performant option if you have something that’s toggling off and on the screen often. We can verify this by setting inStock to false and viewing the element in the browser’s Developer Tools. When v-show is used, we can see that the element is still present in the DOM, but it’s now hidden with an inline style of display: none; added to it.

 









Chained Conditional Logic

📄main.js
 

📄index.html
 

📄index.html
 

