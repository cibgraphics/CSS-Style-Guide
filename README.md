# CSS Style Guide

This document defines formatting and style rules for HTML and CSS. It aims at improving collaboration, code quality, and enabling supporting infrastructure. It applies to raw, working files that use HTML and CSS. Tools are free to obfuscate, minify, and compile as long as the general code quality is maintained.

## Table of Contents
1. [General Meta Rules](#general-meta-rules)
2. [CSS Formatting Rules](#css-formatting-rules)
3. [CSS Style Rules](#css-style-rules)
4. [CSS Meta Rules](#css-meta-rules)
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

```html
<ul>
  <li></li>
  <li></li>
  <li></li>
</ul>
```

```css
.example {
  color: blue;
}
```

### Capitalization

Use only lowercase.

All code has to be lowercase: This applies to HTML element names, attributes, attribute values (unless text/CDATA), CSS selectors, properties, and property values (with the exception of strings).

```html
<!-- Not Recommended -->
<A HREF="#">Home</A>

<!-- Recommended -->
<a href="#">Home</a>
```

```css
/* Not recommended */
color: #E5E5E5;

/* Recommended */
color: #e5e5e5;
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

## CSS Style Rules

## CSS Meta Rules

## General HTML Formatting Rules