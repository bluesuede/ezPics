ezPics
====================

What
----------------------------------

ezPics is a lightweight and free jQuery plugin that has a responsive slider, lightbox and gallery function:

**ezSlider**
Creates a slideshow of at least two images. Buttons under the slideshow for the user to go between images. Moderate customizability, explained in the documentation below.

**ezLbox**
A very simple lightbox. No buttons or fancy features. It puts an image on top of a layer that goes over the whole page.

**ezGlry**
A barebone gallery coming with some simple css placing images in rows of three. When an image is clicked it opens up in a lightbox. From within the lightbox the user can click either on the left or right side of the image to see the previous or next image. Slight customizability, explained in the documentation below.

Why
----------------------------------
There are literally thousands of image handling jQuery plugins out there. Especially for making slideshows, lightboxes and galleries. However, I found that they all try and do way too many things at once, ending up in greater filesizes and longer load times. I've done my best to create a simple, no-fuzz plugin that can be used on simpler sites across all platforms. The minified version of ezPics is only 5kB. There are plugins out there with only a simple slideshow function that are around 5kB in size. It's all because they are trying to do too much.

If you are skilled in CSS it will also be very easy for you to alter the looks of for instance the gallery view. Why would you want me to make design choices for you? This plugin is not made to give a person with zero programming skills an opportunity to have a highly customizable plugin. I don't believe that a person without programming skills would even look for a jQuery plugin in the first place. This plugin is catered towards developers and giving them a backbone to keep building on.

In the future
----------------------------------
In the future I plan on steering the development of ezPics towards better mobile looks. At it's current stage it doesn't scale very well with smaller screens and I am very aware of that. There is currently no support for touch or swiping in the plugin.

I'm also planning to add support for showing the “alt”-information in the img tags in a simple yet beautiful manner. This will be optional.

The ezLbox function will be updated with customizable fade and animation settings. Also a “X” closing button in the corner of the window.

Documentation
====================

General info
----------------------------------
* ezPics have been tested in Firefox, Chrome and iOS Safari.
* ezPics works with images down to 100px in width.

Get started
----------------------------------
* Include the plugin after your jQuery file:
```sh
<script src="yourpath/jquery.js"></script>
<script src="yourpath/jquery.ezpics.js"></script>
```

* Make sure that the css is being read. Either by including the css file:
```sh
<link rel="stylesheet" type="text/css" href="yourpath/ezpics.css">
```
Or pasting it in to your own file:
```sh
/**
 * Style for the ezPics jQuery plugin
 *
 */
 
/* ezSlider style below */
#ezSlider {
  overflow:hidden;
  position:relative;
  width:100%;
}

#ezSlider li {
  max-height:100%;
  width:100%;
  position:absolute;
  display:block;
  left:0;
  top:0;
}

#ezSlider img {
  max-width:100%;
  margin:0 auto;
  display:block;
}

#dots {
  text-align:center;
}

#dots li {
  display:inline;
  float:none;
  margin-right:5px;
}

.dot a {
  border-radius: 15px;
  display: inline-block;
  height: 12px;
  overflow: hidden;
  text-indent: -9999px;
  width: 12px;
}

.unselected-button a {
  background: none repeat scroll 0 0 rgba(0, 0, 0, 0.2);
}

.selected-button a {
  background: none repeat scroll 0 0 rgba(0, 0, 0, 0.6);
}

/* Lightbox style, used in ezLbox och ezGlry */
#overlay {
  position:fixed;
  top:0;
  left:0;
  height:100%;
  width:100%;
  /* background:black url('../../img/loader.gif') no-repeat scroll center center;*/
  background-color:black;
  z-index:10;
}

#lightbox {
  position:fixed;
  z-index:10;
  cursor:pointer;
}

/* Style used in ezGlry */
#ezGlry li {
  height:7em;
  width:30%;
  margin-right:5%;
  float:left;
  overflow:hidden;
  margin-bottom:11px;
}

  #ezGlry img {
    max-width:90%;
	max-height:90%;
	cursor:pointer;
  }

  #ezGlry li:nth-child(3n) {
    margin-right:0;
  }
  
  #ezGlry li:nth-last-child(-n + 3):nth-child(3n + 1),
  #ezGlry li:nth-last-child(-n + 3):nth-child(3n + 1) ~ li {
    margin-bottom:0;
  }
  
.ezGlry-arrow-container {
  position:relative;
}
  
.ezGlry-arrow {
  background-color:rgba(0,0,0,0);
  position:fixed;
}
  
  .ezGlry-arrow:hover {
    background-color:rgba(0,0,0,0.2);
  }
  
  .ezGlry-arrow-inside {
    display:none;
  }
  
  .ezGlry-arrow:hover .ezGlry-arrow-inside {
	color:white;
	text-shadow: 0.05em 0.05em 0.1em black;
	font-size:1.7vw;
  }
  
/**
 * Vertical align centering solution below
 *
 */
  
  /* Parent element */
  .ezGlry-arrow,
  #ezGlry li  {
    text-align:center;
  }
  
  /* Pseudo element */
  .ezGlry-arrow:before,
  #ezGlry li:before {
    content:"";
    display:inline-block;
    height:100%;
    vertical-align:middle;
  }
  
  /* Centered element */
  .ezGlry-arrow:hover .ezGlry-arrow-inside,
  #ezGlry img  {
    display:inline-block;
    vertical-align:middle;
  }
```

