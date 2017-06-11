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

### Warnings

  * It's possible to display messages or the value of any SassScript expression to the standard output stream through the @warn directive.
  * A warning has no impact on the compilation process; it does not prevent compiling to pursue or change it in any way.  Its only purpose is to display a message in the console.
  * There are a lot of reasons to use warnings in Sass, such as:
    * Informing the user of an assumption made about the code in order to avoid surprise and hard-to-track bugs.
    * Advising about a deprecated function or mixin as part of a library or framework
  * Sending a warning is dead simple to do: start with the @warn directive, then state whatever it is.
    * You don't have to use a string; you can warn with a number, a list, a map = whatever. Here, we print a string:
      ```
      @warn 'Uh-oh, something looks weird';
      ```
  * Using a regular CLI client, this warning will emit the following output:
    ```
    WARNING: Uh-oh, something looks weird.
             on line 1 of /Users/hgiraudel/jump-start-sass/warning.scss 
    ```
    
  * The Difference between @warn and @debug
    * There are two major differences between warning about a value and debugging a value.
    * The first one is that warnings can be turned off using the quiet option.
    * Degubs, on the other hand, will always be printed so that you remember to remove them when you're done using them.
    * The second difference is that warnings come with a stack trace - a report of the active stack frames at a certain point in time being during the execution of a program.
      * You know from where they're being emitted.
    * Debugs only print the value, along with the line they were called in, but they offer no extra information.
    * The @debug directive can really come in handy when you want to know what's inside a variable, for instance:
      ```
      @debug $base-font-size;
      ```
  
### Errors

  * The only difference between an error and a warning is that the error stops the compilation process.
  * You can throw an error using the @error directive.
  * Time to tke a look at a real practical example.  Let's start by writing a small function to help accessing deeply nested values in maps, map-deep-get(..):
    ```
    @function map-deep-get($map, $keys...) {
      @each $key in $keys {
        $map: map-get($map, $key);
        
        @if (type-of($map) == 'null') {
          @return $map;
        }
      }
      @return $map; 
    }
    ```
  * Let's enhance it with custom errors. But first, consider the following map and map-deep-get(..) call:
    ```
    $map: (
      'foo': (
        'bar': (
          'baz':42
        )
      )
    );
    
    $value: map-deep-get($map, 'foo', 'bar', 'baz', 'qux');
    ```
  * If we try to execute this code, it will yield:
    ```
    Error: 42 is not a map for 'map-get'
          on line 1 of /Users/hgiraudel/jump-start-sass/error.scss
    ```
  * We can perform a second check to ensure that the map is actually a map, or we throw a meaningful error:
    ```
    @function map-deep-get($map, $keys...) {
      @each $key in $keys {
        $map: map-get($map, $key);
        
        //  If '$map' does not contain the next key, return 'null'
        @if type-of($map) == 'null' {
          @return $map;
        }
      
        //  If '$map' is not a map, throw an error
        @if type-of($map) != 'map' {
          @error 'key '#{$key}' is not associated with a map but a =>#{type-of($map)} ('#{$map}').';
        }
      }
      @return $map;
    }
    ```
  * If we run our previous snippet again, here's the output:
    ```
    Error: key 'baz' is not associated with a map but a number ('42').
            on line 1 of /Users/hgiraudel/jump-start-sass/error.scss
    ```
    
##  Architecture

