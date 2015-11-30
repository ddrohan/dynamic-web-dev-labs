#Step 3 - Creating our Database Schema

Our first step in making a persistent data store is to configure our data models. To do this, we are going to be adding a schema layer on top of **MongoDB** using a nice library called ***Mongoose***. Before we begin, let's make sure our **MongoDB** server is running.

If Mongo isn't running on your machine, enter this into your terminal:

```
mongod
```
and to run a mongo client

```
mongo
```

We connect to our local MongoDB instance by adding the following code into our donations.js **routes** file:

```javascript
var mongo = require('mongodb');
var mongoose = require('mongoose'); 

...

mongoose.connect('mongodb://localhost:27017/donationsdb');
```

(It's probably a good idea to remove our javascript list altogether at this point as we don't need it.)

This will open a connection with the ***donationsdb*** database running on our Mongo server. Now we can modify our existing model and introduce a database schema.

---
## Creating a Schema with Mongoose

In our **models/** directory edit **donations.js** and add the following code:

```javascript
var mongoose = require('mongoose');

var DonationSchema = new mongoose.Schema({
  paymenttype: String,
  amount: Number,
  upvotes: {type: Number, default: 0}
});

module.exports = mongoose.model('Donation', DonationSchema);
```
Here we've defined a model called ***Donation*** with several attributes corresponding to the type of data we'd like to store. We've declared our upvotes field to be initialized to 0.

Next we register that model with the global mongoose object we imported using require() so that it can be used to interact with the database anywhere else mongoose is imported.

**It is strongly recommended to run your web server at this point, to ensure everything is configured correctly and before we go ahead an modify our routes to interact with the database.**

So as before, go ahead and fire up the server - but make sure your mongodb is running first.

Did you get an Error?? (You probably did...)

Did you install the **'mongoose'** and **'mongodb'** modules?? (You probably didn't!! )

run these commands and then try again

```
npm install mongoose
```
and then

```
npm install mongodb
```
and if you check your running mongodb instance, you should see that a connection has been accepted, something like this

![](../images/lab5.step3.1.jpg)
