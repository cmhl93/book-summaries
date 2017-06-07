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
  * A function definition starts with @function, then the name of the function, then a pair of parentheses. The core of the function is then written between braces ({..}).
  * Here's a function that accepts no arguments and returns the base URL for the assets folder as a string:
  ```
  // The 'get-base-url()' function has no parameter
  @function get-base-url() {
    @return '/assets/';
  }
  
  // Usage
  .module {
    background-image: url(get-base-url() + 'unicorn.png');
  }
  ```
  * If we'd forgotten the @return statement from our previous function, Sass would have thrown:
  ```
  Function get-base-url finished without @return
  ```
  * A function can be defined almost anywhere in a document and not just at root level. When defined within a rule set, a function is scoped to that rule set, the same way variables are local when defined within a specific block.
  * A local function sharing its name with a global one will shadow the latter inside the scope where it's defined:
  ```
  @function get-base-url(..) {
    @return '/assets/';
  }
  
  .module {
    // Shadow 'get-base-url()' functions within '.module {}'
    @function get-base-url() {
      @return 'http://cdn.example.com/assets/';   
    }
    background-image: url(get-base-url() + 'unicorn.png');
  }
  
  .foo {
    background-image: url(get-base-url() + 'kittens.png');
  }
  ```
  * The compiled CSS of this example looks like this:
  ```
  .module {
    background-image: url('http://cdn.example.com/assets/unicorn.png');
  }
  
  .foo {
    background-image: url('/assets/kittens.png');
  }
  ```
  
  * Parameters
    * Parameters and Arguments
      * A parameter is the variable that's part of the function's signature (function declaration). An argument is an expression used when calling the function.
    * Parameters can also have a default value - in which case they are called optional parameters.
    * To define an optional parameter, do as if you were declaring a variable in the function signature (without the closing semicolon):
    ```
    //  '$a' is mandatory and '$b' is optional (default value being 2)
    @function multiply($a, $b: 2) {
      @return ($a * $b);
    }
    ```
    * Note that optional parameters must come after any non-optional parameters (or it will throw an error)
    * When calling a Sass function, you can either pass arguments in the order they are defined, or you can use what we call name arguments or keyword arguments.
    * To use named arguments, do as if you were defining variables in the function call:
    ```
    $element-width: 400px;
    
    .foo {
      // Calling 'multiply(..)' with arguments in the defined order 
      width: multiply($element-width, 3);  // 1200px
      // Calling 'multiply(..)' relying on default value
      // for second parameter
      padding: multiply(10px); //20px
    }
    
    .bar {
      //Calling 'multiply(..)' using keyword arguments
      width: multiply($b: 3, $a: $element-width); // 1200px
    }
    ```
    * These are three benefits of using named arguments over definition order:
    1.  They can be declared in any order
    2.  Arguments are obvious to understand when named
    3.  In functions with many optional parameters, only relevant arguments can be defined, leaving the others to their default value.
    * Here's an example:
    ```
    @function set-color-theme(
      $primary,
      $secondary: darken($primary, 10%),
      $tertiary: lighten($primary, 10%)
    ) {
      //  Do something
    }
    
    $color-theme: set-color-theme(hotpink, $tertiary: pink);
    ```
    * In this example:
      * $primary is passed without being named, simply as a first argument;
      * $secondary is left to its default value;
      * $tertiary is named and set to pink
  
  * Usage      
    * Functions can be used anywhere variables can so within selectors, media queries, properties, values, and inside variables, functions, mixins, and so on.
    * Like variables, they might need to be interpolated when used in unconventional places:
    ```
    //  Just for the sake of demonstration, here's a function declaration
    @function my-function() {
      @return 'foo';
    }
    
    //  Calling the function in itself does not work and throws an error:
    //  > 'Invalid CSS after " my-function(()": expected "{", was ";"'
    .foo {
      my-function();
    }
    
    //  Calling the function in place of a property works as long as it is properly interpolated.
    ```
    
    ```
    .foo {
      #{my-function()}: 'bar';
    }
    
    //  Calling the function in place of a selector works as long as it is properly interpolated.
    .foo, #{my-function} {
      content: 'bar';
    }
    
    //  Calling the function inside a variable value works perfectly.
    $foo: my-function();
    
    //  Calling the function in place of a media query value works perfectly
    @media (min-width: my-function()) { .. }
    
    //  Calling the function in place of a feature query value works perfectly
    @supports (content: my-function()) { .. }
    ```
    
    * Arguments List
      * Functions can have an unknown number of parameters if ever needed. To do so, simply add an ellipsis (...) to the last parameter of the signature:
      ```
      //  'map-deep-get' intends to help getting values
      //  deeply nested in maps
      //  The first parameter is the map to browse
      //  Any parameter after that are keys nested within each others
      @function map-deep-get($map, $keys...) {
        @each $key in $keys {
          $map: map-get($map, $key);
        }
        @return $map;
      }
      ```
      * This type of argument is often referred to as arg-list and is sometimes referred to as variable arguments.
      * arglist is in fact a valid Sass data type that only comes up when dealing with arguments lists.
      * You can loop on an arguments list the way you would a list, and access its items with the nth(..) function the same way:
      ```
      @function dummy($mandatory, $extra-arguments...) {
        //  Do something
      }
      
      $foo: dummy('Hello', 'how', 'are', 'you', '?');
      //  ->  $mandatory: 'Hello'
      //  ->  $extra-arguments: 'how', 'are', 'you', '?'
      ```
      
      * Arguments lists are much more powerful than simply creating aliases, as they can be used to expand a lsit or a map of values into a series of arguments passed to a function or mixin.
      
  * Native Functions
    * Sass provides a lot of built-in functions to make writing styles an easier task.
    * Ex: lighten(..), darken(..), or lists and maps with length(..)
    