ezSlider
----------------------------------
**Features**
* Choose your own fading time.
* Choose interval time of swapping images.
* Decide if you want buttons or not.
* Round or square buttons.
* Beautiful smooth transitions.
* Same width as parent element.
* You can choose height of the #ezSlider element.
* If pictures aren't as wide as the parent div, you have the possibility to choose background color.

**Setup**
* Make an unordered list with the id “ezSlider”. Put image tags inside the list item elements:
```sh
<ul id="ezSlider">
  <li><img src="img1.jpg" alt=""></li>
  <li><img src="img2.jpg" alt=""></li>
  <li><img src="img3.jpg" alt=""></li>
  <li><img src="img4.jpg" alt=""></li>
  <li><img src="img5.jpg" alt=""></li>
</ul>
```
* Call the function:
```sh
$(function() {
  $('#ezSlider').ezSlider();
});
```
* Customize settings:
```sh
$(function() {
  $('#ezSlider').ezSlider({
    'fade': 500, // Integer: Fade time in milliseconds
    'intervalTime': 5000, // Integer: Wait before it changes image in milliseconds
	'height': 350, // Integer: Max height of the #ezSlides element
	'dots': true, // Boolean: If buttons with links to the different image should be below images
	'bgColor': 'white', // String: Color of the background under an image
	'squareDots': false // Boolean: Square buttons instead of round ones
  });
});
```
**Important**
* The first image in the first li element will determine the height of #ezSlider. Having images of the same size is the most optimal choice but if that is not possible, make sure to put the image of lowest height first in the list.
* The background color can't be transparent, the user will then see another picture below the one in focus.
* You can only have one slideshow per page.

ezLbox
----------------------------------
**Features**
* Very, very simple. No distractions for the user.
* Does it's job and does it fast.
* Image will at the most be 90% of the window in either width or height.
* Can be used by other functions.
* User can click anywhere in the window to shut lightbox down when up.

**Setup**
* Call the function on your choice of class or id:
```sh
$(function() {
  $('.yourClassName, #yourIdName').click(function() {
    $(this).ezLbox();
  });	  
});
```
**Important**
* ezLbox has to be called with the click event.

ezGlry
----------------------------------
**Features**
* A simple gallery interface before an image has been clicked. Rows of three.
* Possible to use on images as small as 100px wide.
* Will align beautifully even if the pictures are different sizes and have different aspect ratios.
* Possibility to enable or disable a counter that tells which image in order is currently being shown.

**Setup**
* Make an unordered list with the id #ezGlry:
```sh
<ul id="ezGlry">
  <li><img src="img1.jpg" alt=""></li>
  <li><img src="img2.jpg" alt=""></li>
  <li><img src="img3.jpg" alt=""></li>
  <li><img src="img4.jpg" alt=""></li>
  <li><img src="img5.jpg" alt=""></li>
</ul>
```
* Call the function on id #ezGlry like this:
```sh
$(function() {
  $('#ezGlry').ezGlry();
});
```
**Important**
* Haven't been tested on images with width less than 100px.
* Uses the ezLbox function to create the actual lightbox then adds links to it.

License
----------------------------------
MIT