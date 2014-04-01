Coding Standards & Styleguide
================

Welcome to my coding standards & styleguide. This is just a reference for the best practices I try to follow.

<b>References</b>

* https://github.com/styleguide/css
* http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml
* http://thesassway.com/advanced/modular-css-naming-conventions



HTML Formatting Rules
---

* Always indent a full tab (4 spaces)
* Always indent every child element
* Always comment the end of a div block after the closing div tag <code></div><!--/.classname--></code>
* Always use <code>"</code> (double quotes), not <code>'</code> (single quotes) in your html
* Always include an alt attribute on img tags <code>alt=""</code>
* Never close self-closing tags such as hr, br, img, or input
* Never use inline css or inline javascript

Example:

	This is an example of proper syntax
	
	<div class="content">
		<div class="block">
			<p>Lorem ipsum</p>
			<img src="avatar.jpg" alt="Avatar">
			<hr>
			<input type="text">
			<br>
		</div><!--/.block-->
	</div><!--/.content-->




IDs vs Classes
---

Using IDs offers no benefit over classes and tends to cause specificity issues and having to write non-modular, non-reusable CSS. For that reason, we recommend sticking to using classes for CSS styling hooks.

* Classes should only be used for CSS hooks
* You should never use IDs




Type Attributes
---

* Do not add <code>type="text/css"</code> to stylesheet link tags
* Do not add <code>type="text/javascript"</code> to javascript script tags

Example:

	This is an example of proper syntax

	<link rel="stylesheet" href="style.css">
	<script src="js/script.js"></script>
	
	
	
File Naming
---

* Always use <code>-</code> (hyphen) to separate words in a file name
* Always name files starting with the most general term, working your way up to a specific term <code>bg-subpage-hero-price-burst.jpg</code>
* Always use <code>_</code> (underscore) to prefix php includes and scss partials

Example:

	logo-main.jpg
	bg-subpage-sidebar.png
	_urgency-banner.php
	pricing-guide.html
	_navigation.scss



CSS Formatting Rules
---

