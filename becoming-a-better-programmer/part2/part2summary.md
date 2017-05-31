# Part 2: Practice Makes Perfect

## Document Contents
[Software Development Is](#software-development-is)

[Playing by the Rules](#playing-by-the-rules)

[Keep It Simple](#keep-it-simple)

[Use Your Brain](#use-your-brain)

[Nothing Is Set in Stone](#nothing-is-set-in-stone)

[A Case for Code Reuse](#a-case-for-code-reuse)

[Effective Version Control](#effective-version-control)

[Getting One Past the Goalpost](#getting-one-past-the-goalpost)

[The Curious Case of the Frozen Code](#the-curious-case-of-the-frozen-code)

[Please Release Me](#please-release-me)

## Software Development Is

### Software Development is...an Art

> **Key:**  A programmer needs good taste and a sense of aesthetics to write exceptional code.

  * There are many parts of the software development process akin to the creation of a work of art.  The process is:
    * Creative
      * It requires imagination
    * Aesthetic
      * Good code is hallmarked by elegance, beauty, and balance
    * Mechanical
      * As any artist, we work in our particular medium with our particular tools, processes, and techniques
    * Team-based
      * Many forms of art are not single-person endeavours.
      
### Software Development is...a Science

  * It is:
    * Rigourous
    * Systematic
    * Insightful
      * Software development requires intellectual effort and astute analytical powers.
      > **Key:**  Good software development is not cowboy coding, throwing down the first code you can think of.  it is a deliberate, considered, accurate endeavour.

### Software Development is...a sport

  * Software development involves:
    * Teamwork
    * Discipline
    * Rules
    
### Software Development is...Child's Play

  * Consider how this applies to our software development:
    * Learning
    > **Key:**  Good programmers work with humility.  they admit that they don't know it all
    * Simplicity
    * Having fun
    
### Software Development is...a Chore

  * This requires us to:
    * Clean up
    * Work in the background
    * Maintenance
    
## Playing by the Rules

### We Need More Rules!

> **Key:**  Programming teams have a set of rules.  These rules define what we do and how we do it.  But they also describe a coding culture.

### Set the rules

> **Key:**  Don't rely on vague unwritten team "rules." Make the implicit rules explicit, and take control of your coding culture.

## Keep It Simple

> **Key:**  Simple code takes effort to design.  it is not the same thing as overly simplistic code.

### Simple Designs

####  Simple to Use

  * It has a low cognitive overhead
  
####  Prevents Misuse

> **Key:**  Simple designs aim to prevent misuse.  They may involve extra internal complexity in order to present a simpler API.

####  Size matters

> **Key:**  Simple designs are as small as possible. And no smaller.

####  Shorter Code Paths

  * They also avoid unnecessary inheritance, polymorphism, or dynamic binding.

####  Stability

  * Simple interfaces tend to be stable, and don't change much.

### Simple Lines of Code

> **Key:**  Consistency leads to clarity.

### Keeping it simple, not stupid

> **Key:** Apply bugfixes to the root cause, no where symptoms manifest. Sticking plaster symptom-fixes do not lead to simple code.

### Assumptions can reduce simplicity

> **Key:**  Avoid implicit assumptions in your code.

### Avoid premature optimisation

  * The act of code optimisation is generally that of taking a straightforward, readable, algorithmic implementation and butchering it: pulling the algorithm out of shape so that it executes faster on a given machine under particular conditions. 
    * This inevitably alters the shape to be less clear and, therefore, less simple.
  * Write clear code first.  Make it complex only when needed.
  
### Sufficiently Simple

> **Key:**  Only write as much code as is needed.  Anything extra is complexity that will become a burden.

### A Simple Conclusion

  * Our preference for high cohesion and low coupling speaks to simplicity in design.
  
## Use Your Brain

### Don't be stupid

> **Key:**  Stop and think.  Don't write stupid code.

> **Key:**  Admit to your mistakes and bad coding decisions. Learn from them.

### Avoid Mindlessness

> **Key:**  Pay attention. Don't write code without care.

### You are allowed to think!

> **Key:**  Have the courage to use your brain.  Feel empowered to critique code and make decisions about how to improve it.

## Nothing Is Set in Stone

> **Key:**  Do not embalm your code.  If you have "unchangeable" code in your product, then your product will rot.

> **Key:**  You are the master of your software; it's under your control. Do not let the code, or the processes around it, dictate how the code grows.

### Fearless Change

  * How do we reconcile courageous modification with fear or error?
    * Learn how to make good changes
    * Learn what makes software easy to change, and strive to craft software with these attributes.
    * Make daily improvements to your code that make it more malleable.
    * Embrace healthy attitudes that lead to flourishing code.
    
> **Key:**  To modify code you need courage and skill. Not recklessness.

### Change Your Attitude

> **Key:**  "Good Code" is not somebody else's problem. It is your responsibility. You have the power to make a change and to bring about an improvement.

  * Here are important attitudes, both for the team and for the individual, that contribute to healthy code growth:
    * Fixing wrong, dangerous, bad, duplicated, or distateful code is not a distraction, a sidetrack, or a waste of precious time.
    * Refactoring is encouraged.
    * No one "owns" any area of the code.
    * It is not a crime to make a mistake or to write the wrong code.
    * No one's opinion should be considered more important than anyone else's.
    * Good programmers expect change, because that is what software development is all about.
    * We lean on the safety net of accountability.
    
### Make the Change

####  Design for Change

> **Key:**  Often it is best to make a series of frequent, small, verifiable adjustments, rather than one large sweeping code change.

####  Tools for Change

> **Key:** Automated tests are an invaluable safety harness that build confidence in your changes.

####  Pick your battles

  * There is a certain amount of technical debt that we live with until we get a chance to make later improvement.  
  * This should be factored back into the project plan.
  * Significant debt becomes work items that are placed onto the development roadmap, rather than forgotten and left to fester.
  
## A Case for Code Reuse

### Reuse Case 1: The Copy-Pasta

> **Key:**  Avoid copy-and-paste coding.  Factor your logic into shared functions and common libraries, rather than suffer duplicated code (and duplicated bugs).

> **Key:**  Don't copy code you find on the Web into your project without carefully inspecting it first.

### Reuse Case 2: Design for Reuse

  * Focus on constructing the simplest code that satisfies the requirements right now. Write only what's needed, and create the smallest, most appropriate API possible.
    * Then, when another program wants to incorporate this component, you can add or extend the existing, working code. 

### Reuse Case 3: Promote and Refactor

> **Key:**  Code should be "shared" because it is useful to multiple clients, not because the developers want to create a nifty shared library.

### Reuse Case 4: Buy in, or reinvent the wheel

> **Key:**  Don't dismiss other people's code. It may be better to use existing libraries rather than write your own version.

## Effective Version Control

## Getting One Past the Goalpost

## The Curious Case of the Frozen Code

## Please Release Me
