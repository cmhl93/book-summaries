# Part1: You.write(code);

## Document contents
[Keeping Up Appearance](#keeping-up-appearance)

[Write Less Code!](#write-less-code)

[Improve Code by Removing It](#improve-code-by-removing-it)

[The Ghost of a Codebase Past](#the-ghost-of-a-codebase-past)

[Navigating a Route](#navigating-a-route)

[Wallowing in Filth](#wallowing-in-filth)

[Don't Ignore That Error!](#dont-ignore-that-error)

[Expect the Unexpected](#expect-the-unexpected)
  
[Bug Hunting](#bug-hunting)

[Testing Times](#testing-times)

[Coping with Complexity](#coping-with-complexity)

[A Tale of Two Systems](#a-tale-of-two-systems)

## Keeping Up Appearance

> **Key:** Adopt a healthy attitude to your code presentation

### Presentation is powerful

> **Key:** Good code presentation reveals your code's intent. It is not an artistic endeavour

> **Key:** We need good presentation to avoid making code errors. Not so we can create pretty ASCII art.

### It's about Communication
  * We write code for two audiences:
    * For the compiler
    * Other programmers
  * Write maintainable comments --> no banners
  
### Layout
  * Indentation
  * Use of whitespace around operators
  * Capitalisation
  * Brace placement
  * Tabs vs. space indentation
  
### Structure Well
  * Public information comes before private information
  * Creation of an object comes before use of an object
  * Write shorter code blocks
  * Don't write one function with 5 "paragraphs".
    * Consider splitting this up into five functions, each with a well-chosen name
    
### Consistency
  * Adopt a coding standard or style guide
    * Ensure that the entire team's IDE and source code editors are configured the same way.

### Names
  * We name many things: variables, functions and methods, types, namespaces and packages
  * A good name is descriptive, correct, and idiomatic

### Avoid Redundancy
  * Consider:
      ```
      class WidgetList{
        public int numberOfWidgets(){...}
      };
      ```
  
  * The numbersOfWidgets method name is unnecessarily long, repeating the word Widget.
    * It can simply be called size()
    
### Be Clear
  * Favour clarity over brevity
  * Names don't need to be short to save you key presses
  
### Be Idiomatic
  * Employ the capitalisation conventions most often used in your language
  
### Be Accurate
  * Ensure that your names are accurate
  
### Make yourself presentable
> **Key:** Never alter presentation and behaviour at the same time.  Make them separate separate version-controlled changes

## Write Less Code!

> **Key:** Less code can mean more software

### Why Should We Care?
  * More code means, more maintenance
  * More code to understand
  * More work required to make modifications
  * More bugs
  
### Flappy Logic
  * The unnecessary use of conditional statements and tautological logic constructs
  
  * Ex 1:
  
    ```
    if(expression)
      return true;
    else
      return false;
    ```
   
    Simplified as:
    ```
      return expression
    ```
    
  * Ex 2:
  
    ```
    if(something == true){
      //...
    }
    ``` 
    
    Simplified as:
    ```
      if(something)
    ```
    
  * Ex 3:
   
    ```
     bool should_we_pick_bananas() {
      if(gorilla_is_hungry()) {
        if(bananas_are_ripe()) {
          return true;
        }else {
          return false;
        }
      }else {
        return false;
      }
    }
    ```
    
    
    Simplified as:
    ```
      return gorilla_is_hungry() && bananas_are_ripe();
    ```  
    
> **Key:** Express code clearly and succintly.  Avoid unnecessarily long-winded statements

### Duplication
  * Do not copy code sections.  Factor them into a common function.  Use parameters to express any differences
  * DRY principle: Don't Repeat Yourself!  
  * Multiple loops can usually be reduced to single loop
  
> **Key:** If you spot duplication, remove it.

### Dead Code
  * Dead code is code that is never run, that can never be reached
  * Other manifestations of dead code include:
      * Functions that are never called
      * Variables that are written but are never read
      * Parameters passed to an internal method that are never used
      * Enums, structs, classes, or interfaces that are never used
    
### Comments
  * Good code does not need reams of comments to prop it up, or to explain how it works
  
> **Key:** Make sure that every comment adds value to the code.  The code itself says what and how. 
A comment should explain why-but only if it's not already clear.

> **Key:** Do not remove code by commenting it out.  It confuses the reader and gets in the way

### Verbosity
  * A lot of code is needlessly chatty
  * Move variable declarations and definitions together, to reduce the effort required to understand the code,
  and reduce potential errors from uninitialised variables
  
### Bad Design
  * Bad design may introduce many unnecessary communication paths between components.
  * Your design should consider whether off-the-shelf libraries already exist that solve your programming problems.
  
### So What Do We Do?
> **Key:** Every day, leave your code a little better than it was. Remove redundancy and duplication as you find it.

## Improve Code by Removing It

## The Ghost of a Codebase PAst

## Navigating a Route

## Wallowing in Filth

## Don't Ignore That Error!

## Expect the Unexpected

## Bug Hunting

## Testing Times

## Coping with Complexity

## A Tale of Two Systems
