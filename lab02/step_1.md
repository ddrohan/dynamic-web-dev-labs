# Objectives

In this Lab, you will be required to build the first version of our Donation Case Study Web App, called **DonationWeb 1.0**.  We will scaffold the app similar to [Lab 1](https://ddrohan.gitbooks.io/dynamic-web-dev-labs/content/lab01/lab_1.html), so if you're still a bit unsure of this process, maybe have a go at it again?

On completion of this lab you'll be able to

* create a simple **NodeJS** app using **express** 
* run this app as a **NodeJS Server** and process client requests
* be able to use **npm** to install dependency modules
* be able to implement a simple Web APi

In this version we will be implementing a simple **RESTful APi** with the following routes

  <p>
    <li><b>GET /donations</b>  - return a list of donations and associated metadata</li>
    <li><b>GET /donations/:id</b>  - return an individual donation with associated metadata</li>
    <li><b>POST /donations</b>  - create a new donation</li>
    <li><b>PUT /donations/:id/upvote</b>  - upvote a donation, notice we use the donation ID in the URL</li>
    <li><b>DELETE /donations/:id</b>  - delete a donation by ID</li>


