# Step 3 - Creating our 'Model'

Up to this point, we have been managing our list of donations on the Client (via Angular) but we need to move this data management to the Server (Node) and eventually into a database (the next lab).

The first thing we need to do is create a new directory in our root directory called ***models/*** and within that directory create a new file called **donations.js**.

Now, paste the following code into your newly created .js file

```javascript
var donations = [
				 {id: 1000000, paymenttype: 'PayPal', amount: 1600, upvotes: 1}, 
				 {id: 1000001, paymenttype: 'Direct', amount: 1100, upvotes: 2}
				];

module.exports = donations;
```
Notice the extra field (id) in our model, this will be useful later on for deleting etc.

Your project should now look something like this

![](../images/lab4.step3.1.png)