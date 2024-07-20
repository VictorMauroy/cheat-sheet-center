# Jquery basics and good to know

That cheatsheet was made after following courses on Codecademy. I'll add a few useful informations as well as things good to remember.

**USEFUL LINKS**
* [Official Jquery website](https://jquery.com/)
* [W3Schools complete tutorial](https://www.w3schools.com/jquery/default.asp)

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

### Creating a new file

You'll have to create a file with the `.js` extension in order to write jquery things.

Once the file is created, you will usually need to add those lines:
```js
$(document).ready(() => {
    
    // Your Jquery code will be there !

    $(/*Object to select*/).on('click', () => {
    $(/* Current or another object*/).anAction(/* Parameters*/);
});

}
```
That's important because you must **wait for the document (DOM) to be loaded before executing anything!**

## Define variable and select elements

The main use of Jquery is to quickly select DOM elements and apply various effects and update to them.

### Select an object
You can select many things with jquery:
```js
$('.selector-button') // Select all object with the CLASS "selector-button"

$('#highlighted') // Select the object with the ID "highlighted"

$('p') // Select all the paragraphs. (Html object name)

$(this) // Select the current object (usually inside an event handler)
```

Check [here](https://www.w3schools.com/jquery/jquery_selectors.asp) for more selectors. Like selecting with type, attribute or encapsulated elements.

### Variables

Saving the objects that your retrieved is quite easy, you can do that by defining a javascript variable and storing the result inside it.
```js
const $myParagraphs = $('p');
```
Follow the `camelCase` syntax and add a `$` before your variable name. This isn't required but it's a lot easier to know which variable is from native Javascript and which one is from jquery.

## Event handler and effects

Once you're able to select elements inside your document, you will surely search how to add interaction. You can do that by hading **Event Handlers**.

### Define an event handler

There a two ways to define an event with Jquery:
- Use the `.on` notation:
```js
$('.menu-button').on('click', () => {
  $('#nav-menu').show();
});
```
- Call the event name
```js
$('.menu-button').click(function() {
  $('#nav-menu').show();
  //You can add more lines
});
```

There are many events that you can use, check the following array:
|Mouse events|Keyboards events|Forms events|Document / Windows events|
|-|-|-|-|
|click|keypress|submit|load|
|dldclick|keydown|change|resize|
|mouseenter|keyup|focus|scroll|
|mouseleave||blur|unload|

Learn more at the [W3School event handler page](https://www.w3schools.com/jquery/jquery_events.asp).

### Arguments & Callbacks
Take note that some events/effects can accept multiple arguments. 

For instance, the `fade` method:
```js
$("button").click(function(){
  
  $("#div1").fadeIn(); //use of default parameters

  $("#div3").fadeIn(3000); // Define your own duration in milliseconds.
  
  $("#div2").fadeIn("slow"); // Use a prepared string

});
```
*Exemple from W3School.*

It is also possible to **add a callback** at the end of a method (when the effect ends, trigger another function or code).
```js
$("button").click(function(){
  
    $("#div1").fadeIn(2000, function() {
      $(this).css('backgroundColor', '#FFFFFF');    
    }); // classic callback
  
  $("#div1").fadeIn(2000, () => {
    $(this).css('backgroundColor', '#FFFFFF');    
  }); // Use of an arrow function

});
```

### Chain events


## Style Methods

## Moving inside the DOM