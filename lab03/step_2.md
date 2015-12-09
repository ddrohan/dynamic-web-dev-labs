# Step 2 - Setup

First thing you should do is download the starter code (or the solution to the previous lab) **[here](../zips/donationweb-1.0.solution.zip)** and then extract it to your single parent folder for all your web app projects you created for previous labs. 

Rename the extracted folder, (or copy your own version) to **donationweb-2.0**

Open your **donationweb-2.0** web app (in WebStorm) 

![](../lab03/images/lab02s213.png)

and then change your 'title' like so

![](../lab03/images/lab02s214.png)

and launch it.

You may not get any errors, but you should probably reconfigure your project (as it's a copy) and fix the **node modules** path as follows:

Open your preferences and navigate to the **Library** settings

![](../lab03/images/lab02s211.png)

and

update your **node_modules** path to point to the current project

![](../lab03/images/lab02s212.png)

Launch it again, if everything goes to plan you should be able to visit [http://localhost:3000](http://localhost:3000) and you should see the following


![](../lab03/images/lab02s215.png)


The next thing to do is to add the **mongod** and **mongoose** module dependencies to our project. Launch the terminal window 

![](../lab03/images/lab02s216.png)

and run the following commands


~~~
npm install mongoose
~~~

and

~~~
npm install mongodb
~~~

Your project should now look like this

![](../lab03/images/lab02s217.png)

The last step in our 'Setup' is to kick off our localhost mongodb server and insert a few 'Donations' so we can test our refactored 'findAll' function (next step).

Open up a terminal window and launch the mongodb server

![](../lab03/images/lab02s201.png)

Open another, separate window and launch the client

![](../lab03/images/lab02s202.png)

In the client window, create/switch to the 'donationsdb' database

![](../lab03/images/lab02s203.png)

Insert a few records and make sure you name your collection **donations** and **NOT** donationsdb, (as in the screenshots), so you'll be saying something like


~~~
db.donations.find()
~~~

etc.

![](../lab03/images/lab02s204.png)

'Find' all the donations, just to confirm they exist.

![](../lab03/images/lab02s205.png)

![](../lab03/images/lab02s206.png)

![](../lab03/images/lab02s207.png)

![](../lab03/images/lab02s208.png)

![](../lab03/images/lab02s209.png)

![](../lab03/images/lab02s210.png)