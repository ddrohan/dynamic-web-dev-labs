
# Step 4 - Refactoring our Controllers

Our current version of Donation isn't fully functional mainly due to the fact that what was originally a client side app has now become a client-server app and we need to restructure how our views are managed (***controlled***).

The first thing we need to do is create a ***seperate controller*** for each of our views so navigate to the ***public/javascripts/*** directory and create a new folder called ***controllers/***.

We need to move all the **controllers** in our single **angularApp.js** file into their own respective files, so create the following inside your ***controllers*** folder

![](../images/controllers.png)

Now, for each controller in our **angularApp.js** move it into its respective file in the ***controllers/*** (as above).

As each controller is going to be in a separate file we will need to add the following line of code to each file

```javascript
var app = angular.module('DonationWebApp');
```
As a start, here's our updated ***aboutcontroller.js***

```javascript
var app = angular.module('DonationWebApp');

app.controller('aboutController', ['$scope', function($scope) {
    // create a message to display in our view
      $scope.message = 'This is the about Page';
     }
  ]);
```
So initially, have a go at ***contactcontroller.js*** and ***maincontroller.js***.

There's a bit more work involved with last two controllers (***donatecontroller.js*** & ***donationscontroller.js***) so we'll complete those separately.

It's probably worth testing your app again just to confirm that the controllers you've updated still work so point your browser at [http://localhost:3000](http://localhost:3000) and try it out.


### NOTE - Make sure you've added a script reference to your controller files in your Shell Page (index.ejs)

---

## Our 'donationsController' and Dependency Injection (D.I.)
To begin with, take the same approach with this controller as the previous ones, just move it into its own file and add the line of code at the top, so you'll have something like this

```javascript
var app = angular.module('DonationWebApp');

app.controller('donationsController', function($scope, donations) {
    // create a message to display in our view
    $scope.message = 'Donations Page!';
    $scope.donations = donations;

      $scope.delete = function(donation){
      if (confirm("Are you sure you want to delete? : ")) {
          donations.deleteDonation(donation);
         }       
      };

        $scope.incrementUpvotes = function(donation){
          donations.incrementUpvotes(donation);
      };
  });

```
If you try and test it, it may still not be functioning correctly - can you explain why, and how to fix it?

The problem lies in the fact that this controller is in a separate file so the ***$scope*** object needs to be *injected* into the controller (as well as the donations). 

**This wasn't an issue in our Angular version as everything was inside the one file (same scope).**

So here are the changes we need to make

```javascript
var app = angular.module('DonationWebApp');

app.controller('donationsController', ['$scope','donations', function($scope, donations) {
    // create a message to display in our view
    $scope.message = 'Donations Page!';
    $scope.donations = donations;

      $scope.delete = function(donation){
      if (confirm("Are you sure you want to delete? : ")) {
          donations.deleteDonation(donation);
         }       
      };

        $scope.incrementUpvotes = function(donation){
          donations.incrementUpvotes(donation);
      };
  }
  ]);
```
Notice how we *inject* **$scope** and **donations** into our controller and we need to do the same with our **donateController** controller (and a bit more!)

---

## Our 'donateController' and D.I.
Once again, take the same approach with this controller as the previous ones, just move it into its own file and add the line of code at the top.

As we're displaying and posting form data through this controller we are going to make use of the **$scope.formData** object and 'package up' everything we need to display and post.

To save time, here's the completed controller 

```javascript
var app = angular.module('DonationWebApp');


app.controller('donateController', ['$scope', '$location', 'donations', function($scope, $location, donations) {
    
    $scope.formData = {};

    $scope.message = 'Donate Page!';
    $scope.amount = 1000;
    $scope.options = [{ name: "PayPal", id: 0 }, { name: "Direct", id: 1 }];
    $scope.formData.paymentOptions = $scope.options[0];

    $scope.addDonation = function(){
          console.log('Adding FormData: ' + $scope.formData.paymentOptions.name + '//' + $scope.formData.amount);
          donations.add($scope.formData.paymentOptions.name,$scope.formData.amount);
          $location.path('/donations');
      };
  
//Reset our formData fields
    $scope.formData.paymenttype = 'PayPal';
    $scope.formData.amount = 1000;
    $scope.formData.upvotes = 0;
  }

  ]);
```
**It's VERY IMPORTANT you understand the changes we've made as the changes need to be reflected in the corresponding view - (donate.ejs)**

