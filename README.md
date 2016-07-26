# CSS Style Guide

This document defines formatting and style rules for HTML and CSS. It aims at improving collaboration, code quality, and enabling supporting infrastructure. It applies to raw, working files that use HTML and CSS. Tools are free to obfuscate, minify, and compile as long as the general code quality is maintained.

## Table of Contents
1. [General Meta Rules](#general-meta-rules)
  * [Protocal](#protocal)
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
5. [General HTML Formatting Rules](#general-html-formatting-rules)

## General Meta Rules

### Protocol

Omit the protocol portion (http:, https:) from URLs pointing to external stylesheets and other media files unless the respective files are not available over both protocols.

```html
<!-- Not recommended -->
<link href="https://www.example.com/style.css" rel="stylesheet" media="screen" />

<!-- Recommended -->
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

### Block Content Indentation

Indent all block content

```css
@media screen, projection {

  html {
    color: blue;
  }

}
```

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

### Trailing White Space

Remove trailing white spaces.

Trailing white spaces are unnecessary and can complicate diffs.

```css
/* Not Recommended */
.example {
  color: blue;_
}

/* Recommended*/
.example {
  color: blue;
}
```

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

### Selector and Declaration Separation

Separate new selectors and declarations by new lines

```css
/* Not Recommend */
h1, h2 {
  font-weight: normal; top: 1px;
}

/* Not Recommend */
.example { display: block; }

/* Recommended */
h1,
h2 {
  font-weight: normal;
  top: 1px;
}
```

### Rule Separation

Separate new rules by news lines

Always put a blank line (two line breaks) between rules

```css
html {
  font-size: 12px;
}

body {
  margin: auto;
}
```

### CSS Quotation Marks

Use a single quote for attribute selectors and property values.

Do not use quotation marks for URL values.

Exception: If you do need to use the @charset rule, use double quotation marks

```css
/* Not Recommend */
html {
  font-family: "open sans", arial, sans-serif;
  background: url('example.jpg');
}

/* Recommended */
html {
  font-family: 'open sans', arial, sans-serif;
  background: url(example.jpg);
}
```

## CSS Style Rules

### CSS Validity

Use valid CSS where possible

Use only valid CSS code using such tools as the [W3C CSS Validator](https://jigsaw.w3.org/css-validator/). Validations tools can not spot all errors and may even give false positives for newer valid CSS. Take care to note that valid CSS can still contain visual bugs as support and implementation of properties can vary from browser to browser.

### ID and Classes

Use classes for modularity.

For general page styling uses classes. ID's should be reserved for special cases or hooks into other languages such as Javascript.

### ID and Class Naming

Use meaningful or generic ID or class names

Use ID and class names that reflect the purpose of the element in question, or that is otherwise generic that can be used anywhere needed. Names that reflect presentational or cryptic in nature should be avoided.

```css
/* Not Recommended */
.ml20 {}
.blue {}

/* Recommended */
.video {}
.login {}
```

### ID and Class Name Delimiters

Separate ID and class names by hyphens

Do not use underscores, camel case, double hyphens, or any other delimiters.

```css
/* Not Recommended */
.demoImage {}
.error_status {}

/* Recommended */
.demo-image {}
.error-status {}
```

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

### Type Selectors

Avoid qualifying ID and class names with type selectors.

```css
/* Not Recommended */
div.example {}

/* Recommended */
.example {}
```

### Shorthand Properties

Use shorthand properties where possible.

Using shorthand properties is useful for code efficiency and understandability.

```css
/* Not Recommended */
margin-right: 20px;
margin-bottom: 10px;
margin-left: 10px;

/* Recommended */
margin: 0 20px 10px 10px;
```

### 0 and Units

Omit units after "0" values.

```css
margin: 0;
padding: 0;
```

### Leading 0s

Omit leading 0s in values.

```css
font-size: .8rem;
```

### Hexadecimal Notation

Use 3 character hexadecimal notation where possible.

```css
/* Not Recommended */
color: #eebbcc

/* Recommended */
color: #ebc
```

### Hacks

Avoid CSS hacks. Try a different approach first.

The days of IE6 are far behind us. Avoid hacks to target specific browsers unless absolutely necessary. Try a different coding approach first before resorting to a "hack".

## CSS Meta Rules

### Encoding

Use UTF-8.

Specify the encoding in HTML via `<meta charset="utf-8">`. Do not specify the encoding of stylesheets as these assume UTF-8

### Comments

Explain code as needed when possible.

Use comments to explain code. What does it cover? What purpose does it serve? Be thoughtful in the amount of comments as a large project can quickly become unmaintainable with too many comments. Leave comments for only technically difficult or confusing parts of code.

### Section Comments

Group sections by a section comment

If possible, group stylesheet sections by using comments

```css
/*
-----------------------------------------
Large Section Comment
-----------------------------------------
*/

/* Small Section Comment*/
```

## General HTML Formatting Rules