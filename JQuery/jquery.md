# Jquery basics and good to know

That cheatsheet was made after following courses on Codecademy. I'll add a few useful informations as well as things good to remember.

First, let's look at an example which compare basic javascript and jquery:
```js
//Selecting DOM elements and adding an event listener in JS
const menu = document.getElementById('menu');
const closeMenuButton = document.getElementById('close-menu-button');
closeMenuButton.addEventListener('click', () => {
    menu.style.display = 'none';
});

//Selecting DOM elements and adding an event listener in jQuery
$('#close-menu-button').on('click', () =>{
  $('#menu').hide();  
});
```
By using the Jquery library, you'll be able to save a huge amount of time and access a more readable and reusable code.

**TABLE OF CONTENT**
* [Setting up Jquery](#setting-up-jquery)
* [Define variable and select elements](#define-variable-and-select-elements)
* [Event handler](#event-handler)
* [Style Methods](#style-methods)
* [Moving inside the DOM](#moving-inside-the-dom)


## Setting up Jquery

### Include Jquery inside your project
Jquery isn't available by default in your project. You will need to add it by inserting a script, there are two ways to do that:

- **Add the CDN** (Content Delivery Network)
```js
<script src="https://code.jquery.com/jquery-3.3.1.min.js"></script>
```
A CDN allows you to retrieve files from a near server and load it into your project. Currently, you are retrieving the jquery library and adding it to your project when it loads.

- **Download and include the jquery file**

You'll need to visit the [Official Jquery website](https://jquery.com/download/) and download it. Note that there is a production and development version.
<br>
Transfer the downloaded file inside your project and include it withing your script by doing the following:
```js
<script src="jquery-3.7.1.min.js"></script>
```

**For both options:** <br>
Remember to add it a the top of your `<script>` otherwise, using jquery inside other files will be difficult. <br>

Jquery is now ready to be used. 


## Define variable and select elements

## Event handler

## Style Methods

## Moving inside the DOM