### Multiple files and Folders

 * Breaking your code into multiple files is one key advantage to using a preprocessor, and forms the basis of any architecture.
 
 * CSS Imports
  * The CSS @import directive allows you to reference one CSS file from another.  Importing is handled by the browser and requires additional HTTP requests - since the importing file has to be parsed before the @import directive is discovered.
  * If you have a chain of files importing each other, those imports will happen in sequence, blocking the document from rendering until all the CSS has loaded.
  * There are various cases in which Sass will fall back to the vanilla CSS output, such as when:
    * An imported filed has a .css extension 
    * A filename begins with http:// or https://
    * The filename is a url(..) function
    * @import has any media queries
  * The following will compile to standard CSS imports, even in Sass:
    ```
    @import 'relative/styles.css';
    @import 'http://absolute.com/styles.css';
    @import url('landscape.css') screen and (orientation: landscape);
    ```
  * Sass Imports and Partials
    * Look similar to CSS imports, but the imported files are compiled into one single output file, as though their contents were copied and pasted into place before compilation.  This type of Sass import will only work on files with .sass or .scss extensions, but you can leave the extension off when importing (as long as there are no similarly named files).
    * It's also possible to import multiple files in one command, or import files into a nested context:
      ```
      //  Import an explicit file relative to the current directory
      @import 'path/to/explicit.scss';
      
      //  Import a file with either the .sass or .scss extension
      @import 'implicit';
      
      //  Import multiple files...
      @import 'path/to/emory.scss',
              'miko',
              'path/to/gracie';
              
      //  Import a file into a nested context...
      //  (imagine the file copied and pasted into this context)
      .latte {
        @import 'espresso';
      }
      ```
    * The most common use of Sass importing is for partial files - Sass files that are not compiled on their own but are for importing into other files.
    * If you want a Sass file to remain uncompiled until it's imported, add an underscore (_) to the start of the filename.
    * Sass files that start with _ won't compile on their own, but can be imported into other files.
    * When importing partials, Sass allows you to leave the _off, which is similar to leaving off an extension.
    * For example:
      ```
      //  _authors.scss
      .miriam {
        background: blue;
      }
      
      //  jumpstartsass.scss
      @import 'authors';  //  Shorthand for importing '_authors.scss'
      
      //  jumpstartsass.css (compiled CSS)
      .miriam {
        background: blue;
      }
      ```
      * Running Sass in this directory (sass --update .) compiles jumpstartsass.scss to jumpstartsass.css; however, it won't create an _authors.css file, since it has a leading underscore.
    * All Sass imports are handled at compile time and never interrupt the browser, it's perfectly safe (and recommended) to use as many partials as necessary, compiling them into a single stylesheet for production.
    * A common Sass directory for a project might look like this:
      ```
      sass/config/_colors.scss
                /_webfonts.scss
                
      sass/layout/_navigation.scss
                 /_banner.scss
                 
      sass/modules/_calendar.scss
                /_contact.scss
                
      sass/patterns/_buttons.scss
                /_dropdown.scss
        
      sass/main.scss        
      ```
    * After organizing all your partials, they can be imported into the single primary main.scss file for compilation:
      ```
      //  Primary Sass File: main.scss
      @import 'config/colors';
      @import 'config/webfonts';
      
      @import 'patterns/buttons';
      @import 'patterns/dropdown';
      
      @import 'layout/navigation';
      @import 'layout/banner';
      
      @import 'modules/calendar';
      @import 'modules/contact';
      ```
    