### Mixins

  * A mixin is a function that can output code rather than return a result.
  * While a function is a good wway to abstract a repeated operation based on parameters, a mixin is a terrific way to abstract repeated style patterns - all with the ability to adapt the output based on parameters.
  * A mixin can be defined anywhere but inside a function or another mixin.
  * To define it, there's the @mixin notation.
  * As for the function declaration, the name of the mixin comes right after it, and then the parameters.
  * When mixins have no parameters, the parentheses are optional.
  * Ex:
  ```
  @mixin center {
    width: 100%;
    max-width: 1180px;
    margin-left: auto;
    margin-right: auto;
  }
  ```
  * To use a mixin, you have to call it with the @include directive (+ symbol in Sass indented syntax) followed by the name of the mixin.
  * Ex:
  ```
  .container {
    include center;
  }
  ```
  
  * Parameters
    * Mixins will accept parameters since this is where they really kick in.  These parameters can have a default value.
    * The default value of a parameter can be the value of another parameter defined before it.
    * Ex:
      * The default value of the $height parameter is the value of the $width argument:
    ```
    //  Sizing mixin from width and height
    //  If height is omitted, same as width
    //  @param {Length} $width - element width
    //  @param {Length} $height [$width] - element height
    @mixin size($width, $height: $width) {
      width: $width;
      height: $height;
    }
    
    //  Usage
    .foo {
      @include size(100%, 42px);
    }
    
    .bar {
      @include size(100px);
    }
    ```
    * When compiling this code, Sass will render:
    ```
    .foo {
      width: 100%;
      height: 42px;
    }
    
    .bar {
      width: 100px;
      height: 100px;
    }
    ```
  * Inner Content
    * The @content directive allows authors to pass blocks of styles to their mixins.
    * When a mixin has one or more @content directives defined in its core, it can be given custom content between braces ({ and }), like so:
    ```
    @mixin my-mixin {
      @content;
    }
    
    .foo {
      @include my-mixin {
        //  We can add stuff here
      }
    
    }
    ```
    * The @content directive is especially useful when building dynamic selectors or context blocks, such as @media or @supports.
    * @content immutability
      * You store, alter, or iterate the content of a @content directive. What is being passed to a mixin through @content is immutable and unknown.
    * Variables local to a mixin such as those defined in the mixin signature or the mixin scope cannot be used in passed style blocks.
    * They only exist within the mixin scope and not anywhere else.  If you try to use one of those variables in a passed style block, it will either default to the global variable if any, or will simply throw an error:
    ```
    @mixin my-mixin($argument) {
      @content;
    }
    
    //  Does not work and throws an error
    //  > 'Undefined variable: "$argument".'
    .foo {
      @include my-mixin('foo') {
        content: $argument;
      }
    }
    ```
    
##  Loops and Conditions

