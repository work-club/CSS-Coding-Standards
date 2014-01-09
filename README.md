CSS-Coding-Standards
====================

Work Clubs CSS coding standards &amp; guidelines for front-end projects

### Table of contents

This is the table of content

* [Overview](#overview)
    * [What this guide is for](#what-this-guide-is-for)
    * [What this isn't for](#what-this-isnt-for)
    * [Assumptions](#assumptions)
* [File structure](#file-structure)
* [Formatting](#formatting)
    * [Formatting rules](#formatting-rules)
* [Conventions](#conventions)
    * [Naming conventions](#naming-conventions)
* [Rules on specificity](#rules)
    * [Naming](#naming)
    * [IDs vs Classes](#ids-vs-classes)
    * [Depth of aplicability](#depth-of-aplicability)
* [Media](#media)
    * [Image naming](#image-naming)
    * [Sprite compilation](#sprite-compilation)
* [CSS3](#css3)
    * [Progressive enhancement](#progressive-enhancement)
    * [Vendor prefixing](#vendor-prefixing)
* [Patterns](#patterns)
    * [oocss](#oocss)
    * [state-rules](#state-rules)
    * [theming](#theming)

## Overview

This document has been put together by the front-end development team at Work Club, a London based digital agency. 
This document is a reference for all developers in the team to follow. This document is subject to change and 
improvements.
    
### What this guide is for

This document is to be followed by all developers writing CSS on a project, regardless of size or complexity. It's 
intended to be followed to provide consistency across all projects and developers. It will point out good patterns 
and anti-patterns and explain why these should be used or ignored. 

### What this isnt for

This isn't a style guide. This isn't a pattern guide, although we do provide some examples of common patterns 
and how they should be approached, this document won't go in to specific details about things like 
[SMACSS](http://www.smacss.com) or [BEM](http://bem.info/method/). The use of those methodologies will vary 
from project to project whereas this guide is intended to be followed on any project, regardless of size or 
complexity.

### Assumptions

This guide assumes you are using [SASS](http://www.sass-lang.com) to write and compile your CSS. This guide 
will cover a number of patterns and features that aren't possible in native CSS. 

## File Structure


    assets
        ├── images
        │    └── sprites
        │           └── spritsheet.png
        ├── scripts
        │    └── app.js
        │
        ├── styles
        │    └── scss
        │        ├── base
        │        │   ├── _compass.scss
        │        │   ├── _constants.scss
        │        │   ├── _html5bp.scss
        │        │   ├── _normalise.scss
        │        │   ├── _pallette.scss
        │        │   └── _typography.scss
        │        │
        │        ├── components
        │        │   
        │        ├── styles.scss
        │        │
        │        └──css
        │           └── styles.min.css
        │
        └── vendor


## Formatting

### Formatting Rules

## Conventions

### Naming Conventions
    
## Rules

### Naming

### IDs vs Classes

### Depth-of-aplicability
    
## Media

### Image Naming

### Sprite Compilation
    
## CSS3

### Progressive Enhancement

### Vendor Prefixing

## Patterns

### OOCSS

### State rules

### Theming
