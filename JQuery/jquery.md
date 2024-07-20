# Jquery basics and good to know

That cheatsheet was made after following courses on Codecademy. I'll add a few useful informations as well as things good to remember.

First, let's look at an example which compare basic javascript and jquery:
```javascript
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
By using Jquery, you'll be able to save a huge amount of time and access a more readable and reusable code.

**TABLE OF CONTENT**
* [Setting up Jquery](#setting-up-jquery)
* [Define variable and select elements](#define-variable-and-select-elements)
* [Event handler](#event-handler)
* [Style Methods](#style-methods)
* [Moving inside the DOM](#moving-inside-the-dom)


## Setting up Jquery

## Define variable and select elements

## Event handler

## Style Methods

## Moving inside the DOM