### Components and Organization

  * Most CSS and Sass organization systems are based on some concept of user interface "components" or discrete pieces that can be put together to form a complete project.
  * Here are some guidelines for thinking about architecture:
    1.  Break your code into the smallest logical components partials
    2.  Organize your partials into grouped folders based on specificity
    3.  Import those partials into one master file in order of specificity
  
  * Object-oriented CSS (OOCSS)
    * OOCSS is one of the original front-end architectures, and the initial inspiration for adding the @extend directive to Sass.
    * It places a strong emphasis on finding the right granularity for CSS objects.
    * Media object - a fixed size media element (such as an image or video) alongside fluid content such as text.
    * OOCSS is a powerful tool for simplifying CSS and perfecting the performance of large-scale applications. 
      * But taken to extremes, the OOCSS approach can leave you with a mess of single-purpose utility classes (such as .padding-left-10px) that couple your HTML and CSS too tightly, and eliminate any maintainability you might get from more semantic code.
    * The two main principles of OOCSS are worth keeping in mind while you work out your own architecture:
      * Separate structure and skin
        * By having multiple design skins (colors, backgrounds, borders, etc.) that you can mix and match with structural objects, it's possible to achieve more visual variety with less code.
        * This also means decoupling styles from the base semantics of HTML tags. By styling classes (.primary-header) instead of tags (h1), you have more flexibility to keep HTML meaningful, while applying consistent styles wherever they're appropriate. 
      * Separate container and content
        * OOCSS objects should not be dependent on their location or context, but be reusuable and able to file whatever container they are given.
        * This ensures that an object will look the same in any context, without developers having to guess what a given element or class will do in different situations.
        
  * Atomic Design
    * driven by questions of granularity.
    * An atom project is broke down into five stages: atoms, molecules, organisms, templates, and pages.
    * The idea is to style the stages in order, sstarting granular and working outwords, with each stage building on the one before.
    * Atoms can be abstract information such as color palettes, fonts, and typographic scales; they can also be default styles for tags such as form labels, buttons, and paragraphs.
    * Atoms can be put together to form molecules. Combine an image with a paragraph and button (all atoms), and you have a simple product-listing molecule.
    * Molecules are small components that do one task well. Group a number of these molecules together, and you have an organism.
    * Organisms are larger grouped components that form a section of the interface.
    * Templates combine the smaller molecules and organisms into actual layout structures.
    * Each specific instance of a template is called a page.
    * A standard Atomic Design directory will be organized into these five stage-based folders:
      ```
      sass/atoms/_colors.scss
      sass/atoms/_buttons.scss
      
      sass/molecules/_navigation.scss
      sass/molecules/_search.scss
      
      sass/organisms/_banner.scss
      sass/organisms/_gallery.scss
      
      sass/templates/_list.scss
      sass/templates/_detail.scss
      
      sass/pages/_home.scss
      sass/pages/_archive.scss
      
      sass/main.scss
      ```
      
  * Block, Element, Modifier (BEM)
    * The BEM CSS architecture is built around the three ideas in its title.
      * Blocks are components of any size, and can be nested inside each other.
        * The header block might contain a logo block, a navigation block, and a search block.
        * Blocks are reusuable, independent, and mobile - so they can be put anywhere on the page, the repeated as often as necessary.
      * Elements are the constituent parts that belong to a specific block.
        * A menu block might be made up of four tab elements.
      * Modifiers are flags on blocks or elements that change their appearance, behavior, or state.
    * There are variations on the exact syntax, but the formal documentation allow hyphens (-) within a block, element, or modifier namee; double underscore (__) between block and element names; and single underscore (_) before a boolean (true/false) modifier, or between a key-value modifier name and its given value.
    * Here's an example straight from the BEM documentation that defines a form block with a _login boolean modifer, a _theme_forest key-value modifer, and two elements:
      ```
      <form class="form form_login form_theme_forest">
        <input class="form_input">
        <input class="form_submit form_submit_disabled">
      </form>
      ```
    * A related Sass partial would look like this:
      ```
      .form {}
      .form_theme_forest {}
      .form_login {}
      .form_input {}
      .form_submit {}
      .form_submit_disabled {}
      ```
    * Elements and modifiers have their own subdirectories using the same underscore-driven naming conventions:
      ```
      blocks/input/_type/input_type_search.css
      
      blocks/input/__box/input__box.css
      
      blocks/input/input.css
      
      blocks/input/input.js
      
      blocks/button/button.css
      
      blocks/button/button.js
      
      blocks/button/button.png
      ```
    
  * Scalable and Modular Architecture for CSS (SMACSS)
    * This architecture uses five categories for organizing for CSS.
    * The five categories here are base, layout, module, state, and theme.
      * Base rules define the default style of elements.
      * Layout styles are used to break the document into sections that can contain modules, the individual components of a design.
      * State rules define different JavaScript-dependent states for a module or layout.
      * Most sites have no need for themes, but they can be used to describe multiple style options for the same modules.
    * SMACSS pays special attention to what Snook calls the depth of applicabiliy.
    * The Sass "inception rule" states that you should never nest selectors more than three layers deep.
    * By shortening the selector, we've lowered the specificity, but we still have a large depth of applicability.  The problem with so much depth is that it makes our CSS more dependent on a particular HTML structure.
    
  * Hugo's 7-1    
    * A variation of SMACSS for organizing Sass partials.
    * It uses seven folders of partials and one master file to pull them all together
    * The base/ folder contains broad standards across a site - such as a reset, default styles for common HTML tags, common animations, and basic typography.
    * The layout folder includes everything one might need for laying out the structure of a site.
    * The components folder is organized into partials by component; the pages folder contains any page-specific styles; and a themes folder holds any theme-related styles (if your project has multiple themes).
    * 7-1 also includes an abstracts folder for Sass tools and helpers, which is organized into partials for global variables, functions, mixins, and placeholders. Nothing in this folder should output any CSS if compiled on its own.
    * There is a vendors folder for third-party libraries, frameworks, and toolkits such as Normalize, Bootstrap, jQueryUI, FancyButttonsOMG, and so on.
    * Put it all together, and you have a Sass directory similar to this:
      ```
      sass/base/_reset.scss
      
      sass/base/_typography.scss
      
      sass/components/_buttons.scss
      
      sass/components/_carousel.scss
      
      sass/components/_cover.scss
      
      sass/components/_dropdown.scss
      
      sass/layout/_navigation.scss
      
      sass/layout/_grid.scss
      
      sass/layout/_header.scss
      
      sass/layout/_footer.scss
      
      sass/pages/_home.scss
      
      sass/pages/_contact.scss
      
      sass/themes/_theme.scss
      
      sass/themes/_admin.scss
      
      sass/utils/_variables.scss
      
      sass/utils/_functions.scss
      
      sass/utils/_mixins.scss
      
      sass/utils/_helpers.scss
      
      sass/vendors/_bootstrap.scss
      
      sass/vendors/_jquery-ui.scss
      
      sass/main.scss
      
      ```
      
  * Inverted Triangle CSS (ITCSS)
    * ITCSS organizes all your Sass and CSS based on three metrics: reach, specificity, and explicitness - visualized as an inverted triangle.
    * Code should be organized from least to most explicit, starting with general catchall rules and moving up to more explicit styles.
    * Code is organized from broadest to narrowest reach - so that styles affecting more HTML come early in the code, and styles with a more localized application come later.
    * Code is organized from lowest to highest specificity, so that later code can always override earlier code.
    * The triangle is broke down into seven layers. Each layer is more specific, explicit, and narrow-reaching than the layer before it:
      * Settings contains global Sass configuration that can be accessed anywhere in the project, such as font sizes, colors, and other project configuration.
      * Tools are global functions and mixins that are helpful across the project and not specific to one component.
      * Generic is the first layer with CSS output of its own, which includes browser resets or normalization, global box-sizing, and any other broad-scoped rules.
      * The elements layer provides default styles for bare HTML elements such as links and paragraphs.
        * It provides a more opinionated style.
      * ITCSS objects are similar to OOCSS objects, and are defined in class-based selectors.  They define reusuable patterns that have a consistent structure no matter what content or cosmetic style is applied.
      * Components are recognizable pieces of an interface.
        * After the initial setup, this is where the majority of a project's feature-building work takes place. 
      * Finally, trump styles can be used to override any other layer.  Trumps should be used sparingly, and have as narrow a scopr as possible.
    * The results could look like this:
      ```
      @import "settings/global";
      @import "settings/colors";
      
      @import "tools/functions";
      @import "tools/mixins";
      
      @import "generic/box-sizing";
      @import "generic/normalize";
      
      @import "elements/headings";
      @import "elements/links";
      
      @import "objects/wrappers";
      @import "objects/grid";
      
      @import "components/site-nav";
      @import "components/buttons";
      @import "components/carousel";
      
      @import "trumps/clearfix";
      @import "trumps/utilities";
      @import "trumps/ie8";
      ```
      
