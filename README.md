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

The following is the base folder structure for any project. The assets folders location may vary, but would 
ideally sit in a development folder with only the compiled CSS source being deployed to the build folder.

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


#### Images
The only convention to follow here is the sprites folder. All individual sprite image should be stored in this folder 
which compass will use to compile a spritesheet. All sprites must be in .png format. If you are unfamiliar with 
[Compass](http://compass-style.org/) and [compiling spritesheets](http://compass-style.org/help/tutorials/spriting/) please refer to the documentation before using this. If using a spritesheet from a third party it must go in the 
'vendor' folder. If using an existing manual spritesheet create a separate folder with the images directory.

#### Scripts 
These guide lines make no assumptions of JavaScripts. JavaScript coding conventions are covered [elsewhere](#).

#### Styles
The styles folder has two sub-folders: scss and css. All uncompiled SASS files exist in this directory. The folder 
must be named 'scss' as this is the SASS syntax used. SASS will compile to a minified single .css file that will be 
outputted to the 'css' folder. 

The 'base' folder contains all boilerplate, resets and normalisation stylesheets aswell as constants and typography. 
The specifics of these will be covered later.

#### Vendor

This folder will contain all third party JavaScript or CSS code. 

## Formatting

### Formatting Rules

The following are basic formatting rules that MUST be followed: 

* Use tabs consisting of 4 spaces.
* 1 space after : in property declarations.
* 1 space before { in rule declarations.
* 1 line return after { in rule declations.
* 1 line return after } in rule declations.
* Curley braces must appear on their own line.
* Use hex color codes (#000).
* All propery declartions and rule declations to be lower case.
* Rule declarations to use dashes (-) in place of spaces.

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