### Conditions

  * Conditions are a pillar of any piece of software ever written.
    * They are path switches in our programs.
  * The basic conditional structure exists under the form of if condition then...else....
  * Sass uses @if and @else as directives.
  * A conditional structure in Sass always starts with the @if keyword, directly followed by an expression.
  * The code to be executed if the expression matches lives between an opening and a closing brace ({ .. }):
  ```
  @if $condition {
    //  Do something
  } @else {
    //  Do something else
  }
  ```
  * How Sass evaluates the conditions expression to determine which code block to execute:
    * If the result is true, the condition is truthy, otherwise it's said to be falsy.
    * Only two values are falsy in Sass: false and null.
  * If the expression is evaluated to either false or null, the @else block is executed. Otherwise the condition is truthy and the @if block is executed (even for values such as 0, "" or ()).
  
  * Multiple Conditions
    * You can place extra conditions between the first @if and the optional @else statement. These are written using a combination of both keywords, like so: @else if <condition>,
    * Be aware that as soon as a condition is evaluated to true, its code is executed and no other condition in the chain can be matched.
    
  * Conditional Operators
    * Each component of the expression is evaluated on its own, then the results of these evaluations interact with the and and or keywords.
    * Expressions are evaluated from left to right.
    
  * Ternary Functions
    * A ternary operator takes three arguments.
      * The first one is usually a condition that is evaluated, depending on whether its result is truthy or falsy; the second or third argument is returned respectively.
    * Most languages use a syntax borrowed from C, using a question mark (?) after the condition and a colon (:) between the two possible outcomes.
    * Ex:
    ```
    var backgroundColor = error ? 'red' : 'green';
    ```
    * Sass has a ternary function.  The function is appropriately named if(..).
    * The first argument of the if(..) function is the condition, the second one is the result if the condition is truthy, and the third one is returned value if the condition is falsy.  This function is useful when wanting to shorten an @if/@else statement to a single line:
    ```
    $background-color: if($errer, red, green);
    ```
    * If the $error variable is truthy, $background-color will be red, otherwise it will be green. We could have written this using a regular condition as well:
    ```
    $background-color: green;
    
    @if $error {
      $background-color: red;
    }
    ```
    
### Loops

  * The for-loop
    * The for-loop is a logical structure that iterates a given number of times.
    * In Sass, the for-loop expects a starting index and an ending index, and runs as many times as needed from start to end.
    * A for-loop is written as follows:
      1.  The @for directive
      2.  The name of the index variable (usually but not necessarily $i)
      3.  The keyword from
      4.  The start index (as a static number, a variable, or a function call)
      5.  Either the keyword through (end index inclusive) or the keyword to (end index exclusive).
      6.  The end index (as a static number, a variable, or a function call)
    * Ex:
    ```
    @for $i from 1 through 10 {
      .item:nth-child(#{$i}) {
        animation-delay: ($i - 1) * 0.1s;
      }
    }
    ```
      
  * The each-loop
    * The each-loop is a logical structure aiming at iterating over a collection.
    * An each-loop runs as many times as the number of elements in a collection (items in a list, key/value pairs in a map).
    * A simple each-loop is written as follows:
      1.  The @each directive
      2.  The name of the item variable
      3.  The keyword in
      4.  The collection to iterate
    * Ex:
    ```
    $authors: ('hugo', 'miriam');
    
    @each $author in $authors {
      .section-#{$author} {
        background-image: url('/images/authors/#{$author}.jpg');
      }
    } 
    ```
    * Multi-assignment is a feature from Sass each-loops that allows authors to define several variables that can then be accessed in the loop content.  
    * Two variables are better than one
      * When looping through a map with a single variable, it contains the key and the value as a two-item list.  
      * Always define two variables in the loop: one for the key, one for the value.

  * The while-loop
    * a way to execute a chunk of code as long as a condition remains true.  
    * In Sass, it is veery hard to find a decent use case for a while-loop
    * Here is how a while-loop is described in Sass:
      1.  The @while directive
      2.  The matching condition for the loop to keep going
    * Ex:
    ```
    $number: 4;
    
    @while ($number > 0) {
      //  Do something with '$number'
      $number: $number - 1;
    }
    ```
    
##  Nesting

