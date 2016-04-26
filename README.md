# Coding Standards

Welcome to my coding standards & styleguide. This is based off the coding standards I wrote for the company I work for. I'm including it here as a reference to the best practices I try to follow.

**(Still in progress)**



## General Formatting Rules

See / use .editorconfig file. Using this common file will prevent whitespace bounce.

* indent_style = space
* indent_size = 2
* end_of_line = lf
* charset = utf-8
* trim_trailing_whitespace = true
* insert_final_newline = true



## HTML Formatting Rules

General formatting rules plus..

* Paragraphs of text should always be placed in a `<p>` tag. Never use multiple `<br>` tags
* Items in list form should always be in `<ul>`, `<ol>`, or `<dl>`
* Every form input that has text attached should utilize a `<label>` tag. Especially radio or checkbox elements
* `<label>` tags associated with an input should have a `for` attribute, or the associated input an `aria-labelledby` attribute.
* Always use `"` (double quotes), not `'` (single quotes) in your html
* Use typographic quotes in visible text `&lsquo;`, `&rsquo;`, `&ldquo;` and `&rdquo;` (&lsquo;, &rsquo;, &ldquo;, &rdquo;).
* Always include an `alt=""` attribute on `<img>` tags
* Avoid trailing slashes in self-closing elements. such as `<br>`, `<hr>`, `<img>`, `<meta>` and `<input>`
* Don't set tabindex manually. Rely on the browser to set the order
* Never use inline css or inline javascript

```html
<div class="element">
  <img class="element__avatar" src="avatar.jpg" alt="Avatar">
  <p class="element__content">This is a paragraph of text.</p>
  <ul class="element__list">
    <li class="element__list-item">List Item</li>
    <li class="element__list-item">List Item</li>
    <li class="element__list-item">List Item</li>
  </ul>
</div>
```



## Lean Markup

Avoid unnecessarily wrapping elements in a parent element when possible. This creates extra bloat and over-specificity in the CSS.

```html
<!-- Bad -->
<div class="headline--bad">
  <h1>Headline</h1>
</div>

<!-- Good -->
<h1 class="h1 headline--good">Headline</h1>
```



## IDs vs Classes

Using IDs offers no benefit over classes and tends to cause specificity issues and having to write non-modular, non-reusable CSS. Always use classes for CSS styling hooks.



## Type Attributes

* Do not add `type="text/css"` to stylesheet link tags
* Do not add `type="text/javascript"` to javascript script tags

```html
<link rel="stylesheet" href="style.css">
<script src="script.js"></script>
```



## Asset File Naming

* Always use `-` (hyphen) to separate words in an asset file name
* Always name asset files starting with the most general term, working your way up to a specific term `bg-subpage-hero-large.jpg`

**Note:** Capitalization on file paths can look nice but causes problems across different operating systems.



## Sass/CSS Formatting Rules

#### CSS Formatting

* Always put a space after the `:` (colon) in property declarations
* Always put a space before the `{` (curly brace) in rule declarations
* Use hex color codes `#000` unless using rgba
* Use lower case letters in your hex color codes `#f1d2e3`
* Do not add a leading 0 in front of values that are less than 1. **Bad:** `0.5`
* Never add units after 0 values. **Bad:** `0px`
* Always include a `;` (semicolon) after the last property declaration
* Always use `'` (single quote), not `"` (double quote) in your CSS
* Always write your CSS multi-line, and never single line. **Bad:** `.format {color: #000; line-height: 2;}`
* Always put each selector on its own line when extending property declarations. **Bad:** `.h1, .h2, .h3 {}`
* Avoid using selectors like, `>`, `~`, or `+` when possible. This creates overly specific, non-reusable scope in the CSS output

#### Sass Formatting

* Besides pseudo classes, always avoid nesting elements when possible. Nesting creates over-specificity in the CSS output
* Always name SCSS partials with a leading `_` (underscore)
* When importing a partial, do not include the `.scss` extension or leading `_`
* Always use `//`, and never `/* */`, for css comments
* Always inline comment on property declarations that are needed for a special circumstance
* Always declare any variables at the top of the SCSS file
* Always use variables when a value is used multiple times
* Lint your Sass

```SCSS
@import 'partial';

// Variables
$variable: #000;

// Element
.element {
	color: $variable;
	background-color: rgba(0,0,0,.5);
	margin: 10px 0;

  &:after {
    content: ''; // This is a special circumstance comment
  }
}

.element__child {
  border: 2px solid #a1b2c3;
}

// Headlines
.h1,
.h2,
.h3 {
	font-size: 24px;
  line-height: 1.2;
}
```

**Note:** Included is a .scss-lint.yml file that you can add to your build and editor.



## Class Naming Conventions

* Separate words in a class name with a single `-` (hyphen)
* Never use a single `\_` (underscore) to separate words in a class name
* Never use camel-casing in class names
* Always be descriptive when choosing your class name `class="button"`
* Never abbreviate common names like button, header, footer, etc. **Bad:** `btn, hdr, ftr`
* Always use a `is-` prefix for state rules that are shared between CSS and JS

```CSS
.menu {
	...
}

.menu.is-open {
	...
}
```


## BEM Naming Convention

BEM, or Block Element Modifier is a methodology, that helps you to achieve reusable components and code sharing in the front-end.

* Bullets coming soon...

```CSS
.form {}
.form--signup {}
.form__input {}
.form__input--select {}
.form__submit {}
```

```HTML
<form class="form form--signup" action="" method="">
  <input class="form__input" type="text">
  <select class="form__input--select">
    <option></option>
    <option></option>
  </select>
  <input class="form__submit" type="submit" value="Submit">
</form>
```

**Reference:** http://getbem.com/naming/



## Pixels vs Ems

* Always use `px` for font-size
* Always use unit-less value for line-height, unless you are vertically centering single-line text

```CSS
.element {
	font-size: 16px;
	line-height: 2;
}
```



## Javascript HTML Hooks

* Always use a new class with a `js-` prefix when adding a hook in your html for javascript
* Never use the `js-` hook as a styling hook in your CSS

```HTML
<div class="button button--primary js-menu-button">
	...
</div>

<select class="input input--select js-date-picker">
	<option>option</option>
	<option>option</option>
</select>
```



## Javascript Lint

JSLint is a static code analysis tool used in development for checking if JavaScript source code complies with coding rules. See the included `.jscsrc` and `.jshintrc` file for more info.



## Learn More

* http://getbem.com/
* http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/
* https://github.com/styleguide/css
* http://thesassway.com/advanced/modular-css-naming-conventions
