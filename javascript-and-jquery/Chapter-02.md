# Basic JavaScript Instructions

##  Document Contents

[Statements](#statements)

[Comments](#comments)

[What is a variable?)(#what-is-a-variable)

[Variables: How to declare them](#variables:-how-to-declare-them)

[Variables: How to assign them a value](#variables:-how-to-assign-them-a-value)

[Data Types](#data-types)

[Rules for naming variables](#rules-for-naming-variables)

[Arrays](#arrays)

[Creating an array](#creating-an-array)

[Values in arrays](#values-in-arrays)

[Accessing & changing values in an array](#accessing-&-changing-values-in-an-array)

[Expressions](#expressions)

[Operators](#operators)

[Arithmetic operators](#arithmetic-operators)

[String operator](#string-operator)

##  Statements

  * A script is a series of instructions that a computer can follow one-by-one.  Each individual instruction or step is known as a statement.  Statements should end with a semicolon.
  * Javascript is Case sensitive
  * Statements are instructions and each one starts on a new line.
    * The semicolon also tells the JavaScript interpreter when a step is over, indicating that it should move to the next step
  * Statements can be organized into code blocks
    * Some statements are surrounded by curly braces; these are known as code blocks.  The closing curly brace is not followed by a semicolon.
    
##  Comments

  * You should write comments to explain what your code does.
  * They help make your code easier to read and understand.
  * Multi-line comments
    * To write a comment that stretches over more than one line, you use a multi-line comment, starting with the /* characters and ending with the */ characters. 
  * Single-line comments
    * In a single-line comment, anything that follows the two forward slash characters // on that line will not be processed by the JavaScript interpreter.
    
## What is a variable?

 * A script will have to temporarily store the bits of information it needs to do its job.  It can store this data in variables.
 * A variable is a good name for this concept because the data stored in a variable can change (or vary) each time a script runs
 * The result is said to be calculated or computed 
 
## Variables: How to declare them

 * Before you can use a variable, you need to announce that you want to use it.
 * `var quantity;`
 * var is an example of what programmers call a keyword.
 * In order to use the variable, you must give it a name. (This is sometimes called an identified.)
   * In this case, the variable is called quantity.  
 * In a variable name is more than one word, it is usually written in camelCase.
 
## Variables: How to assign them a value

 * Once you have created a variable, you can tell it what information you would like it to store for you.
 * `quantity = 3;`
 * Here we set a value for the variable called quantity.
 * The equals sign (=) is an assignment operator. It says that you are going to assign a value to the variable.  It is also used to update the value given to a variable.
 * Until you have assigned a value to a variable, programmers say the value is undefined.
 * Where a variable is declared can have an effect upon whether the rest of the script can use it.  Programmers call this the scope of a variable.
 
## Data Types

 * JavaScript distinguishes between numbers, strings, and true or false values known as Booleans.
 * Numeric Data Type
  * The numeric data type handles numbers
 * String Data Type
  * The strings data type consists of letters and other characters
 * Boolean Data Type
  * Boolean data types can have one of two values: true or false.
  
## Rules for naming variables

 * Here are six rules you must always follow when giving a variable a name:
  1. The name must begin with a letter, dollar sign ($), or an underscore (_).  It must not start with a number.
  2. The name can contain letters, numbers, dollar sign ($), or an underscore (_).  Note that you must not use a dash (-) or a period (.) in a variable name.
  3. You cannot use keywords or reserved words.
  4. All variables are case sensitive.
   * It is bad practice to create two variables that have the same name using different cases.
  5. Use a name that describes the kind of information that the variable stores.
  6. If your variable name is made up of more than one word, use a capital letter for the first letter of every word after the first word.
  
## Arrays

 * An array is a special typpe of variable.  It doesn't just store one value; it stores a list of values.
 * You should consider using an array whenever you are working with a list or a set of values that are related to each other.
 
## Creating an array

  ```
  var colors;
  colors = ['white','black','custom'];
  var el = document.getElementById('color');
  el.textContent = colors[0] // Color: white
  ```

## Values in arrays

 * Values in an array are accessed as if they are in a numbered list.  
 * Numbering items an array
  * Each item in an array is automatically given a number called an index.
   ```
   var colors;
   colors = ['white','black','custom'];
   ```
  * Index values start at 0, so the following table shows items from the array and their corresponding index values:
   ```
   Index Value
    0    'white'
    1    'black'
    2    'custom'
   ```
 * Accessing items in an array
  * To retrieve the third item on the list, the array name is specified along with the index number in square bbrackets.
   ```
   var itemThree;
   itemThree = colors[2];
   ```
 * Number of items in an array
  * Each array has a property called length, which holds the number of items in the array.
  * The name of the array is followed by a period symbol (or full stop) which is then followed by the length keyword.
   ```
   var numColors;
   numColors = colors.length;
   ```

## Accessing & changing values in an array

 ```
 // Create the array
 var colors = ['white','black','custom'];
 
 // Update the third item in the array
 colors[2] = 'beige';
 
 // Get the element with an id of colors
 var el = document.getElementById('colors');
 
 // Replace with third item from the array
 el.textContent = colors[2];  // Color: beige
 
 ```
 
## Expressions

 * An expression evaluates into a single value.  Broadly speaking there are two types of expressions.
  1. Expressions that just assign a vlue to a variable.
   Ex: `var color = 'beige'; // The value of color is now beige.`
  2. Expressions that use two or more values to return a single value.
   Ex: `var area = 3 * 2; // The value of area is now 6`
 
## Operators

 * Expressions rely on things called operators; they allow programmers to create a single value from one or more values.
  * Assignment operators (=)
  * Arithmetic operators (*,-,+,/)
  * String operators ('')
  * Comparison operators (>)
  * Logical operators (true, false)
  
## Arithmetic operators  

 * Addition (+)
 * Subtractiion (-)
 * Division (/)
 * Multiplication (*)
 * Increment (++)
 * Decrement (--)
 * Modulus (%)
 
 * Order of execution
  * Multiplication and division are performed before addition or subtraction.
  
## String operator

 * There is just one string operator: the + symbol.  It is used to join the strings on either side of it.
 * Programmers call the process of joining together two or more strings to create one new string concatenation.
 * Mixing numbers and strings together
  * Ex 1:
   ```
   var cost1 = '7';
   var cost2 = '9';
   var total = cost1 + cost2;

   You would end up with a string saying '79'.
   ```
  
  * Ex 2:
  ```
  var number = 12;
  var street = 'Ivy Road';
  var add = number + street;
  
  You would end up with a string saying '12Ivy Road'.
  ```
  
  * Ex 3:
  ```
  var score = 'seven';
  var score2 = 'nine';
  var total = score * score2;
  
  You would end up with the value NaN.
  ```