* Always put a space after <code>:</code> (colon) in property declarations
* Always put a space before <code>{</code> (curly brace) in rule declarations
* Use hex color codes <code>#000</code> unless using rgba
* Use lower case letters in your hex color codes <code>#f1d2e3</code>
* Do not add a leading 0 in front of values that are less than 1. <i>Bad:</i> <code>0.5</code>
* Never add units after 0 values. <i>Bad:</i> <code>0px</code>
* Always include a <code>;</code> (semicolon) after the last property declaration
* Always use <code>'</code> (single quote), not <code>"</code> (double quote) in your CSS
* Always include a line-break in-between rule declarations
* Always write your CSS multi-line, and never single line. <i>Bad:</i> <code>.format {color: #000; line-height: 2;}</code>
* Always put each rule declaration on its own line when extending property declarations. <i>Bad:</i> <code>h1, h2, h3 {}</code>

Example:

	This is an example of proper syntax
	
	.formatting-rules {
		color: #000;
		background: rgba(0,0,0,.5);
		margin: 10px 0;
	}
	
	.formatting-rules:after {
		content: '';
	}
	
	h1,
	h2,
	h3 {
		padding: 5px;
	}
	

	
Class Naming Conventions
---

* Only use <code>-</code> (hyphen) to separate words in class names
* Never use <code>_</code> (underscore) in class names
* Never use camel-casing in class names
* Always be descriptive when choosing your class name <code>class="button"</code>
* Never abbreviate common names like button, header, footer, etc. <i>Bad:</i> <code>btn, hdr, ftr</code>
* When using a class modifier, always use a descriptive prefix such as <code>is- has- with-</code>

Example:

	This is an example of proper syntax
	
	.button {
		// styles
	}
	
	.button.is-hidden {
		// styles
	}



Pixels vs Ems
---

* Always use <code>px</code> for font-size
* Always use unit-less value for line-height, unless you are vertically centering single-line text

Example:

	This is an example of proper syntax
	
	.formatting-rules {
		font-size: 16px;
		line-height: 2;
	}
	


Javascript HTML Hooks
---

* Always use a new class with a <code>js-</code> prefix when adding a hook in your html for javascript
* Never use the <code>js-</code> hook as a styling hook in your CSS
* Always use <code>'</code> (single quote), not <code>"</code> (double quote) in your Javascript

Example:

	This is an example of proper syntax
	
	<div class="menu-button js-menu-button">
		// stuff
	</div><!--/.menu-button-->
	
	<select class="js-date-picker">
		<option>option</option>
		<option>option</option>
	</select>
	
	
	
PHP Formatting Rules
---

* Always name your php partial with a leading underscore and a php extension <code>'_filename.php'</code>
* Do not name your php include with an html extenstion <code>'_urgency-banner.html'</code>



Sass Formatting Rules
---

* Never nest deeper than 3 levels unless absolutely necessary
* Always name your Scss partial with a leading <code>_</code> (underscore)
* Do not include the .scss extension in @import partial
* Use <code>//</code> for css comments
* Never use <code>/* */</code> for css comments
* Always inline comment on property declarations that are needed for a certain reason
* Always declare any variables at the top of the scss file

Example:
	
	// Imports
	@import '_nav-partial';
	
	// Variables
	$color: #000;
	
	// Nav
	nav {
		
		ul {
			// styles
		}
		
		li {
			position: absolute; // this is a comment about why this needs to be positioned absolute
			color: $color;
			
			&:first-child {
				// styles
			}
		}
		
		a {
			// styles
			
			&:hover {
				// styles
			}
		}
	} // nav
	
	
	
Sass Mixins
---

We recommend using the RV Sass mixins included in the sass/globals folder. This will make it much easier to keep all team members familiar with our mixin syntax as well as not having to require dependencies based on other libraries. For this reason, we do not recommend the use of external libraries such as Bourbon or Compass. If there is a certain mixin you need or want to use in your project, we recommend adding it into a partial in the sass/globals folder for your project only. The RV Sass mixins we recommend are in the new site spinup or can be found at the link below.

https://github.com/RVCreative/sass-mixins



Folder Organization
---


HTML Example:
	
	data
	├── landing_pages
	|	└── default
	|		└── includes
	|			├── banners
	|			├── globals
	|			|	├── _header.php
	|			|	├── _masthead.php
	|			|	└── _footer.php
	|			└── heroes
	|
	└── assets
		└── css
		|	└── compiled.css
		├── images
		|	└── //files
		├── js
		|	├──	app.js
		|	├──	library
		|	|	└──	jquery.js
		|	├── plugins
		|	|	├──	clycle.js
		|	|	└──	placeholder.js
		|	└── functions.js
		├── sass
		|	└── compiled.scss
		|		└──	//files (see below)
		└── fonts
	


Sass Example:

	compiled.scss
	└── project
		├──	_project-fonts.scss
		├──	_project-styles.scss
		├──	_project-variables.scss
		|
		├──	sections
		|	├──	_header.scss
		|	├──	_masthead.scss
		|	└──	_footer.scss
		|	
		└──	globals
			├──	_mixins.scss
			├──	_typography.scss
			├──	_reset.scss
			└──	_base.scss



Object Oriented / Modular CSS
---

Modular CSS is all about learning to think about your CSS in terms of objects, or better yet, modules. Modules are small little chunks of reuseable functionality. The idea is to write a small bit of code that encourages code reuse and faster, more efficient stylesheets that are easier to add to and maintain.

First lets look at a non-modular example:

Non-modular Example:

	.content-box {
		width: 200px;
		height: 200px;
		background: #fff;
	}
	
	.bordered-content-box {
		width: 200px;
		height: 200px;
		border: 5px solid #000;
		background: #fff;
	}
	
	<div class="content-box">
		//stuff
	</div><!--/.content-box-->
	
	<div class="bordered-content-box">
		//stuff
	</div><!--/.bordered-content-box-->
	
As you can see, we have 2 content boxes, 1 with a border, and 1 without. Because we wrote this in a non-modular way, we had to write specific CSS for each box just to add a border to the second box. This obviously works but also adds pointless bloat to the stylesheet.

Now lets rewrite this in a modular, object oriented way:

Modular Example:
	
	.content-box {
		width: 200px;
		height: 200px;
		background: #fff;
	}
	
	.with-border {
		border: 5px solid #000;
	}
	
	<div class="content-box">
		//stuff
	</div><!--/.content-box-->
	
	<div class="content-box with-border">
		//stuff
	</div><!--/.content-box-->

You will now see we achieved the same effect just by creating a modifier class to add the border to the content box. This reduces needless code in the stylesheet, and gives us a 'with-border' modifier class that we can now use on any object in the markup.

This is just a very simple example of how you should write your css in an object oriented / modular way. We would encourage you to continue to learn more about object oriented / modular css by visiting these sites below.
	
<b>Learn more</b>

* http://coding.smashingmagazine.com/2011/12/12/an-introduction-to-object-oriented-css-oocss/
* http://www.creativebloq.com/css3/create-modular-and-scalable-css-9134351
* http://thesassway.com/advanced/modular-css-naming-conventions
