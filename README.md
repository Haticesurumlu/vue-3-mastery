# vue-3-mastery


###Touring the Starting Code

To take a tour of the starting code, you’ll see we have an assets directory. Inside of there, there’s a directory for images. We’ve got one for blue socks, and green socks. We also have a CSS file for all of our styles.
![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/4d1f414b-6bf9-4a74-88d3-5fea55dc3cad)

###Creating a Vue App

To display our data within our HTML, we’ll first have to create a Vue app. In our main.js file, we’ll create our app with:

📄main.js
![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/03df8a9b-456e-4ee0-97b4-d8c157ca6b3f)

As an argument, we’re going to pass in an object and add a data property. This is going to be a function that returns another object, where we’ll store our data. In here, we’ll add product as a data item.

📄main.js

![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/b8488ad8-8418-4287-8d92-5e15046d6e50)

📄index.html
![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/f55c5eb5-1604-4bfd-b982-9eeeb3161b70)

Mounting Our App
We’ve created our app, we need to mount the app that we just created, into our DOM. We’ll do that inside of a script tag, in our index.html file.

📄index.html
![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/56caf9c5-de68-44a9-984c-114671542539)

###Displaying the Data

Now that we’ve created, imported and mounted out Vue app, we can now start displaying the data that lives within it.

To render the product data within the h1, we’ll write:
![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/7683a6f5-8036-4bff-9a92-6347b0f44b7c)

###Understanding the Vue Instance

When we created our Vue app, we passed in the options object, which allowed us to add some optional properties to configure the application. Doing this creates our Vue instance, the heart of our Vue application, which powers everything.

📄main.js
![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/35ef068c-53f4-4f7c-94dd-b032f5af88cc)
By importing this app, and mounting it to the DOM, we’ve essentially plugged the app into our DOM, giving our HTML a direct line into the app. This way, our template code can access options from the app, such as its data.


![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/e3627d95-9df1-43bc-a76e-7b5f05149417)

If you’re wondering what’s happening with this double curly brace syntax, you can imagine it like a phone, which has access to a phone within our Vue app. From our template, we’re able to ask the app, “Hey, what’s the value of product?” And the app responds, “Socks.” When the page renders, we see “Socks” display on the page.


###Vue’s Reactivity

What would happen if we changed the value of product from “Socks” to “Boots”?

📄main.js
![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/7fc28faa-77be-457e-aae6-0b31a838c4ea)

Because of how Vue works, the h1’s expression that is relying upon product would automatically receive that new value, and our DOM would update to display “Boots”.

📄index.html
![image](https://github.com/Haticesurumlu/vue-3-mastery/assets/71832100/9e15b14a-91e9-430e-9fe1-e4ff2b4bc9ca)


