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

  * Sass (mostly) exists as both a Ruby gem (sometimes called Ruby Sass) and a wrapped C/C++ library (also known as LibSass).

### Ruby Sass

  * The programming language Ruby handles dependencies as gems. 
    * A gem is a package that contaains program information along with files to install.
    * The sass gem is a package containing everything needed to compile Sass stylesheets to CSS.

####  Instally Ruby

  * On Mac OS, Ruby comes preinstalled so there's nothing further to do.
  * On Debian or Ubuntu Linux distributions, you need to install Ruby manually like so:
  
    sudo apt-get install ruby-full
  
  * On a Windows machine, you'll have to go through the Ruby Installerr setup, a simple program that helps install and run Ruby.
  
####  Installing Sass

  * To install it, open a terminal window. Then type in the following command:
  
    gem install sass
    
  * Sass is now installed on your machine and you can use the sass command to compile your stylesheets.
  
####  Using Sass

  * The Sass gem provides a sass command that accepts a lot of options.
  * In its simplest form, the sass command accepts an input and an output file, like so:
  
    sass input.scss output.css
    
  * We can use a watcher programmer to detect when a file is being changed and execute a task when it happens.
  * Sass comes with a built-in watch features: the --watch option. Every time the input file is being modified, Sass will recompile it and override the output file:
  
    sass --watch input.scss output.css
    
  * You will want Sass to compile the whole folder without having to specify a list of files manually. This is how you do it:
  
    sass --watch sass/:stylesheet/.
    
### LibSass (with node-sass)

  * LibSass is unusuable on its own and must be wrapped by another library to provide an inteerface for compiling Sass stylesheets to CSS.
  
####  Installing Node.js

  * The easiest way to install Node.js is by using one of the installers on the homepage of the project. Once done, you'll be able to install node packages.
  
####  Installing node-sass

  * Node-sass is a Node package distributed through npm. 
  * It provides both a command-line interface and a JavaScript API to interact with the inner program.
  * Your first task is to install it - either locally in the project with --save or globally with -g:
  
    npm install node-sass -g
    
####  Using Sass

  * Compiling a single file to CSS is the same as with Ruby Sass:
  
    node-sass input.scss output.css
  
  * You can also add the --watch flag in the same fashion to tell Sass to automatically recompile the file on change:
  
    node-sass --watch input.scss output.css
  
  * However, it's slightly different when you want to watch a folder:

    node-sass --watch sass/ --output stylesheets/

##  Variables

##  Functions and Mixins

##  Loops and Conditions

##  Nesting

##  The @extend Directive

##  Warnings and Errors

##  Architecture

##  The Sass Ecosystem
