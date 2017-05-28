# Part 1: You.write(code);

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

> **Key:** You can improve a system by adding new code.  You can also improve a system by removing code.

### So What?

> **Key:** Remove dead code wherever possible.  It gets in the way and slows you down.

### Waking the Dead

  * How can you find dead code?
    * The best approach is to pay attention whilst working in the codebase.  
    * Be responsible for your actions, and ensure that you always clean up after your work. 
    
### Surgical Extracting

> **Key:** It is safe to remove code that you might need in the future.  You can always get it back from version control.

> **Key:** Code cleanup should always be made in separate commits to functional changes

## The Ghost of a Codebase Past

> **Key:** Looking back at your older code will inform you about the improvement (or otherwise) in your coding skills.

###  Presentation

  * A style should be employed consistently in your codebase.
  
### The State of the Art

  * The introduction of a language-supported threading model renders third-party thread libraries (often implemented with rather questionable APIs) redundant.
  * The introduction of lambdas removes the need for a lot of verbose handwritten "trampoline" code. 
  * The range-based for helps remove a lot of syntactical trees so you can see the code-design wood.

### Idioms

  * Each language, with its unique set of language constructs and library facilities, has a particular "best practice" method of use.  
  * These are the idioms that experienced users adopt, the modes of use that have become honed and preferred over time.
  * As languages gain new features (e.g., lambdas) the kind of idiomatic code you'd write today may look very different from previous generations of the code.
  
### Design Decisions

  * You make a few mistakes, read some different code, work with talented coders, and pretty soon find you improved design skills.
  
### Bugs

  * Sometimes coming back with fresh eyes uncover obvious problems that you missed at the time.
  * After you've been bitten by certain kinds of bugs (often those that the common idioms steer you away from) you naturally begin to see potential bugs in old code
  
## Navigating a Route

### A Little Help from My Friends

> **Key:** Your best route into code is to be led by someone who already knows the terrain.  Don't be afraid to ask for help!

  * Look for online forums or mailing lists that contain helpful information and helpful people.  
  * There is often a healthy community that grows around popular open source projects
  
### Look for Clues

  * These are good indicators:
    * Ease of getting the source
    > **Key:**  Healthy projects require a single checkout to obtain the whole codebase, and the code can be placed in any directory on your build machine.  Do not rely on multiple checkout steps, or code in hardcoded locations.
    * Ease of building the code
      * If it's hard to build the code, it's often hard too work with it.
    > **Key:**  A healthy build runs in one step, with no manual intervention during the build process
    * Tests
    * File structure
    * Documentation
    * Static analysis
    * Requirements
    * Project dependencies
    * Code quality
    * Architecture
    > **Key:**  Often the real architecture of a system differs from the ideal design.  Always trust the code, not the documentation.
    
### Learn by Doing

> **Key:**  The best way to learn code is to modify it. Then learn from your mistakes.

### Low-Hanging Fruit

  * Start with a small, repeatable, low-risk fault report, rather than a meaty intermittent nightmare.
  
### Inspect the Code

  * Run the codebase through some code validators (like Lint, Fortify, Cppcheck, FxCop, ReSharper, or the like).
  * Look to see if compiler warnings have been disabled; re-enable them, and fix the messages.
  
### Study, Then Act

  * Study a small piece of code.  Critique it.  Determine if there are weak spots. Refactor it.
  
### Test First

  * Look at the tests. 
  * Work out how to add a new unit test, and how to add a new test file to the suite.  How do the tests get run?
  * A great trick is to try adding a single, one-line, failing test.  Does the suite immediately fail? This smoke test proves that the tests are not actively being ignored.
  
### Housekeeping

  * Tidy the source files: correct the directory hierarchy. Make it match the organisation in the IDE or projects files.
  
### Document What you Find

  * Does the code have any kind of top-level README documentation file explaining how to start working on it?
  * If not, create one and include the things that you have learned so far.
  * As you gain understanding of the system, maintain a layer diagram of the main sections of code.  Keep it up-to-date as you learn.
  
## Wallowing in Filth

### Smell the Signs

## Don't Ignore That Error!

## Expect the Unexpected

## Bug Hunting

## Testing Times

## Coping with Complexity

## A Tale of Two Systems