### Selector Nesting

 * Selector nesting, or "nested rules" is the ability to write rule sets within other rule sets that result in composed selectors.
 * Ex:
 ```
 .container {
   margin: 0 auto;
   max-width: 42em;
   padding: 0 1em;
  
   p, li {
    text-indent: 1em;
   }
 }
 ```
 * Compiling this would generate the following CSS code:
 ```
 .container {
   margin: 0 auto;
   max-width: 42em;
   padding: 0 1em;
 }
 
 .container p,
 .container li {
  text-indent: 1em;
 }
 ```
 
 * Variable Scoping
  * Global scoping:
  ```
  $rhythm: 1em;
  
  .container {
    margin: 0 auto;
    max-with: 42em;
    padding: 0 $rhythm;
    
    p {
      text-indent: $rhythm;
    }
  }
  ```
  * Local scoping:
  ```
  .container {
    $rhythm: 1em;
    
    margin: 0 auto;
    max-width: 42em;
    padding: 0 $rhythm;
    
    p {
      text-indent: $rhythm;
    }
  }
  ```
  
  * The Ampersand Selector
    * Nicknamed the parent selector reference
    * It might be useful to dynamically access the parent selector from an inner rule. The & selector does precisely this.
    ```
    .container {
      margin: 0 auto;
      max-width: 42em;
      padding: 0 1em;
      
      p {
        text-indent: 1em;
        
        a {
          color: deeppink;
          
          &:hover,
          &:active {
            color: hotpink;
          } 
        }
      }
    }
    ```
    * The code snippet will be compiled to:
    ```
    .container {
      marginL 0 autol
      max-width: 42em;
      padding: 0 1em;
    }
    
    .container p {
      text-indent: 1em;
    }
    
    .container p a {
      color: deeppink;
    }
    
    .container p a:hover,
    .container p a:active {
      color: hotpink;
    }
    ```
    
    * The ampersand selector can also be followed by a suffix that will be added to the parent selector.
    ```
    .component {
      display: block;
      
      &-hidden {
        display: none;
      }
    }
    ```
    * The following code will be compiled to:
    ```
    .component {
      display: block;
    }
    
    .component-hidden {
      display: none;
    }
    ```
    
### Context Nesting

  * It's the ability to nest a CSS scoping directive or a rule set, such as a media query (@media) or a support query (@supports).
  * Ex #1:
  ```
  @media screen {
    .navigation li {
      display: block;
      
      @media (min-width: 42em) {
        display: inline-block;
      }
    }
  }
  ```
  * The code is then compiled to:
  ```
  @media screen {
    .navgivation li {
      display: block;
    }
  }
  
  @media screen and (min-width: 42em) {
    .navigation li {
      display: inline-block;
    }
  }
  ```
  * Ex #2:
  ```
  .navigation {
    display: block;
    
    @supports (display: flex) {
      display: flex;
    }
  }
  ```
  * The code is then compiled to:
  ```
  .navigation {
    display: block;
  }
  
  @supports (display: flex) {
    .navigation {
      display: flex;
    }
  }
  ```
  
  * The @at-root Directive
    * The @at-root directive was introduced so as to be able to emit a style block at the root of the document, rather than nest in beneath its parent selectors.
    * Have Sass output this rule set at the root of the document:
    ```
    .button {
      color: red;
      
      @at-root a#{&} {
        color: blue;
      }
    }
    ```
    * Our final CSS looks like this:
    ```
    .button {
      display: inline-block;
    }
    
    a.button {
      text-decoration: none;
    }
    ```
  
### Property Nesting

  ```
  .container {
    font: {
      family: 'Jump Start', sans-serif;
      size: 42px;
      weight: bold;
      style: normal;
    };
  }
  ```

  * The code will be compiled as:
  ```
  .container {
    $font: (
      'family': ('Jump Start, sans-serif),
      'size': 42px,
      'weight': bold,
      'style': normal,
    );
    
    font: {
      @each $property, $value in $font {
        #{$property}: $value;
      }
    };
  }
  ```
  
### Best Practices and Nesting Etiquette

  * Selector nesting:
    * Does not make it any faster to write code
    * Unlikely that your speed bottleneck is typing CSS selectors
    * If you have to use selector nesting, the reason should never be to avoid retyping selectors.
    * Makes code harder to read
    * Makes the codebase harder to search
    
##  The @extend Directive

  * the @extend directive is one way to handle inheritance in Sass.
  
### Building Clear Relationships

  ```
  .message, .info, .warning {
    background-color: gray;
    border: 1px solid black;
    margin: 1em;
  }
  
  .info {
    background-color: blue;
  }
  
  .warning {
    background-color: red;
  }
  ```
  
  * We can write the following Sass and output exactly the same CSS as before:
  ```
  .message {
    background-color: gray;
    border: 1px solid black;
    margin: 1em;
  }
  
  .info {
    @extend .message;
    background-color: blue;
  }
  
  .warning {
    @extend .message;
    background-color: red;
  }
  ```
  
