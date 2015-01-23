What
----------------------------------

ezPics is a lightweight and free jQuery plugin that has a responsive slider, lightbox and gallery function:

**ezSlider**
Creates a slideshow of at least two pictures. Buttons under the slideshow for the user to go between pictures. Moderate customizability, explained in the documentation below.

**ezLbox**
A very simple lightbox. No buttons or fancy features. It puts a picture on top of a layer that goes over the whole page.

**ezGlry**
A barebone gallery coming with some simple css placing pictures in rows of three. When a picture is clicked it opens up in a lightbox. From within the lightbox the user can click either on the left or right side of the picture to see the previous or next picture. Slight customizability, explained in the documentation below.

Why
----------------------------------
There are literally thousands of image handling jQuery plugins out there. Especially for making slideshows, lightboxes and galleries. However, I found that they all try and do way too many things at once, ending up in greater filesizes and longer load times. I've done my best to create a simple, no-fuzz plugin that can be used on simpler sites across all platforms. The minified version of ezPics is only 5kB. There are plugins out there with only a simple slideshow function that are around 5kB in size. It's all because they are trying to do too much.

If you are skilled in CSS it will also be very easy for you to alter the looks of for instance the gallery view. Why would you want me to make design choices for you?

In the future I plan on steering the development of ezPics towards better mobile looks. At it's current stage it doesn't scale very well with smaller screens and I am very aware of that. There is currently no support for touch or swiping in the plugin.

Documentation
====================

General info
----------------------------------
* ezPics have been tested in Firefox, Chrome and iOS Safari.
* ezPics works with pictures down to 100px in width.

Get started
----------------------------------
* Include the plugin after your jQuery file:
```sh
<script src="yourpath/jquery.js"></script>
<script src="yourpath/jquery.lightboxgallery.js"></script>
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