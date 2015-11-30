
# Step 4 - Adding our 'Routes', Part 1 ( 'home' & 'findAll' )

With our backend model in place, it's now time to open some routes that the frontend client can interact with. The following are a list of actions a user can perform:

* view all donations
* Add a new donation
* Upvote a donation
* Delete a donation
* go home :-)

The actions map directly to several routes, which are described as follows:

* GET **/donations** - return a list of donations and associated metadata
* POST **/donations** - create a new donation
* GET **/donations/:id** - return an individual donation with associated metadata
* PUT **/donations/:id/upvote** - upvote a donation, notice we use the donation ID in the URL
* DELETE **/donations/:id** - delete a donation by ID

---
## Creating Our First Route - 'List All Donations'

To keep things organised we will be defining these routes in a **routes/donations.js** file. 

Let's begin by opening up the first route we listed, which should return a **JSON** list containing all donations. We start by creating a function (***findAll***) for retrieving donations in our **routes/donations.js** file.

```javascript
var donations = require('../models/donations');
var express = require('express');
var router = express.Router();

router.findAll = function(req, res) {
  // Return a JSON representation of our list
    res.json(donations);
}

module.exports = router;
```
We make sure we import **express** and have a handle to our donations model. By right, we should have some error handling in there, but we'll be optimistic!

Next, inside our **app.js** we need to define the actual route which will trigger the above function so first, add the following around line 9 or 10

```javascript
var donations = require('./routes/donations');
```
to import our own custom module and the add this around line 26/27

```javascript
app.get('/donations', donations.findAll);
```
to add the actual ***GET*** express route.

As we already have data in our Model, we can test it by pointing the browser at [http://localhost:3000/donations](http://localhost:3000/donations) and we should get back a json string of our data, like so


![](../images/lab4.step4.1.png)

---
## Creating Our Second Route - 'Go Home'

We don't necessarily need this route but it's a useful exercise so we're going to create a simple function (and route) to redirect the user back to the home page if any **GET** request other than those expected is processed.

Here's the function (***home***) to be added to our **routes/donations.js** file

```javascript
router.home = function(req, res) {
  //route to handle all angular requests
  res.sendFile('../public/index.ejs'); // load our public/index.ejs file
}
```
and our route for **app.js**

```javascript
app.get('*', donations.home);
```