### Extending Utilities

  ```
  //  Mixin Input
  
  @mixin clearfix {
    &::after {
      content: '';
      display: table;
      clear: both;
    }
  }
  
  .emory {
    @include clearfix;
  }
  
  .gracie {
    @include clearfix;
  }
  
  .miko {
    @include clearfix;
  }
  ```
  
  ```
  /*  Mixin Output  */
  
  .emory::after {
    content: '';
    display: table;
    clear: both;
  }
  
  .gracie::after {
    content: '';
    display: table;
    clear: both;
  }
  
  .miko::after {
    content: '';
    display: table;
    clear: both;
  }
  ```
  
  * Using @extend will create less output:
  ```
  //  Extends Input
  
  .clearfix:after {
    content: '';
    display: table;
    clear: both;
  }
  
  .emory {
    @extend .clearfix;
  }
  
  .gracie {
    @extend .clearfix;
  }
  
  .miko {
    @extend .clearfix;
  }
  ```
  
  ```
  /*  Extends Output  */
  
  .clearfix::after, .emory::after, .gracie::after, .miko::after {
    content: '';
    display: table;
    clear: both;
  }
  ```
  
### The Placeholder (Extend-only) Selector

  * A placeholder selector is a new selector type that only exists in Sass.
  * Placeholder selectors look like class or id selectors, but they start with % instead of . or #, and disappear completely in the output:
  ```
  //  Placeholder Input
  
  %clearfix::after {
    content: '';
    display: table;
    clear: both;
  }
  
  .emory {
    @extend .clearfix;
  }
  
  .gracie {
    @extend .clearfix;
  }
  
  .miko {
    @extend .clearfix;
  }
  ```
  
  ```
  /*  Placeholder Output  */
  
  .emory:: after, .gracie::after, .miko::after {
    content: '';
    display: table;
    clear: both;
  
  }
  ```
  * This is great for third-party libraries wanting to provide extendable classes without adding bloat to code. If a placeholder is not extended, that code block is never rendered.
  
### Advanced Extending

  * If you extend something that isn't there, Sass will throw an error:
  ```
  ".error-message" failed to @extend ".aliens".
  The selector ".aliens" was not found.
  Use "@extend .aliens !optional" if the extend should be able to fail.
  ```
  * Adding !optional to your @extend will silence that error, making your extension optional.  This is especially helpful when working with third-party libraries.  Here's an example:
  ```
  .error-message {
    @extend .aliens !optional;
  }
  ```
### Nesting Extends

  * The most notorious feature of @extends is when one nested selector extends another:
  ```
  .leonardo .cobb .dicaprio {
    background: blue;
  }
  
  .cillian .fischer .murphy {
    @extends .dicaprio
  }
  ```
  * If Sass compiled every possible meaning behind that extension - weaving together each possible iteration - the results would be exponentially long.  Sass is smarter than that, but still has to cover reasonable possibilities:
  ```
  .leonardo .cobb .dicaprio,
  .leonardo .cobb .cillian .fischer .murphy,
  .cillian .fishcer .leonardo .cobb .murphy {
    background: blue;
  }
  ```
  
### The Limits of Extending

  * Confusing Cascade:
    * @extend messes with the cascade, changing the specificity of styles in ways that are not obvious or easy to control.
    * To specificity isn't determined by the order in which you use extensions, but the order in which they're defined:
    ```
    .important {
      font-size: 4rem;
    }
    
    .message {
      font-size: 0.75rem;
    }
    ```
  
  * Collateral Damage
    * What happens if we want the .message class to look different in other contexts?
    * Many teams avoid this problem by only extending placeholder selectors and only defining placeholders in one location. 
    * That's a great rule of thumb, and helps to make extensions clear and controllable.
    
  * Hard-to-Read Output
    * When you see that long list of selectors in your browser inspector, it can be difficult to trace back to your original code - or hard to know your original intention.
    * Suffice it to say, you should look at the output CSS to make sure it means what you intended.
    
  * Media Query Madness
    * Various people have proposed using mixins that will wrap extends, so you caan choose between the two options on the fly:
    ```
    //  Define a Mixtend:
    @mixin clearfix($mixin: false) {
      @if $mixin {
        &::after {
          content: '';
          display: table;
          clear: both;
        }
      } @else {
        @extend %clearfix;
      }
    }
    
    %clearfix {
      @include clearfix(mixin);
    }
    
    //  Using a Mixtend:
    .container {
      @include clearfix;
    }
    
    @media (min-width: 48em) {
      .grid-row {
        @include clearfix(mixin);
      }
    }
    ```
    
    * Dependable Mixins
      * While the media query issue may get fixed down the road, the other issues are here to stay.
      * It's from basic problems with trying to represent inheritance in CSS. 
      * The current hold-up with @media is that every proposal fixing that issue would make the other issues worse.
      
##  Warnings and Errors

##  Architecture

##  The Sass Ecosystem
