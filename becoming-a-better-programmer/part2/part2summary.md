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

 * Version control is the process of managing multiple revisions of a set of files. These are a commonly the source files for a software system, but it could just as easily be revisions of a document tree, or of anything else you'd store in a filesystem.
 
 * A good version control system, used well, brings us many benefits:
  * It provides a central collaboration hub
  * It maintains a history of the work on a project.
  * It provides the developer with a safety net.
  * It fosters a rhythm and cadence of work
  * It enables multiple concurrent streams of development to occur on the same codebase withoutt interference.
  * It enables reversibility.
  
### Use It or Lose It

> **Key:** Use version control. It is not optional or a nice-to-have tool. It is the backbone of development. Your work is at risk without it.

### Pick one, any one

 * The historical centralised systems funnel all communication through a central server that hosts the repository of all version-controlled files.
 * This is a simple model, but requires access to that server for any non-trivial operation.
 * The most recent VCS development is the distributed model, a peer-to-peer approach where each computer can host its own copy of the repository.  
  * This enables more impressive workflows, and allows you to interact with the repository even when away from a network connection.

### Storing the Right Things

#### Answer One: Store Everything

 * That means your repository must include:
  * All source code files
  * All documentation
  * All build files (makefiles, IDE setup, scripts)
  * All configuration files
  * All assets (graphics, sounds, install media, resource files)
  * Any third-party-supplied files (e.g., code libraries you depend on)
  
#### Answer Two: Store as Little as Possible

 * Keep the repository file structure as simple as you can. Specifically:
  * Don't store IDE configuration files or cache files.
  * Don't store generated artefacts - you needn't check in object files, library files, or application binaries if they are a result of the build process.
  * Don't store things that are not a part of your project
  * Don't check in test or bug reports.
  * "Interesting" project emails do not belong in the repository.
  * Don't store personal settings, like the colour scheme for you editor
  * Don't keep things in the repository that you think you might need one day.
  
> **Key:** Store every file that comprises your software project under version control. But store as little as possible; do not include any unnecessary files.

### Storing Software Releases

 * This is usually a separate "release" repository; the binaries do not really belong beside the source files.
 * Consider archiving these in a simple static directory structure elsewhere.
 
### Repository Layout

 * Include a helpfule "read me" document at the top level.
 * Mercilessly avoid duplication.
 * Manage third-party code carefully. Keep it separate from your own source files.
 
### Use Version control well

#### Make Atomic Commits

 * Check in changes little and often

#### Sending the Right Messages

 * This should start with a brief summary of what has changed, ideally one clear sentence. 
 * Then follow up with the reasons why you made the change, if these are of interest. 
 * If appropriate, include a bug reference number or other supporting information.
 * Ex: fix #4507: Utility windows load behind ACVS

#### Craft Good Commits
 
 * Don't break the build
 * Don't trash or move a file unless you know thhat everyone is done with it.
 * Don't let editors fight over line endings.
 
### Branches: Seeing the wood for the trees

 * Consider using them for:
  * Encapsulating revisions of the source tree.
  * Exploratory development work - the stuff you're not sure will work
  * Major changes that cut across a lot of the source tree and will take a while to complete, requiring many QA tests, and many individual check-ins to get right.
  * Individual bug fixes.
  * Separating volatile development from stable release lines.
  
### The Home for Your Code

> **Key:** Source code inhabits the VCS it is stored in. The more mature a project, the more deeply it relies on this habitat.

## Getting One Past the Goalpost

### What is QA Good for?

 * The "QA" department exists to ensure that your project ships a software product of sufficient quality.
  * They have to test the living daylights out of whatever the developers create in order to ensure:
   * That it matches the specification and requirements
   * That the software works correctly on all platforms
   * That no faults have been introduced in the latest build.
  * QA must be deeply involved throughout, not just a final adjunct to the development process
   * They have a hand in the specification of the software, to understand - and shape - what will be built
   * They contribute to design and construction, to ensure that what's built will be testable.
   * They are involved heavily in the testing phase, naturally.
   * And also in the final physical release.
   
### Software Development: Shovelling Manure

 * The process goes something like this:
  1. Someone pours some requirements into the mouth of the pipe.
  1. They flow through architects and designers, where they turn into specifications and pretty diagrams.
  1. This flows through the programmers, and turns into executable code.
  1. Then it flows into QA. Where it hits a blockage as the "perfectly formed" software magically turns into a nonfunctioning disaster. These people break the code!
  1. Eventually the developers push hard enough down the pipe to break this blockage, and the software finally flows out of the far end of the pipe.
  
