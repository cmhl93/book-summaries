# The ABC of Programming

##  Document Contents

[What is a script?](#what-is-a-script)

[How do computers fit in with the world around them?](#how-do-computers-fit-in-with-the-world-around-them)

[How do I write a script for a web page?](#how-do-I-write-a-script-for-a-web-page)

##  What is a script?

  * A script is a series of instructions that a computer can follow to achieve a goal.  
    * You can compare scripts to any of the following:
      * Recipes
      * Handbooks
      * Manuals
    * Scripts are made up of instructions a computer can follow step-by-step.
    * A browser may use different parts of the script depending on how the user interacts with the web page.
    * Scripts can run different sections of the code in response to the situation around them.
  * To write a script, you need to first state your goal and then list the tasks that need to be completed in orfer to achieve it.
    * Start with the big picture of what you want to achieve, and break that down into smaller steps.
      1.  Define the goal
        * You can think of this as a puzzle for the computer to solve.
      2.  Design the script
        * To design a script you split the goal into a series of tasks that are going to be involved in solving this puzzle
        * Each individual tasks may be broken down into a sequence of steps.  
          * When you are ready to code the script, these steps can then be translated into individual lines of code.
      3.  Code each step
        * Each of the steps needs to be written in a programming language that the computer understands.

##  How do computers fit in with the world around them?

 * Computers create models of the world using data
 * Objects & properties
  * Objects (things)
    * In computer programming, each physical thing in the world can be represented as an object.  
    * There are two different types of objects here: a hotel and a car.
    * Programmers might say that there is one instance of the hotel object, and two instances of the car object.
    * Each object can have its own:
      * Properties
      * Events
      * Methods
    * Together they create a working model of that object.
  * Properties (Characteristics)
    * Each property has a name and a value, and each of these name/value pairs tells you something about each individiual instance of the project.
  * Events
    * What is an event?
      * Programs are designed to do different things when users interact with the computer in different ways.
      * An event is the computer's way of sticking up its hand to say, "Hey, this just happened!"
    * What does an event do?
      * A script will state which events the programmer wants to respond to, and what part of the script should be run when each of those events occur.
  * Methods
    * What is a method?
      * Methods typically represent how people interact with an object in the real world.
      * They are like questions and instructions that:
        * Tell you something about that object (using information stored in its properties)
        * Change the value of one or more of that object's properties
    * What does a method do?
      * When you use a method, you do not always need to know how it achieves its task; you just need to know how to ask the question and how to interpret any answers it gives you.
  * Web browsers are programs built using objects
    * Window object
      * The brower represents each window or tab using a window object.
      * The location property of the window object will tell you the URL of the current page.
    * Document object
      * The current web page loaded into each window is modelled using a document object.
      * The title property of the document object tells you what is beween the opening <title> and closing </title> tag for that web page, and the lastModified property of the document object tells you the date this page was last updated.
    
