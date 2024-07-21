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

When you define an event handler, Jquery will automaticaly add the corresponding event to the targeted element.
<br>
For instance, `$('.menu-button').on('click', () => {});` will add a `click` event to every objects with the class `.menu-button`.

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

### Useful tips

1) The use of `$(this)` and `$(event.currentTarget)`
When writing an event handler and defining the events that may occurs, it is a good practice to use the latter notations.

The use of `$(this)` allows you to edit the objects of the class `".menu-button"` quickly without having to write the name again.
```js
  $('.menu-button').on('click', () => {
    $('#nav-menu').show();
    $(this).css('color', '#FF00FF');
  });
```

`$(event.currentTarget)` is doing a slightly different work because it will only affect the **one element that has been triggered** instead of every element that share the class name.

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
It is possible to chain the events applied to an element. They will be triggered from left to right:
```js
// Applying styles and effects one after the other
$("#p1").css("color", "red")
  .slideUp(2000)
  .slideDown(2000);
```
*Example from W3Schools*

It can be particularly useful when you have to **chain event handler**:
```js
// The mouseleave won't happen if the mouseenter hadn't.
$('#menu-button').on('mouseenter', () => {
  $('#menu').show();
}).on('mouseleave', () => {
  $('#menu').hide();
});
```
*Example from Codecademy*

## Effects
**Useful links:** [All Jquery effects](https://api.jquery.com/category/effects/)

Jquery effects are quite simple to understand, let's show you some examples.

**String as speed**: Note that many effect methods allows the use of a string instead of a float value. For instance:
```js
$('#menu-button').on('mouseenter', () => {
  $('#menu').show(200);
  // can be replaced by:
  $('#menu').show("fast");
  // or
  $('#menu').show("slow");
});
```

### Slide

The slide methods are similar to `hide`, `show` and `toggle`. You will be able to use `slideUp`, `slideDown` and `slideToggle`.

**Syntax:** `$(selector).slideMethod(duration, callback);`

```js
$('#menu-button').on('click', () => {
  // menu appears over 1000ms duration
  $('#menu').slideDown(1000);
});
```
The default duration (without argument) is 400ms.

- `SlideUp` will **show** the targeted elements **with a sliding animation**.
- `SlideDown` will **hide** the targeted elements with a sliding animation.
- `SlideToggle` will hide or show with a sliding animation the targeted elements, depending of the current visibility state .

### Hide, show and toggle

That's quite straighforward.
```js
// Showing a menu when entering a specific button area
$('#menu-button').on('mouseenter', () => {
  $('#menu').show();
});

// Hiding a menu when leaving a specific button area
$('#menu-button').on('mouseleave', () => {
  $('#menu').hide();
});

// Toggle (invert) visibility of an element when performing a click on a specific button.
$('#menu-button').on('click', () => {
  // Hide or show, depending of the current visibility of "menu".
  $('#menu').toggle(); 
});
```

The **syntax** to follow:
- Hide:
`$(selector).hide(speed, callback);`

- Show: `$(selector).show(speed, callback);`

- Toggle: `$(selector).toggle(speed, callback);`

Speed in milliseconds.

### Fade
There are four fade methods. 

- **FadeIn**
Used to **gradually show** an hidden element
```js
$("button").click(function(){
  $("#div1").fadeIn();
  $("#div2").fadeIn("slow");
  $("#div3").fadeIn(3000);
  //You can also add a Callback.
});
```
*Examples from W3Schools* <br>

- **FadeOut**
Used to **gradually hide** an hidden element
```js
$("button").click(function(){
  $("#div1").fadeOut();
  $("#div2").fadeOut("fast");
  $("#div3").fadeOut(2000);
  //You can also add a Callback.
});
```

- **FadeToggle** 
Works the same as the previous ones but depends of the current state of the targeted element.
```js 
$(selector).fadeToggle(speed, callback);
// Optional callback
```

- **FadeTo** Fade an element to a given opacity
```js
$(selector).fadeTo(speed, opacity, callback);
// Optional callback
```

## Style Methods

When working with methods that should affect the CSS properties of an object, you can either:
- Apply **one modification**
```js
// Edit one property
$('.text').css('color', 'red');
```
- Apply **multiple modifications** at the same time
```js
// Edit multiple properties by using an object as argument.
$('.text').css({
  color: 'red',
  backgroundColor: 'gray',
  fontSize: '24px'
});
```

Note that the way to write it greatly differs. When trying to edit multiple properties, you should **write the property names without quotes** and by writing them **with camelCase instead of the classic CSS kebab-case**.

### Animations

- **Animate**
The jquery `.animate()` method allows you to custom an effect which uses CSS properties that should be triggered over time.

**Syntax**
`$(selector).animate({params},speed,callback);`


## Moving inside the DOM