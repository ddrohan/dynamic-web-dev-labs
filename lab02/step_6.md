
# Step 6 - Adding our 'Routes', Part 2 ('Add', 'Delete' & 'UpVotes')

Recall our routes, described as follows:

* GET **/donations** - return a list of donations and associated metadata
* POST **/donations** - create a new donation
* GET **/donations/:id** - return an individual donation with associated metadata
* PUT **/donations/:id/upvote** - upvote a donation, notice we use the donation ID in the URL
* DELETE **/donations/:id** - delete a donation by ID

We've already implemented the first one, so now let's have a go at 

* Adding a new donation
* Deleting a donation and
* 'Upvoting' a donation

We'll leave finding an individual donation for the final lab - Lab 5.

---
## Creating Our 'Add' Route - 'addDonation'
Similar to the previous step, we start by creating a function (***addDonation***) for adding a single donation in our **routes/donations.js** file

```javascript
router.addDonation = function(req, res) {
    //Add a new donation to our list
    var id = Math.floor((Math.random() * 1000000) + 1); //Randomly generate an id
    // parameters to store
    // id (for id)
    // req.body.paymenttype (for paymenttype)
    // req.body.amount (for amount)
    // 0 (for upvotes)
    
    donations.push(/*fill in missing code here */);

    res.json({ message: 'Donation Added!'});
}
```
Notice we only return a json message confirming we've added the donation.

Next, inside our **app.js** we need to define the actual route which will trigger the above function so keeping in mind the route is **/donations** with a **POST** request, see can you make the necessary additions?

---
## Creating Our 'Delete' Route - 'deleteDonation'
Again, we start with the function in our **routes/donations.js** file

```javascript
router.deleteDonation = function(req, res) {
    //Delete the selected donation based on its id
    var donation = getByValue(donations,req.params.id);
    var index = donations.indexOf(donation);
    donations.splice(index, 1);  

    router.findAll(req,res); //CAN YOU EXPLAIN WHY THIS IS NEEDED?
}
```
and update our **app.js** accordingly

```javascript
app.delete('/donations/:id', donations.deleteDonation);
```

We also need to write our own 'lookup' function to find a particular donation so make sure you add the following to your **routes/donations.js** file but be sure you understand how it works....

```javascript
function getByValue(arr, id) {

  var result  = arr.filter(function(o){return o.id == id;} );

  return result ? result[0] : null; // or undefined
}
```

---
## Creating Our 'Upvote' Route - 'incrementVotes'

Finally, here's what we need to implement the 'Upvote' route

**routes/donations.js**

```javascript
router.incrementUpvotes = function(req, res) {
    //Add 1 to upvotes property of the selected donation based on its id
    var donation = getByValue(donations,req.params.id);
    donation.upvotes += 1;

    router.findAll(req,res);      
}
```

**app.js**

```javascript
app.put('/donations/:id/votes', donations.incrementUpvotes);
```

So that's the Server-Side of things done!