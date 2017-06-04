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
    ```
    sudo apt-get install ruby-full
    ```
  * On a Windows machine, you'll have to go through the Ruby Installerr setup, a simple program that helps install and run Ruby.
  
####  Installing Sass

  * To install it, open a terminal window. Then type in the following command:
    ```
    gem install sass
    ```
  * Sass is now installed on your machine and you can use the sass command to compile your stylesheets.
  
####  Using Sass

  * The Sass gem provides a sass command that accepts a lot of options.
  * In its simplest form, the sass command accepts an input and an output file, like so:
    ```
    sass input.scss output.css
    ```
  * We can use a watcher programmer to detect when a file is being changed and execute a task when it happens.
  * Sass comes with a built-in watch features: the --watch option. Every time the input file is being modified, Sass will recompile it and override the output file:
    ```
    sass --watch input.scss output.css
    ```
  * You will want Sass to compile the whole folder without having to specify a list of files manually. This is how you do it:
    ```
    sass --watch sass/:stylesheet/.
    ```
### LibSass (with node-sass)

  * LibSass is unusuable on its own and must be wrapped by another library to provide an inteerface for compiling Sass stylesheets to CSS.
  
####  Installing Node.js

  * The easiest way to install Node.js is by using one of the installers on the homepage of the project. Once done, you'll be able to install node packages.
  
####  Installing node-sass

  * Node-sass is a Node package distributed through npm. 
  * It provides both a command-line interface and a JavaScript API to interact with the inner program.
  * Your first task is to install it - either locally in the project with --save or globally with -g:
    ```
    npm install node-sass -g
    ```
####  Using Sass

  * Compiling a single file to CSS is the same as with Ruby Sass:
    ```
    node-sass input.scss output.css
    ```
  * You can also add the --watch flag in the same fashion to tell Sass to automatically recompile the file on change:
    ```
    node-sass --watch input.scss output.css
    ```
  * However, it's slightly different when you want to watch a folder:
    ```
    node-sass --watch sass/ --output stylesheets/
    ```
##  Variables

  * A variable is a storage location paired with an associated identified (aka a variable name).
  * So a variable is basically made up of a key and a value, the former being used to retrieve the latter.
  
  * Ex:
    ```
    //Variable assignment
    $my-variable: 42px;
    
    //Variable usage
    .foo{
     width: $my-variable;
    }
    ```
  * Dashes + Underscores = Same
    * Dashes and underscores are considered the strict equivalent in variable names; hence, $my-variable and $my_variable actuallt refer to the same location.
    
