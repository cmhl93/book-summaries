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

> **Key:**  Be prepared to encounter bad code. Fill your toolbox with sharp tools to deal with it.

### Wading into the Cesspit

> **Key:**  Silence the feeling of revulsion when you encounter "bad" code. Instead, look for ways to practically improve it.

### The Survey Says..

  * Consider employing software archaeology in your survey: mine your revision control system logs for hints about the quality.

### Working in the Sandpit

> **Key:**  Pick your battles. Consider carefully whether you should invest time and effort in "tidying up" bad code. It may be pragmatic to leave it alone right now.

### Cleaning Up Messes

> **Key:**  Follow the Boy Scout Rule. Whenever you touch some code leave it better than you found it.

### Making Adjustments

> **Key:**  Make code changes slowly, and carefully. Make one change at a time.

  * There are many practical ways to follow this advice. Specifically:
    * Do not change code layout whilst adjusting functionality.
    * Do everything you can to ensure that your :tidying" preverses existing behaviour.
    * Adjust the APIs that wrap the code without directly modifying the internal logic.
    
### Bad Code? Bad Programmers?

> **Key:**  There is no need to apportion blame for "bad" code.

## Don't Ignore That Error!

> **Key:**  Do not ignore possible errors in your code. Don't put off handling errors until "later" (you won't get around to it).

### The Mechanism

  * We report errors in our code in a number of ways, including:
    * Return codes
    * Side effects
    * Exceptions
    > **Key:**  Use exceptions well, with discipline. Understand your language's idioms and requirements for effective exception use.
    
### The Madness

  * Not handling errors leads to:
    * Brittle code
      * This type of code is full of hard-to-find crashes
    * Insecure code
      * Crackers often exploit poor error handling to break into software systems
    * Bad structure
      * If there are errors from your code that are tedious to deal with continually, you probably have a bad interface. 
      * Express it better, so the errors are not so onerous.

## Expect the Unexpected

### Errors

  * Ensure that your error handling is idiomatic, and uses the appropriate language mechanisms.
  
### Threading

  * Make sure you understand basic concurrency principles, and how to decouple threads so they cannot interact in dangerous ways.
  * Understand mechanisms to reliably and quickly pass messages between thread contexts without introducing race conditions or blocking the threads unnecessarily.

### Shutdown

  * don't enqueue threaded callbacks that target objects already discarded by other threads.
  
### The Moral of the Story

> **Key:**  Consider all the potential code paths as you write your code. Do not plan to handle "unusual" cases later: you'll forget and your code will be buggy.

## Bug Hunting

### An Ounce of Prevention

> **Key:**  Avoid injecting bugs into your code by employing sound engineering practices. Don't expect quickly hacked-out code to be of high quality.

### Bug Hunting

  * Two factors usually determine how hard a bug is to fix:
    * How repoducible it is
    * The time between the cause of the bug entering the code, the "software fault" itself - the bad line of code, or faulty integration assumption - and you actually noticing.
  * The first, and most important thing, is to methodically investigate and characterise the bug.  Give yourself the best raw material to work with:
    * Reduce it to the simplest set of reproduction steps possible.
    * Ensure that you are focusing on a single problem
    * Determine how repeatable the problem is.
    
### Lay Traps

  * Find places in the code path between these two points, and set traps to catch the fault.
  * Add assertions or tests to verify the system invariants - the facts that must hold for the state to be correct.
  * Add diagnostic printouts to see the state of the code so you can work out what's going on.
  > **Key:**  Assertions and logging (even the humble printf) are potent debugging tools. Use them often
  
### Learn to Binary Chop

  * This is a very powerful approach - allowing you to get to a solution in order O(log n) time, rather than O(n).
  > **Key:**  Binary chop problem spaces to get results faster.
  * Employ this technique with trap laying.
  
### Employ Software Archaeology

  * Software archaeology describes the art of mining through the historical records in your version control system.
  * Determine a point in the near past of the codebase when this bug didn't exist.
  * Once you find the breaking code change, the cause of the fault is usually obvious, and the fix is self-evident.
  
### Test, Test, Test

> **Key:**  Untested code is a breeding ground for bugs. Tests are your bleach.

