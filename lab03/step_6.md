# Step 6 - Updating our 'Views'


If you go ahead and try and delete or upvote a 'donation' you'll probably get some kind of error - and it's to do with the parameter we're passing to our 'delete' and 'incrementVotes' functions on the client side (in our .ejs file) - it's the wrong one.

To fix this, you first need to identify what is the ***right*** parameter to pass so you need to find out what is being sent in the response JSON string to the 'List All Donations' request.

Type the following in your browser and see can you work it out?

```
http://localhost:3000/donations
```
Now, you simply need to change the current parameter being passed to the one that ***mongo*** uses to uniquely identify an object in its collections.

Restart your server and give it another go and see how you get on?