### Modular Imports in Sass 4

  * Modular imports - the major new feature that is driving plans for Sass 4.
  * Where Sass imports currently work as though the entire imported document has been cut and pasted into place, modular imports provide a lot more control for the developer.
  * It will probably look a little like this:
    ```
    @use 'path/to/sitepoint/author' as 'miriam';
    
    .sitepoint {
      @include miriam.write('Jump Start Sass');
      -webkit-paycheck: miriam.money('millions');
    }
    ```
    
  * Locality
    * It's impossible to tell by looking at a single Sass file what already exists in that global space.
    * Sass will default to using the filename as a prefix if none is provided, and also allow you to remove the prefix when you need to.
    * In addition to using a file with or without a given prefix, it might be possible to use an entire file as a mixin, so you can apply the code of that file anywhere you want - even in a nested context.
    
  * Encapsulation
    * With encapsulation, you'll have control over which mixins, functions, variables, and (possibly) placeholders should be made public.  Adding - or _ to the start of a name will define it as private.
    * There is also talk of a @forward directive that would allow authors to pass the API from one module along as part of another.
    
##  The Sass Ecosystem

### Open-source Sass

  * There are the big front-end frameworks that provide all the common front-end patterns aa site might need.  The largest frameworks such as Bootstrap and Foundation take this to an extreme, providing Ikea-style website kits just waiting to be assembled.
  * The Sass frameworks provide all the Sass utilities and toolkits that you might need along the way: helpers for layout, accessibility, typography, and so on.
  * There are also design component libraries that focus on providing specific styles, such as glossy buttons or nice typography.
  * There are the abstract toolkit utilities that act more like a hammer: they're good at hitting things, but they don't care what's hit, or why.

### Frameworks

  * Compass was the first big Sass framework.  It was primarily intended as a Sass package manager, but also included a library of common utilities for other Sass toolkits (Compass plugins) to reference.
  * Compass has reached the end of its life and is no longer being actively maintained, but ThoughtBot's Bourbon provides aa similar set of features.  Both are Ruby gems:
    ```
    gem install bourbon
    gem install compass
    ```
  * And Bourbon is now also available as a Node package:
    ```
    npm install bourbon
    ```
  * Both have been built around the official CSS3 syntax, so their APIs are often (but not always) identical.  

### Grids

  * Susy was the first grid system for Sass
  * The quickest entry point for Susy is the span(..) mixin.
  * The mixin provides float-based output, but the functions can be used anywhere to create any style of grid you can image; for example:
    ```
    //  Susy configuration:
    $susy: (
      columns: 12,  //  the number of columns in a grid
      gutters: 1/4, //  the size of a gutter relative to a column
    );
    
    //  Span mixin:
    article {
      include span(8 of 12);
    }
    
    //  Susy functions:
    aside {
      flex: 1 1 span(4 of 12);
      margin-left: gutter();
    }
    ```
    
    ```
    /*  Compiled CSS  */
    article {
      width: 66.10169%;
      float: left;
      margin-right: 1.69492%;
    }
    
    aside {
      flex: 1 1 32.20339%;
      margin-left: 1.69492%;
    }
    ```

  * 
  
### Media Queries

### Toolkits

### Beautiful Code

### Package Managers
