##  Document Contents

[Hello World!](#hello-world)

[Getting Started](#getting-started)

[Variables](#variables)

[Functions and Mixins](#functions-and-mixins)

[Loops and Conditions](#loops-and-conditions)

[Nesting](#nesting)

[The @extend Directive](#the-@extend-directive)

[Warnings and Errors](#warnings-and-errors)

[Architecture](#architecture)

[The Sass Ecosystem](#the-sass-ecosystem)

##  Hello World!

### CSS in Modern Front-end Development

  * With modern websites providing more content in various ways and with most web makers adoping an approach that 
  incorporates responsive web design principles, we're now writing more complex CSS than ever before.
  
### What is Sass?

  * Sass is a stylesheet language that is an extension of CSS.
  * It is one of a few preprocessors available to the front-end developer.
  * Described as the "most mature, stable, and powerful professional-grade CSS extension language in the world".
  * Using Sass helps eliminate some of the monotony and overhead from writing CSS.
  * Pros:
      *  Sass can remember a specific hex color code
      *  increased page load times by splitting up your CSS files to several files
      *  Easier way to write media queries
  
### What is preprocessing?

  * Sass is a preprocessor.
  * It takes Sass (.sass) or scss (.scss) files as input, and outputs CSS files (.css).
  * Web browsers only understand CSS, not Sass.
      *  What we do is write our CSS in .scss or .sass files in our code editor, and then have Sass compile that into a .css file for the browser to read.
  * Using a preprocessing language means we're not bound within the limitations of CSS.
  * Sass can add features that enhance our writing of CSS; however, it does not add features to CSS itself.
  
### The Tale of Two Syntaxes

  * Sass (the preprocessor) allows two syntaxes:
      * Sass, also known as the indented syntax
      * SCSS, or Sassy CSS, a CSS-like syntax
  * The rule of thumb is if it is valid CSS, it's valid SCSS
  * Note that "Sass" is never uppercase, no matter whether we're talking about the language or the syntax.
  
####  SassScript

  * You might have heard of SassScript, the actual scripting language used by Sass.
  * The Sass interpreter then translates SassScript into CSS.
  
### LibSass

  * There are two primary implementations of the Sass compiler: one in Ruby, and another (called LibSass) in C/C++.
  
### Alternative Processing Tools

  * Stylus, Less and PostCSS also assist with writing CSS, just like Sass.
      * Stylus is built in Node.js
        * Stylus is usually more permissive, implementing a lot of features that you'd consider "too much for CSS".
        * Stylus is very flexible with the syntax: you can safely omit most bits of punctuation without risking a compilation error
      * Less is fundamentally different to Sass, despite looking similar in a number of ways: it is a declarative language while Sass is imperative.
        * A declarative language describes to a machine what we want, and an imperative language tells the machine how to do it.
      * PostCSS has a different approach as it does nothing more in itself than read your stylesheet.
        * To actually create something out of this tool, you have to configure plugins.
        * A plugin is basically an instruction for PostCSS to translate one thing into another.
        * PostCSS enjoys an ecosystem of hundreds of plugins.

##  Getting Started

##  Variables

##  Functions and Mixins

##  Loops and Conditions

##  Nesting

##  The @extend Directive

##  Warnings and Errors

##  Architecture

##  The Sass Ecosystem
