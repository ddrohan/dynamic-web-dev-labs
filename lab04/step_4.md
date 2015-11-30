# Step 4 - Implement the 'Contact Us' Page

This step (which is virtually identical to the previous step) involves adding another navigation link to our navigation bar to take the user to a 'Contact Us' page, like so

![](../images/navbar.lab1.v3.png)

---

## Updating the Navigation Bar

Once again, adding the link is quite straightforward so open up your **index.html** page and add the following html code to the list of links

```html
<li><a href="#contact"><i class="fa fa-comment"></i> Contact</a></li>

```
Save the file and a quick refresh of the page in your browser should display the expected result.

---

##Adding 'contact.html'

We'll again keep this page fairly simple for the moment so create a new file (contact.html) within the **'pages'** directory/folder of your webapp folder and place the following html inside it.

```html
<div class="jumbotron text-center">
	<h1>Contact Us</h1>
	
	<p>{{ message }}</p>
</div>
```
---

##Wiring it all up - the 'Contact Us' Controller and Routing

This is more or less the same as the previous step as we need to  

* create a new ***controller*** object to manage the page and
* add a new ***route*** to ensure the link is correctly associated with the **controller**

So try and have a go at adding the controller ('contactController') and the routes without referring to the previous step. 

Once again, make sure you save your file before you refresh in the browser. If all goes to plan you should now be able to navigate to the **'Contact Us'** page and see your message displayed.

##Well done - you've just built your 1st Angular Web App!