### Invest in Sharp Tools

> **Key:**  Learn how to use your debugger well. Then use it at the right times.

### Remove Code to Exclude it from Cause Analysis

  * Disable other threads that shouldn't be involved. 
  * Remove subsections of code that do not look like they're related.
  
### Cleanliness Prevents Infection

> **Key:**  Fix bugs as soon as you can. Don't let them pile up until you're suck in a code cesspit.

### Oblique Strategies

  * Take a break
  * Explain it to someone else
  
### Don't Rush Away

  * Once you find and fix a bug, don't rush mindlessly on.  

### Non-Reproducible Bugs

  * How do we go about finding, and fixing, these fiends?
    * Keep records of the factors that contribute to the fault.
    * As you get more information, start to draw conclusions.
    * Consider adding more logging and assertions in beta or releaase builds to help gather information from the field.
    * If it's a really pressing problem, set up a test farm to run long-running soak tests.
  * There are a few things that are known to contribute to such unreliable bugs. 
  * You may find they provide hints for where to start investigating:
    * Threaded code
    * Network interaction
    * The variable speed of storage
    * Memory corruption
    * Global variables/singletons
  
## Testing Times

### Why Test?

  * Problems are found
  
### Shortening the Feedback Loop

  * Good testing strategies shorten the feedback loop, so we can work most effectively:
    * We know that our code works when it's used in the field and returns accurate results to users.
    * To ensure correctness before we ship, the QA team tests candidate releases
    * We want to check that our new subsystems work before integrating them into the project.
    * The subsystems are comprised of smaller units: classes and functions.
  * The shorter the feedback loop, the faster we can iterate over design changes, and the more confident we can feel about our code.
  
> **Key:**  To improve our software development we need rapid feedback, to learn of problems as soon as they appear. Good testing strategies provide short feedback loops.

### Code That Tests Code

  * Work smarter, not harder
    * Your IDE can highlight syntax errors as you type.
  * Computers can run tests rapidly and repeatedly, reducing the feedback loop.
  
### Who Writes the Tests?

  * Unit-test engineer - specializes in verifying the code of an upstream programmers.
  
> **Key:**  We need tests at all levels of the software stack and development process. However, programmers particularly requires tests at the smallest scope possible, to reduce the feedback loop and help develop high-quality software as quickly and easily as possible.

### Types of Tests

  * Unit tests
    * Unit tests specifically exercise the smallest "units" of functionality in isolation, to ensure that they each function correctly.
  * Integration tests
    * These tests inspect how individual units integrate into larger cohesive sets of co-operating functionality.
  * System tests
    * Otherwise known as end-to-end tests, these can be seen as a specification of the required functionality of the entire system.
    
### When to Write Tests

  * The term TDD (test-driven development) is conflated with test-first development
  * The test-first cycle is:
    1.  Determine the next piece of functionality you need.
    1.  Only then implement that functionality, in the simplest way possible.
    1.  This is the important part that's often overlooked: now tidy up the code. Refactor unpleasant commonality. Restructure the SUT to have a better internal structure.
    1.  Go back to step 1 and repeat until you have written passing test cases for all of the required functionality.
  * This is a great example of a short, feedback loop. 
    * It is often referred to as the red-green-refactor cycle in honour of unit-test tools that show failing tests as a red progress bar, and passing tests as a green bar.
    
> **Key:**  Write tests as you write the code under test. Do not postpone test writing, or your tests will not be as effective.

### When to Run Tests

> **Key:**  Encourage tests to be run early and often. Bake them into your build process

> **Key:**  Good development tests do not replace thorough QA testing

### What to Test

### Good Tests

> **Key:**  Bad tests can be a liability. They can impede effective development

### What does a Test Look Like?

####  Test Names

### The Structure of Tests

####  Maintain the Tests

> **Key:**  Maintain your test suite, and listen to it when it talks to you.

####  Picking a Test Framework

### No Code Is an Island

> **Key:**  Global variables and singleton objects are anathema to reliable testing. You can't easily test a unit with hidden dependencies.

> **Key:**  Factoring your code to make it "testable" leads to better code design.

## Coping with Complexity

## A Tale of Two Systems
