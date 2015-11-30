# Step 2 - Setup

![](../lab01/images01/lab01s01.png)

We're going to build our first Node/Express web app using **WebStorm**, so (assuming you already have it installed) launch your WebStorm IDE and create a new Node/Express Project as follows;

![](../lab01/images01/lab01s02.png)

and you should get something like this

![](../lab01/images01/lab01s03.png)

![](../lab01/images01/lab01s04.png)

and make sue you choose **EJS** as the templating option (more on this later)

![](../lab01/images01/lab01s05.png)

![](../lab01/images01/lab01s06.png)

![](../images/lab3.step2.1.png)

As you can see, this will auto-generate a node web app, creating all the necessary folders and files we need to get started. *--ejs* specifies we want to use the **Embedded JavaScript Templates** (instead of the default which is Jade) and *--save* just ensures the dependencies are added to our *package.json* file (more on this later).

Now, follow the instructions to install the dependencies, and you should get something like this (+ a lot more!)

![](../images/lab3.step2.2.png)

And once you've dragged it into Sublime Text you should have something like this

![](../images/donationweb-3.0.start.png)

Finally, navigate to your **donationweb-3.0** folder and type the following to launch the server

```
npm start

```

if everything goes to plan you should be able to visit [http://localhost:3000](http://localhost:3000) and see the following

![](../images/lab3.step2.3.png)

The next step will involve bringing in our angular files to get the front-end implemented.