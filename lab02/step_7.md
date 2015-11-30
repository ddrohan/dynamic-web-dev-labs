
# Step 7 - Updating our 'Views', Part 2

As with Step 5, we need to wire up the angular frontend to allow donations to be

* Added
* Deleted
* Upvoted

---
## Updating 'donateController' with 'POST' request

Similar to the *donationsController*, we need to inject the **$http** object and remove the **donations** object, so go ahead and do that now. 

Next, replace the existing **addDonation()** function with the following

```javascript
$scope.addDonation = function(){
      $scope.formData.paymenttype = $scope.formData.paymentOptions.name;
       $http.post('/donations', /*enter a parameter here*/)
            .success(function(data) {
                $scope.donations = data;
                $location.path('/donations');
                console.log(data);
            })
            .error(function(data) {
                console.log('Error: ' + data);
              });
            };
```

And try and work out what parameter object you need to pass to the POST request. Now, test your web app by trying to add a donation, and try and fix the error.

**(HINT - it involves injecting an object into the controller)**

---
## Updating 'donationsController' with 'DELETE' request

Here's what you need for the DELETE request

```javascript
$scope.delete = function(id) {
      if (confirm("Are you sure you want to delete?")) {
              console.log('Deleting id : ' + id);
        $http.delete('/donations/' + id)
            .success(function(data) {
                $scope.donations = data;
                console.log(data);
            })
            .error(function(data) {
                console.log('Error: ' + data);
            });
          }
    };
```
Notice how we append the **id** to the request, which is passed in as a parameter - **this is important so be sure where it comes from, and why we need it**.

---
## Updating 'donationsController' with 'PUT' request
And finally, this is how we 'Upvote' a donation via a PUT request

```javascript
$scope.incrementUpvotes = function(id){
          $http.put('/donations/' + id + '/votes')
            .success(function(data) {
                $scope.donations = data;
                console.log(data);
            })
            .error(function(data) {
                console.log('Error: ' + data);
            });
          }
```


---
## Updating our .ejs pages

There's actually very little required for this part, and if you followed the previous changes closely, ***especially the implementation of the routes in donations.js in Step 6 (and how we delete in this Step)*** you should be able to make the minimal changes in **donations.ejs**

Once you've made all these modifications and updates, you should be able to navigate to [http://localhost:3000/](http://localhost:3000/), and use all the features of the web app (except update :-) )

##Well Done!!!!