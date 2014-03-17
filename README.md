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
    * [Naming](#naming)
    * [IDs vs Classes](#ids-vs-classes)
    * [Depth of aplicability](#depth-of-aplicability)
    * [Selector intent](#selector-intent)
    * [Project dependencies](#project-dependencies)
* [Media](#media)
    * [Image naming](#image-naming)
    * [Sprite compilation](#sprite-compilation)
* [CSS3](#css3)
    * [Progressive enhancement](#progressive-enhancement)
* [Proprocessors](#preprocessors)
* [Patterns](#patterns)
    * [Components](#components)
    * [Layouts](#layouts)
    * [OOCSS](#oocss)
    * [Trumps](#trumps)

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
        │        ├── trumps
        │        |   └──_trumps.scss
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

_styles.scss should be structured in the following order:

```
   /* SPRITE SHEET IMPORT */
   @import "../images/sprites/*.png";
   @include all-sprites-sprites;
   
   /* Core */
   @import 'core/_compass';
   @import 'core/_constants';
   @import 'core/_grid';
   @import 'core/_normalise';
   @import 'core/_palette';
   @import 'core/_typography';
   @import 'core/_core-layout';
   
   /* Mixins */
   @import 'mixins/_media-queries';
   
   /* Component list */
   @import 'components/_example-component';
   
   /* Objects */
   @import 'objects/example-oocss-classes';
   
   /* Trumps */
   @import 'trumps/_trumps';
```

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
The conventions and naming of these guidelines is reliant on the practices setout in [BEM](http://bem.info/method/), those not aware of BEM should familiarise themselves with the main principles first. Only some principles of BEM have been adopted in this document. 

The methodology covered in this guide should be implemented in all projects, without exception. Projects are constantly subject to change and it is not always easy to know what size project may or maynot require a scalable solution. With that in mind, all projects should be built assuming the need for scalability. 

### Naming

CSS should not directly reference elements. Each element that requires styling should have a classname associated with it.

When naming elements, be sure to follow the BEM naming pattern:

    .block {}
    .block__element {}
    .block--modifier {}
    
***block*** is for highlevel elements, such as `.primary-navigation`.

***element*** would be an item within the block, such as `.primary-navigation__link`.

***modifier*** is any variation on an existing item. If we had an active link state for the code above, it would look like: `.primary-navigation__link--active`. In this example, the modifier would only contain the code that changes.

For more information, [refer to this article](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/).

### IDs vs Classes
IDs should NEVER be used in CSS for the following reasons:

* IDs tightly couple a style to specific markup, making that element unusable in any other situation.
* The specificity of that style rule is much harder to override in instances where you need to.
* An ID is intended to signify a specific item on a page, where as your CSS is more concenred with style over function.

Classes are intended to be resuable, as therefore your CSS should be reusable too.

### Depth-of-aplicability
The 'Depth of aplicability' is the number of selectors used in a rule. This is a brief overview, but more information is [available](http://smacss.com/book/applicability). Put simply, you should NEVER exceed 4 levels of depth, 3 levels is preffered. 

Over qualifying selectors with many levels make them harder to amend and tie your CSS specifically to the markup. Take the following example:

 `div.nav ul li a {color: red;}`
 
 This markup tighly binds the intended layout to that exact markup. The following would be preffered:
 
  `.navigation .navigation__navigation-item__link {color: red;}`
    
 In the second example, we reference no elements directly and only go to two levels of aplicability. This means if we have to override the class later, we have more freedom to do so. We only use `.navigation ` to namespace the code as pertaining to the link.
 
### Selector Intent

The concept of selector intent is related to the above section. Classes should target the elements they wish to change directly, instead of targetting a parent element and drilling down with element selectors. Never assume the markup will not change and instead be explicit and target the elements you intend to target.

Selector intend and aplicability should go hand in hand.

Please refer to [this article](http://csswizardry.com/2012/07/shoot-to-kill-css-selector-intent/) for more information on the subject.
 
### Project dependencies

As we assume the use of SASS, please make sure you provide documentation for all compiling rules. If you use Grunt, ensure your Grunt.js file is clearly visible and relevant build steps and clearly stated. In this default build, there is a 'watch' file. This documents how to compile the SASS for a base build and should ***always*** be present in builds where SASS is required and Grunt is not being used.
 
## Media

### Image Naming

* All assets should be lowercase
* Assets should not contain spaces
* Only use hyphens to separate words
* Sprites should be in a 'sprites' folder
* Assets should have a descriptive, human readable names
* Avoid names containing numbers where possible

### Sprite Compilation
    
## CSS3 

### Progressive Enhancement
Apply the following principles to markup:

* Create all markup and CSS to ensure the content is accessible
* Use 'forward facing' selectors; assume support but target fallbacks using 'no-' prefixes

## Preprocessors

It is generally accepted that [SASS](http://sass-lang.com/) will be used on a project. Please ensure you have the latest version of SASS installed before starting a project.

All variables should be defined in either ***_constants.scss*** or *** _palette.scss***, both of which should be in the ***core*** folder. 

As per the rules on [aplicability](#depth-of-aplicability), nesting in SASS should be limited to only situations where it is necessary. For components, it is permitted to use the name of the file (for example, 'primary-nav') as a namespace and nest all elements inside this. Nesting of pseudo states and pseudo elements is also permitted, for readability. In all other situations maintian intendation using tabs to visually signify the elements are related, ie:

***GOOD:***
```
   .primary-navigation {
      /* example */
   }
   
      .primary-navigation .primary-navigation__item {
         /* example */
      }
```
***BAD:***
```
   .primary-navigation {
      /* example */
   
      .primary-navigation__item {
         /* example */
      }
   }
```

The following examples would be accepted:

***GOOD:***
```
   .primary-navigation {
      /* example */
   }
   
      .primary-navigation .primary-navigation__item {
         /* example */
         
         .ie8 & {
            /* Browser specific code */
         }
         
         &:hover {
            /* state specific code */
         }
      }
```
   
## Patterns

### Components
As per [folder structure](#file-structure), code should be organised into components. A component is any part of markup that can be broken in to a self contained item. Components should be written to be as reusable as possible, even if there appears to be no place where they are currently reused, this may change much later in the project.

Write markup before writing any styles. This will avoid the possibility of redundant styles. Maintain a [single responsibility principle](http://en.wikipedia.org/wiki/Single_responsibility_principle) when writing a component to ensure no styling is only being applied to places where it does not make logical sense. In some instances a module will need an override depending on where it appears (i.e. a navigation may have less margin when it appears in the header). When this occurs make sure the override class appears in the file related to the component, like this:

***GOOD: _primary-navigation.scss***
```
   .navigation {
      margin: 10px 0 0 0;
   
      .header & {
         margin: 0;
      }
   }
```

***BAD: _header.scss***
```
   .header {
      
      .navigation {
         margin: 0;
      }
   }
```

The logic here is that another developer is more likely to check ***_navigation.scss*** for overrides, rather than ***_header.scss***.

### Layouts
All components should be built independant of widths and heights. The structure and position of components should be applied by grids, meaning components are flexible within these grid columns. No styles should ever be applied to grids - grids are soley concerned with the layout and structure of content, not the content themselves.

### OOCSS
Where possible, look for instances where rules or patterns can be abstracted into reusable sections. OOCSS classes should be mainly structure and not 'skin'. Consider the following example:

```
   (in _primary-navigation.scss)

   .primary-navigation {
   
      .primary-navigation .navigation-list {
         margin: 0;
         padding: 0;
         list-style-type: none;
      }
   }
   
   (in _secondary-navigation.scss)

   .secondary-navigation {
   
      .secondary-navigation .secondary-list {
         margin: 0;
         padding: 0;
         list-style-type: none;
      }
   }
```

The classes .secondary-list and .primary-list could both be removed and replaced with the following:

```
   .vertical-list {
      margin: 0;
      padding: 0;
      list-style-type: none;
   }
```

### Trump classes
Trump classes are classes that can be applied to any component to override specific behaviour. All trumps should be in _trumps.scss and should be specified last in the styles.scss. This is to ensure trumps have maximum effect when being applied.

The following is an example of a trump class:

```
   .is-hidden {
      display: none;
   }
```

It is acceptable for trump classes to contain ` !important ` for the means to override a property. Trump classes should not reference any classes, for example:

```
   .is-hidden {
      display: none;
      
      .primary-navigation & {
         /* implementation specific feature */
      }
   }
```

If you find that this is the only way for your code to work, it is likely that your have either specified the _trumps.scss too early, or have too many levels of aplicability in your classes.
