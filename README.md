# CSS Style Guide

This document defines formatting and style rules for HTML and CSS. It aims at improving collaboration, code quality, and enabling supporting infrastructure. It applies to raw, working files that use HTML and CSS. Tools are free to obfuscate, minify, and compile as long as the general code quality is maintained.

## Table of Contents
1. [General Meta Rules](#general-meta-rules)
    * [Protocol](#protocol)
2. [CSS Formatting Rules](#css-formatting-rules)
    * [Indentation](#indentation)
    * [Block Content Indentation](#block-content-indentation)
    * [Capitalization](#capitalization)
    * [Trailing White Space](#trailing-white-space)
    * [Declaration Stops](#declaration-stops)
    * [Property Name Stops](#property-name-stops)
    * [Declaration Block Separation](#declaration-block-separation)
    * [Selector and Declaration Separation](#selector-and-declaration-separation)
    * [Rule Separation](#rule-separation)
    * [CSS Quotation Marks](#css-quotation-marks)
    * [Nesting Rule Separation](#nesting-rule-separation)
3. [CSS Style Rules](#css-style-rules)
    * [CSS Validity](#css-validity)
    * [ID and Classes](#id-and-classes)
    * [ID and Class Naming](#id-and-class-naming)
    * [ID and Class Name Delimiters](#id-and-class-name-delimiters)
    * [ID and Class Name Style](#id-and-class-name-style)
    * [Type Selectors](#type-selectors)
    * [Shorthand Properties](#shorthand-properties)
    * [0 and Units](#0-and-units)
    * [Leading 0s](#leading-0s)
    * [Hexadecimal Notation](#hexadecimal-notation)
    * [Hacks](#hacks)
4. [CSS Meta Rules](#css-meta-rules)
    * [Encoding](#encoding)
    * [Comments](#comments)
    * [Section Comments](#section-comments)
5. [Modern CSS](#modern-css)
    * [CSS Custom Properties](#css-custom-properties)
    * [Logical Properties](#logical-properties)
6. [CSS Preprocessor Rules](#css-preprocessor-rules)
    * [File Organization](#file-organization)
    * [Multiple Variable Declaration](#multiple-variable-declaration)
7. [CSS Preprocessor Helpers](#css-preprocessor-helpers)
    * [Breakpoints](#breakpoints)
    * [Media Queries](#media-queries)
    * [Container Queries](#container-queries)
    * [Clearing Floats](#clearing-floats)
    * [Rem Units](#rem-units)
    * [Box Sizing Mixin](#box-sizing-mixin)


## General Meta Rules

### Protocol

Always include the protocol (`https://`) for external resources. Explicit `https://` URLs ensure secure, predictable loading and avoid ambiguity caused by protocol-relative URLs. Use `https://` for external stylesheets and other media whenever they are available over HTTPS.

```html
<!-- Recommended -->
<link href="https://www.example.com/style.css" rel="stylesheet" media="screen" />

<!-- Avoid -->
<link href="//www.example.com/style.css" rel="stylesheet" media="screen" />
```

## CSS Formatting Rules

### Indentation

Indent by 2 spaces.

Do not use tabs or mixed tabs and spaces for indentation.

```css
.example {
  color: blue;
}
```

---
### Block Content Indentation

Indent all block content.

```css
@media screen, projection {

  html {
    color: blue;
  }

}
```

---
### Capitalization

Use only lowercase.

All code has to be lowercase: This applies to HTML element names, attributes, attribute values (unless text/CDATA), CSS selectors, properties, and property values (with the exception of strings).

```css
/* Not recommended */
HTML {
  color: #E5E5E5;
}

/* Recommended */
html {
  color: #e5e5e5;
}
```

---
### Trailing White Space

Remove trailing white spaces.

Trailing white spaces are unnecessary and can complicate diffs.

```css
/* Not Recommended */
.example {
  color: blue;_
}

/* Recommended */
.example {
  color: blue;
}
```

---
### Declaration Stops

Use a semicolon after every declaration.

```css
/* Not Recommend */
.example {
  display: block;
  color: blue
}

/* Recommended */
.example {
  display: block;
  color: blue;
}
```

---
### Property Name Stops

Use a space after a property name's colon.

```css
/* Not Recommend */
.example {
  margin:20px;
}

/* Recommended */
.example {
  margin: 20px;
}
```

---
### Declaration Block Separation

Use a space between the first and last selector and the declaration block.

Always use a single space between the last selector and the opening brace of the block. Blocks should never be on a single line. The opening brace should be on the same line as the last selector.

```css
/* Not Recommend */
.example{
  display: block;
}

/* Not Recommend */
.example { display: block; }

/* Not Recommend */
.example
{
  display: block;
}

/* Recommended */
.example {
  display: block;
}
```

---
### Selector and Declaration Separation

Place declarations on their own lines.

Selectors may share a line **only when they are closely related** (e.g., sharing the same styling role).

Otherwise, place each selector on its own line for clarity and maintainability.

**Do not:**
- Put declarations on the same line.
- Combine unrelated selectors onto one line.

```css
/* Not Recommended — unrelated selectors crammed together */
h1, .card-title {
  font-weight: 600;
}

/* Not Recommended — declarations on same line */
.example { display: block; color: red; }

/* Recommended — related selectors on one line */
h1, h2 {
  font-weight: 600;
  margin-block-end: 0.5em;
}

/* Recommended — unrelated selectors on separate lines */
h1,
.card-title,
.page-heading {
  font-weight: 600;
}

/* Recommended — declarations separated cleanly */
.example {
  display: block;
  color: red;
}
```

---
### Rule Separation

Separate new rules by new lines.

Always put a blank line (two line breaks) between rules. No new line is needed at the end of files.

```css
html {
  font-size: 12px;
}

body {
  margin: auto;
}
```

---
### CSS Quotation Marks

Use double quotes for CSS strings and attribute selectors. 

Do not quote `url()` values unless the URL contains spaces or special characters.

```css
/* Not Recommend */
html {
  font-family: 'Open Sans', Arial, sans-serif;
  background: url('example.jpg');
}

/* Recommended */
html {
  font-family: "Open Sans", Arial, sans-serif;
  background: url(example.jpg);
}

input[type="text"] {
  border: 1px solid #ccc;
}
```

@charset must always use double quotes. Please note that this code is not needed in modern setups.

```css
@charset "UTF-8";
```

---

### Nesting Rule Separation

Separate blocks of rules by new lines.

The only exception to this is if the parent do not have any styles.

```css
/* Not Recommended */
.container {

  p {
    color: blue;
    span {
      display: block;
    }
  }
  ul {
    margin: 20px;
  }
}

/* Recommended */
.container {
  p {
    color: blue;

    span {
      display: block;
    }
  }

  ul {
    margin: 20px;
  }
}
```


## CSS Style Rules

### CSS Validity

Use valid CSS where possible.

Use only valid CSS code using such tools as the [W3C CSS Validator](https://jigsaw.w3.org/css-validator/). Validations tools can not spot all errors and may even give false positives for newer valid CSS. Take care to note that valid CSS can still contain visual bugs as support and implementation of properties can vary from browser to browser.

---
### ID and Classes

Use classes for modularity.

For general page styling uses classes. ID's should be reserved for special cases or hooks into other languages such as Javascript.

---
### ID and Class Naming

Use meaningful or generic ID or class names.

Use ID and class names that reflect the purpose of the element in question, or that is otherwise generic that can be used anywhere needed. Names that reflect presentational or cryptic in nature should be avoided.

```css
/* Not Recommended */
.ml20 {}
.blue {}

/* Recommended */
.video {}
.login {}
```

---
### ID and Class Name Delimiters

Separate ID and class names by hyphens.

Do not use underscores, camel case, double hyphens, or any other delimiters unless you are using a system like BEM or similar.

```css
/* Not Recommended */
.demoImage {}
.error_status {}

/* Recommended */
.demo-image {}
.error-status {}
```

---
### ID and Class Name Style

Use ID and class names that are as short as possible but as long as necessary.

Use ID and Class names that is easy to understand but is not verbose. This will help with readability and code efficiency.

```css
/* Not Recommended */
.a {}
.main-header-navigation-right {}

/* Recommended */
.author {}
.navigation {}
```

---
### Type Selectors

Avoid qualifying ID and class names with type selectors.

```css
/* Not Recommended */
div.example {}

/* Recommended */
.example {}
```

---
### Shorthand Properties

Use shorthand properties where possible.

Using shorthand properties is useful for code efficiency and understandability.

```css
/* Not Recommended */
margin-inline-start: 10px;
margin-inline-end: 20px;
margin-block-end: 10px;

/* Recommended */
margin: 0 20px 10px 10px;
```

---
### 0 and Units

Omit units after "0" values.

```css
margin: 0;
padding: 0;
```

---
### Leading 0s

Always include leading zeros for decimal values for improved readability.

```css
font-size: 0.8rem;
opacity: 0.5;
```

---
### Hexadecimal Notation

Use 3 character hexadecimal notation where possible.

```css
/* Not Recommended */
color: #eebbcc;

/* Recommended */
color: #ebc;
```

---
### Hacks

Avoid CSS hacks. Try a different approach first.

The days of IE6 are far behind us. Avoid hacks to target specific browsers unless absolutely necessary. Try a different coding approach first before resorting to a "hack".


## CSS Meta Rules

### Encoding

Use UTF-8.

Specify the encoding in HTML. Do not specify the encoding of stylesheets as these assume UTF-8.

```html
<meta charset="utf-8">
```

---
### Comments

Explain code as needed when possible.

Use comments to explain code. What does it cover? What purpose does it serve? Be thoughtful in the amount of comments as a large project can quickly become unmaintainable with too many comments. Leave comments for only technically difficult or confusing parts of code.

---
### Section Comments

Group sections by a section comment.

If possible, group stylesheet sections by using comments.

```css
/*
-----------------------------------------
Large Section Comment
-----------------------------------------
*/

/* Small Section Comment*/
```


## Modern CSS

### CSS Custom Properties

Prefer CSS custom properties (native "CSS variables") wherever possible before falling back to preprocessor variables like SCSS's. Custom properties are dynamic at runtime, participate in the cascade, can be changed with media queries or JavaScript, and make theming and overrides much simpler. Use SCSS variables only when you need build-time values or to compute values that cannot be expressed with CSS alone.

Example (preferred):

```css
:root {
  --primary: #b20215;
  --secondary: #149ff6;
  --grey: #848484;
  --brown: #a89f94;
}

.button {
  color: var(--primary);
}
```

---
### Logical Properties

Use CSS logical properties instead of physical properties to keep layouts direction-agnostic and easier to maintain. Logical properties adapt automatically to LTR, RTL, and other writing modes.

**Avoid:**
- Physical properties like `margin-left`, `padding-right`, `top`, `bottom`, etc.
- Mixing logical and physical properties on the same element unless unavoidable for legacy reasons.

**Use:**
- `margin-inline`, `margin-block`
- `padding-inline`, `padding-block`
- `inset`, `inset-inline`, `inset-block`
- `border-inline-start`, `border-inline-end`
- `border-block-start`, `border-block-end`

**Example**
```css
/* Not Recommended */
.card {
  padding-top: 1rem;
  padding-bottom: 1rem;
  padding-left: 1.5rem;
  padding-right: 1.5rem;
  border-top: 2px solid var(--border);
  left: 0;
  right: 0;
}

/* Recommended */
.card {
  padding-block: 1rem;
  padding-inline: 1.5rem;
  border-block-start: 2px solid var(--border);
  inset-inline: 0;
}
```

## CSS Preprocessor Rules

---
### File Organization

Separate your files into logical groups.

Split your files into logical files and folders to keep things organized and clear to understand. There are many ways to do this. **The following is an example of what *could* be done, but not what *has* to be done**.

##### Example Structure for SCSS

```
css/
|
|-- helpers/              # Bootstrapping
|   |-- _normalize.scss
|   |-- _variables.scss
|   |-- _mixins.scss
|
|-- base-styles/          # Base Styles
|   |-- _general.scss
|   |-- _layout.scss
|   |-- _fonts.scss
|   |-- _typogrpahy.scss
|   |-- _buttons.scss
|   |-- _forms.scss
|   ...
|
|-- modules/              # Modules
|   |-- _masthead.sass
|   |-- _footer.scss
|   |-- _home.scss      
|   ...
|
|-- utility/              # CSS or Sass from other projects or libraries
|   |-- _colorpicker.scss
|   |-- _slider.scss
|   ...
|
|-- style.scss            # Primary Sass file
```

---
### Multiple Variable Declaration

Line up all properties and values when declaring multiple variables.

```css
/* SCSS Variables */
$primary:        #b20215;
$secondary:      #149ff6;
$grey:           #848484;
$brown:          #a89f94;
```

Prefer CSS custom properties for runtime theming and overrides — see the [CSS Custom Properties](#css-custom-properties) section above. Use SCSS variables only when you need build-time values or computations that cannot be expressed with CSS alone.


## CSS Preprocessor Helpers

### Breakpoints

You should have a single source of breakpoints to reference. You may have how ever many your project needs.

```css
$breakpoints: (
  "mega-wide": 1600px,
  "ultra-wide": 1440px,
  "desktop-wide": 1248px,
  "desktop": 1024px,
  "desktop-small": 992px,
  "tablet-wide": 850px,
  "tablet": 768px,
  "tablet-small": 720px,
  "phone-wide": 600px,
  "phone": 480px,
  "phone-small": 400px,
  "mini": 375px,
);
```

---

### Media Queries

This is a helpful mixin to generate media queries automatically that is mobile first. When support is added to browsers, the query range syntax is preferred.

Mixin:
```css
@mixin mq($width, $type: ">=") {
  @if map_has_key($breakpoints, $width) {
    $width: map_get($breakpoints, $width);
  }
  // For the future
  // @media only screen and (width #{$type} $width) {
  //   @content;
  // }

  @if $type == ">=" {
    @media only screen and (min-width: $width) {
      @content;
    }
  } @else if $type == "<=" {
    @media only screen and (max-width: $width) {
      @content;
    }
  } @else if $type == ">" {
    @media only screen and (min-width: $width + 1px) {
      @content;
    }
  } @else if $type == "<" {
    @media only screen and (max-width: $width - 1px) {
      @content;
    }
  }
}

```

```css
/* Usage: */

@include mq('tablet') {
  ... styles
}
```


---

### Container Queries

By default, the container query mixin will take a mobile first approach. When support is added to browsers, the query range syntax is preferred.

To use you need to define a container first by 

```css
  container: container-name / container-type;
```
  Example usage:
```css
  container: product-card / inline-size;
```
  You can also define the name and type seperatly and can be used on different elements. 
```css
  container-name: product-card;
  container-type: inline-size;
```
Mixin:

```css
@mixin container($width, $containerName: "", $type: ">=") {
  $widthValue: null;

  // Check if the width is a key in the breakpoints map and get the corresponding value
  @if map_has_key($breakpoints, $width) {
    $widthValue: map_get($breakpoints, $width);
  } @else {
    $widthValue: $width;
  }

  // For the future
  // @container #{$containerName} (width #{$type} #{$width}) {
  //   @content;
  // }

  @if $type == ">=" {
    @container #{$containerName} (min-width: #{$widthValue}) {
      @content;
    }
  } @else if $type == "<=" {
    @container #{$containerName} (max-width: #{$widthValue}) {
      @content;
    }
  } @else if $type == ">" {
    @container #{$containerName} (min-width: #{($widthValue + 1px)}) {
      @content;
    }
  } @else if $type == "<" {
    @container #{$containerName} (max-width: #{($widthValue + 1px)}) {
      @content;
    }
  }
}
```

```css
/* Usage */

.container {
  container: product-card / inline-size;
}

@include container('tablet', 'product-card') {
  ... styles
}
```

---

### Clearing Floats

There are many ways to clear a float, but the following does it in the most efficient way possible. Support is IE8 and above.

Note: Please do not use floats for layout. Use Flexbox or Grid.

##### CSS

```css
/* Use as a class */
.clear-fix:after {
  content: "";
  display: table;
  clear: both;
}
```

##### SCSS

```css
/* Use as a mixin */
@mixin clear-fix() {
  .clear-fix {
    &:after {
      content: "";
      display: table;
      clear: both;
    }
  }
}

/* Usage */
.example {
  @include clear-fix();
}
```

---
### Rem Units

Using rem units gives us flexibility in our designs, and the ability to scale elements up and down, instead of being stuck with fixed sizes. We can use this flexibility to make our designs easier to adjust during development, more responsive, and to allow browser users to control the overall scale of sites for maximum readability.

With this rem conversion you can automatically convert a px unit into a rem.

##### SCSS

```css
/* Requires custom property without unit */
--base-font-size-strip: 16;
```

```css
@use "sass:math";

@function rem($value) {
  @return calc(#{$value} / var(--base-font-size-strip) * 1rem);
}

/* Usage */
p {
  font-size: rem(20);
}
```

---
### Box Sizing Mixin

Mixin for defining box sizing.

Mixin:
```css
@mixin box-sizing($sizing: border-box) {
     -moz-box-sizing: $sizing;
  -webkit-box-sizing: $sizing;
          box-sizing: $sizing;
}
```

```css
/* Usage */
@include box-sizing();
```