> **Key:** It is wrong to view software development as a linear process.

### A False Dichotomy

> **Key:** Beware of fostering an artificial separation between development and testing efforts. 

### Fix the Team to Fix the Code

> **Key:** Unhealthy team interactions result in unhealthy code

### Releasing a Build to QA

> **Key:** Not creating a QA build thoughtfully and carefully shows a lack of respect to the testers.

 * Tests Your Work First
 * Release with Intent
 * More Haste, Less Speed
 > **Key:** Never rush the creation of a build. You will make mistakes
 * Automate
  * Automation of manual steps always removes the potential for human error.
 * Respect

### On Getting a Fault Report

> **Key:** Testing will only reveal problems that software developers added to the system (by ommission or commission). If they find a fault, it was your fault!

> **Key:** Don't take fault reports personally. They are not a personal insult!

### Our Differences Make Us Stronger

> **Key:** Cultivate a healthy respect for the QA team. Enjoy working with them to craft excellent software.

### Pieces of the Puzzle

> **Key:** The QA team is not the sole owner of, nore the gatekeeper of "quality". It's everyone's responsibility.

## The Curious Case of the Frozen Code

### Hunting the Code Freeze

 * A Code freeze denotes the period between some "done" point - when no further work is expected to be performed - and the release date.
 
> **Key:** "Code freeze" is the period leading up to a release when no changes are anticipated.

> **Key:** "Code freeze" is a misleading term. Code never stands still, even if you'd like it to.

### A New World Order

> **Key:** We slow down development work to carefully shepherd a code line to release, managing the final fixes and changes carefully.

### Forms of Freeze

 * Feature freeze
  * A feature freeze declares that only bug fixes may now be committed - no new features will be developed.
 * Code freeze
  * We no longer work on any features, nor on any bugs that have not been highly prioritised. We only accept fixes for "showstopping" issues.
 * "Hard" code freeze
  * No changes are allowed at all.
  
### Branches Make It Work

> **Key:** Branch or bust

### But it's not really frozen!

 * Be wary that the word "freeze" doesn't tempt you to keep things rigid when they should not be. When changes must be made, they must be made.
 
### Length of the Freeze

 * A typical freeze period length is two weeks
 * Beware the Pareto principle: we often see in IT projects where the "last" 20% of effort expands to take up 80% of the total time.
  * To avoid this, make sure you enter the freeze at the right point.
  
### Feel the Freeze

> **Key:** It's not unusual (or wrong) to ship software that you know could be better.

> **Key:** During code freeze you will accrue technical debt. Monitor this, and be prepared to pay the debt off soon after the release ships.

### The End Draws Near

> **Key:** The only true "code freeze" is when an acceptable release is made. This is the point that the code is finally set in stone.

### Antifreeze

 * We can minimise, and even remove, code freeze periods by:
  * Employing continuous delivery
  * Establishing a good automated test harness with good coverage.
  * Good acceptance criteria testing
  * Reduce the test period
  * Develop a simple and reliable "release pipeline" that will take your code and deploy in into production with little effort and no human intervention.
  
> **Key:** Aim for code that never "freezes" but is permanently ready to release to production.

## Please Release Me

> **Key:** Creating software releases requires discipline and planning. It is more than hitting "build" in a developer's IDE.

### A Cog in the Machine

#### Step 1: Initiate the Release

#### Step 2: Prepare the Release

 * A release branch is a stable snapshot of the code that alllows you to continue development of "unstable" features on the trunk.

#### Step 3: Build the Release

> **Key:** Make your build as simple as a single step that automates all parts of the process. Use a scripting language to do this.

> **Key:** Deploy your builds on a CI server to ensure their health. Make formal releases from the same system

#### Step 4: Package the Release

 * Package the code (create an installer image, CD ISO images, etc.)
 
#### Step 5: Deploy the Release

> **Key:** Never release software without testing the final artefacts.

### Release Early and Often

> **Key:** Do not defer the planning and construction of a software release process until the last minute. Build it early, iterate through builds rapidly and frequently. Debug the build like you'd debug any other software.