###  Data Types

 * There are seven data types in SassScript:
   * string (e.g. "Hello world", kittens)
   * number (e.g. 42, 1337px)
   * color (e.g. hotpink, rbg(1,33,7), #BADA55)
   * list (e.g. (a,b,c), a b c)
   * map (e.g. (a: 1, b:2))
   * bool (true or false)
   * null (null)
   
#### Strings

  * A string is nothing more than a series of characters, such as Hello World!:
   ```
   $my-variable: 'Hello world!';
   ```
  * In Sass, strings do not have to be quoted. It is perfectly fine for a string to live by itself without being wrapped withing quotes, as long as non-identifier characters are escaped.
  * An unquoted string is strictly equivalent to its quoted counterpart, so that "abc" (or 'abc') is the same as abc.
  * String variables are useful for storing some CSS values, property anems, or identifiers, such as sans-serif, left, or margin-bottom.
   ```
   $font-name: 'Helvetica';
   $font-type:  sans-serif;
   
   .foo {
    font-family: $helvetica, $font-type;
   }
   ```  
  * Strings can be concatenated (joined together) using the plus symbol (+). You can thus create a new string from several chunks:
   ```
   $base-path: '/images/';
   $file-name: 'kittens';
   $extension: 'png';
   $file-path: $base-path + $file-name + '.' + $extension;
   // -> '/images/kittens.png'
   ```
 
#### Numbers
 
  * A number in Sass can - but does not necessarily - have a unit, like 42px.
    * Both 42 and 42px are numbers, while 42 px and px42 are strings.
  * You want to make those values easily configurable in order to keep the codebase clean and maintainable:
    ```
    $container-max-width: 1180px;
    .container {
      width:  100%;
      margin: 0 auto;
      max-width:  $container-max-width;
    }
    ```
  * Sass supports the five basic operators: plus (+), minus (-), multiply (*), divide (/), and modulo (%).
  * Some Sass third-party tools such as Compass^2 or SassyMath^3 add extra math features.
    ```
    $element-width: 400px;
    /**
    * 1.  Size the element
    * 2.  Horizontally center the element in its container
    *     @TODO: move to CSS transforms once we drop support for IE 8
    */
    
    .foo {
      width:  $element-width; /* 1 */
      position: absolute; /* 2 */
      left: 50%;  /* 2 */
      margin-left: ($element-width / -2); /* 2 */
    }
    ```
  * There are three scenarios in which Sass does perform division instead of leaving the / as authored:
    * If the value, or any part of it, is stored in a variable or returned by a function.
    * If the value is surrounded by parentheses.
    * If the value is used as part of another arithmetic expression.
  * The following code snippet illustrates these scenarios:
    ```
    .foo {
      $gap: 20px;
      // No variable nore parentheses: no division performed 
      font: 16px / 2 sans-serif;
      // Wrapping parentheses: division returning 8px
      padding: (16px / 2);
      // Member as variable: division returning 10px
      margin: $gap / 2;
      // Arithmetic expression: calculation returning 308px
      width: 300px + 16px / 2;
    }
    ```
 
##### Units
 
  * Units are not just random strings living at the end of numbers; they actually belong to the number.
  * The next two examples produce entirely different results:
    ```
    $value: 42;
    $good: $value * 1px;
    $bad: $value + px;
    ```
    * The $good variable multiplies $value with 1px, making the result 42px, a valid number.
    * On the other hand, the $bad variable simply appends the px string at the end of $value, composing a string.
    * Having a string in place of a number is not only inconsistent, it can bring new issues, such as it being impossible to perform any further mathematical operations on it.
  * To have 42px from 42, you need to multiply it by one member of the px unit (1px). 
  * Similarly, to have 42 from 42px, you have to divide it by one member of the px unit (1px):
    ```
    $initial-value: 42;
    $value-in-px: ($initial-value * 1px); //42px
    $unitless-value: ($value-in-px / 1px);  //42
    ```
 
#### Colors
 
  * A color is Sass can be expressed in three to four different ways, using:
    * the rgb(..)/rgba(..) CSS functions (for example, rgb(1,33,7)),
    * the hsl(..)/hsla(..) CSS functions (for example, hsla(1,33%,7%,0.5)),
    * the hexadecimal notation (for example, #BADA55)
    * when available, a keyword name (for example, hotpink)
  
  * Avoid Color Keywords
    * CSS color keywords are not reccommended, unless for rapid prototyping.
    * Indeed, as English words some of them do a poor job at describing the color they represent, especially for non-native speakers.
  
  * By keeping frequently-used colors in variables, we save ourselves from guessing and inventing new colors:
    ```
    $brand-color: #BADA55;
    
    .logo {
      color: $brand-color;
    }
    ```
  * Sass native color-manipulation functions, such as darken(..), lighten(..), and mix(..). Let's now consider an alert module with different themes depending on the type of message (information, warning, confirm):
    ```
    .message {
      padding: 10px;
      border: 1px solid currentcolor;
    }
    
    .message-info {
      $color: blue;
      color: $color;
      background-color: lighten($color, 20%);
    }
    
    .message-danger {
      $color: red;
      color: $color;
      background-color: lighten($color, 20%);
    }
    
    .message-confirm {
      $color: green;
      color: $color;
      background-color: lighten($color, 20%);
    
    }
    ```
    
#### Booleans

  * There are only two boolean values: true and false.
  * Here's a short example:
    ```
    $support-legacy-browsers: true;
    
    @if $support-legacy-browsers {
      .clearfix {
        *zoom: 1;
      }
    }
    
    .clearfix:after {
      content: '';
      display: table;
      clear: both;
    }
    ```
  
  * The not keyword
    * Sass lacks a bang operator (!) to get the opposite of a value, such as if (!value). Instead, it provides the not keyword, which works the same way:
    ```
    $bool: false;
    
    // "if not false"
    // which can be rewritten as: "if true"
    @if not $bool {
      // We get in there
    }
    ```

  * Bang bang not not
    * The very popular "bang bang you're a boolean" technique (!!value) to coerce a value to a boolean is doable in Sass by chaining two not keywords:
    ```
    $value: 'Hello world';
    $coerced-value: not not $value; // true
    ```
    * A falsy value would return false, while a truthy value would return true.
    * In Sass, only two values are falsy: false and null, so anything else returns true.
    
#### Null

  * Null is both the value and its type, making it a very specific element of the Sass language.
  * Note that it has to be lowercase and unquoted for it to be from null tye; NULL or any variant containing uppercase letters is from type string:
    ```
    $type: type-of(null); //  null
    $type: type-of(NULL); //  string
    $type: type-of('null'); //  string
    $type: type-of('n' + 'u' + 'LL'); //string
    ```
  * null is commonly used to describe an empty value that will be filled later on, or an empty state that's neither true nor false.
  * null has a very handy behavior: when evaluated as a CSS value, Sass will omit the declaration altogether:
    ```
    $value: null;
    
    .foo {
      // This declaration will not be output since
      // The variable is evaluated as 'null'
      color: $value;
    }
    ```
  * Instead of testing each argument to see if it has a value, we can take advantage of a null value not being output:
    ```
    @mixin absolute($top: null, $right: null, $bottom: null, $left: null) {
      position: absolute;
      top: $top;
      right: $right;
      bottom: $bottom;
      left: $left;
    }
    ```
  * Here's an example:
    ```
    .foo {
      @include absolute($top: 13px, $left: 37px);
    }
    ```
  * The Sass snippet would be compiled to:
    ```
    .foo {
      position: absolute;
      top: 13px;
      left: 37px;
    }
    ```
    
#### Lists

  * They are basically what other languages call arrays.
  * Arrays are often used to store a collection of related values, usually to iterate over them in order to perform a repeated action.
  * A Sass list is a collection of zero or more values separated by either spaces or commas.
  * Values from a list can be of any type, including list, leading to nested lists:
    ```
    $list: (42, hotpink, 'kittens');
    ```
  * The first point to know about lists is that it's the delimiter that makes a list, not the wrapping parentheses. 
  * Parentheses are optional unless the list is empty.
    ```
    $empty-list: ();
    ```
  * Any two or more values separated by a space or a comma form a list:
    ```
    $value: Hello world;
    $type: type-of($value); //  list
    $length: length($value); //  2
    $separator: list-separator($value); //  space
    ```
` * To make it an explicit string, wrap it in (single or double) quotes. Here's another - preferred - way of describing the previous list:
    ```
    $value: ('Hello', 'world');
    $type: type-of($value); //  list
    $length: length($value); //  2
    $separator: list-separator($value); //  comma  
    ```
  * While it's possible to call list-related functions on single values, it does not make the value an actual list:
    ```
    $value: 'foo';
    $length: length($value);  //1
    $type: type-of($value); // string
    ```
  * Sass allows lists that use a comma as a separator to have a trailing comma after the last value. By adding a trailing comma to any value, Sass coerces it into a list:
    ```
    $value: ('foo',);
    $length: length($value);  //1
    $type: type-of($value); // list
    ```
    * Lengthy matters
       * The length(..) function returns the length of a value (which might be greater than one for lists and maps), but not the length of a string! To count the number of characters in a string, use str-length(..).
       
#### Maps

  * A map is a series of pairs of associated keys and values where keys are unique to each map.
  * A map uses its keys to find their associated value.
  * You would use a list when you need an index, and a map when you need a key (such as a string):
    ```
    $message-themes: (
      'info': deepskyblue,
      'danger': tomato,
      'warning': gold,
      'confirm': lightgreen,
    );  
    ```
  * You can pick a specific value from the map based on its key using the map-get(..) function:
    ```
    .message-info { color: map-get($message-themes, 'info');  }
    .message-danger  {  color: map-get($message-themes, 'danger'); }
    .message-warning  { color: map-get($message-themes, 'warning'); }
    .message-confirm  { color: map-get($message-themes, 'confirm'); }
    ```
  * Keys of a map can be of any type and not just strings. Yes, lists and maps as well, although they have to remain unique:
    ```
    $color-names: (
      #ff0000: 'blood';
      #00ff00: 'grass';
      #0000ff: 'ocean';
    );
    ```
  * No trails with the trailing comma
    * It is possible to add a trailing comma to the last pair of a map. I would indeed recommend doing so as it makes adding new values easier, and git diffs simpler.
  * Empty Maps
    * An empty map is described exactly like an empty list [()]. Therefore, when testing the type of the () value with the type-of(..) function, it returns list (as maps were added to the language later on).
    
### Scope

  * Depending on where a variable is assigned, however, its access might be restricted to a specific code block; this is what we usually call a scope.
  * A variable defined in a mixin, function, or rule set is local by default.  This means that a global variable and a local variable can share the same name seamlessly: the local will be restricted to its own scope, while the global will be accesible elsewhere in the document.  This is reffered to as variable shadowing in Sass.
  * When declaring in an inner scope a variable whose name already exists in the global namespace, the local variable is said to be shadowing the global one:
   ```
   $padding: 10px;
   
   .module {
    $padding: 20px;
    padding: $padding; // 20px
    
   .foo {
    padding: $padding; // 10px
   } 
   
   ```
   * Within the scope, the value of $padding is now 20px, but anywhere else in the document, it still refers to the global value, 10px.  Thus, the code snippet will be compiled to:
   ```
   .module {
    padding: 20px;
   }
   
   .foo {
     padding: 10px;
   }
   ```
  * The !global Flag
    * To definitely override a global variable from a local scope, we use the !global flag.
      * The variable will not be overshadowed but effectively replaced by a new value.
  * Ex:
    ```
    $padding: 10px;
    
    .module {
     $padding: 20px !global;
     padding: $padding; //20px
    }
    
    .foo {
     padding: $padding; //20px
    }
    ```
  * The !default Flag
    * The !default flag makes it possible to assign a variable if it doesn't have a value yet:
    ```
    $padding: 10px;
    $padding: 20px !default;
    
    .foo {
      padding: $padding;  //10px
    }
    ```
    * It's recommended that you use !default when declaring default configuration variables.
    * The default flag is incredibly useful when building third-party libraries and modules. It enables users to configure the library, but still provide defaults if they don't:
     ```
     // You configuration of the third party library
     $third-party-output-prefix: false;
     
     // The third party library has some default values such as 
     // $third-party-output-prefixL true !default;
     // In this case, the value is 'false' thanks to '!default'.
     @import 'third-party-library';
     ```
    * The !default flag also comes in handy when dealing with dynamically created Sass files from user input, such as theme files:
    ```
    // User theme stylesheet containing:
    // $brand-color: hotpink;
    @import 'user-theme';
    
    // Default configuration
    $brand-color: grey !default;
    
    /foo {
      color: $brand-color;  // hotpink
    }
    ```
    * Bear in mind that variables with null value are treated as unassigned by default, which means that a variable assignment with !default will override a variable assignment to null:
    ```
    $padding: null;
    $padding: 20px !default;
    
    .foo {
      padding: $padding; // 20px
    }
    ```

### Interpolation

  * Interpolation is often referred to as variable interpolation or variable substitution.
  * Interpolating is the process of evaluating an expression or a string containing one or more variables, yielding a result in which the variables are replaced with their corresponding values in memory.
  * Thanks to variable interpolation, we can have a string containing variable(s) without having to concatenate several string chunks:
   ```
   $name: 'Hugo';
   
   .foo {
    content: 'Hello #{$name}!';
   }
   ```
    * By wrapping a variable identifier with #{}, it tells Sass to treat the content of the variable as plain CSS.
  * One of the most common use cases for interpolating a variable is within the calc(..) CSS function.
   ```
   .main {
    $sidebar-width: 300px;
    width: calc(100% - #{$sidebar-width});  //  calc(100% - 300px)
   }
   ```
  * Sass will only evaluate Sass variables in a media query if they're within a pair of parentheses. So when dynamically creating media blocks, you need to wrap the whole thing in parentheses.
   ```
   $media: screen;
   $feature: min-width;
   $value: 1337px;
   
   @media #{$media} and ($feature: $value) {
    //  ...
   }
   ```
  * To use a variable in a selector, we have to interpolate it:
   ```
   $section: 'home';
   
   .section-#{$section} {
    background: transparent;
   }
   ```
### Creating Meaningful Variables

  * Use hyphens to separate words within your variables names rather than underscores or camel case:
   ```
   $brand-color: #BADA55;
   ```
  * A constant is an immutable value that, unlike a variable, cannot be reassigned.  Sass does not support actual constants.
  * The variable name should be used to describe the value without explicitly referring to it contents.
  * Store colors in variables with representative names, and then use these in other generic variables where the original meaning is retained:
   ```
   $gold: hsl(42, 78%, 54%);
   $dark-blue: rgb(13,33,70);
   
   $primary-theme-color: $gold;
   $secondary-theme-color: $dark-blue;
   ```
  * Avoid naming your variables after the way they're used such as $border-color.  
    * Later you will use these variables for completely different purposes, and you'll be left with a name that makes little sense, or is misleading even.
    * Don't be too specific with your variable names.
    
### CSS Custom Properties or Sass Variables

  * CSS Custom properties are often referred to as CSS variables.
    * Custom propreties share the same purpose as variables, limiting code repetition by associating value to specific identifies (variable names).
  * Ex:
   ```
   /**
    * Declaring a CSS custom property named 'main-color' at root level
    * so that it is accessible anywhere in the document
    */
   
   :root {
    --main-color: #BADA55;
   }
   
   /**
    * Using the 'main-color' variable through the 'var(..)' function
    */
   
   body {
    background-color: var(--main-color);
   }
   ```
  * It is recommended to declare global variables on: root because it's the root of the document, making those custom properties accessible anywhere in it.
  * Sass variables are scoped and rely on a global scope to be accessible anywhere, while CSS variables respect the cascad principle and should be defined on the uppermos element to flow down the document.
  
##  Functions and Mixins

### Functions

  * A function is a chunk of code that returns a result, possibly accepting arguments.  It's an ideal way to extract repeated pieces of code into a single reusuable pattern.

##  Loops and Conditions

##  Nesting

##  The @extend Directive

##  Warnings and Errors

##  Architecture

##  The Sass Ecosystem
