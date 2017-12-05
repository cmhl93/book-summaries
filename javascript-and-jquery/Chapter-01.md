# The ABC of Programming

##  Document Contents

[What is a script?](#what-is-a-script)

[How do computers fit in with the world around them?](#how-do-computers-fit-in-with-the-world-around-them)

[How do I write a script for a web page?](#how-do-i-write-a-script-for-a-web-page)

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
  * The document object represents an HTML page
    * Like other objects that represent real-world things, the document object has:
      * Properties
        * Properties describe characteriestics of the current web page (such as the title of the page).
      * Methods
        * Methods perform tasks associated with the document currently loaded in the browser
      * Events
        * You can respond to events, such as a user clicking or tapping on an element.
    * When the browser creates a model of a web page, it not only creates a document object, but it also creates a new object    
  * How a browser sees a web page
    1.  Receive a page as HTML code
    2.  Create a model of the page and store it in memory
    3.  Use a rendering engine to show the page on screen
  * All major browsers use a JavaScript interpreter to translate your instructions (in JavaScript) into instructions the computer can follow.
  
##  How do I write a script for a web page? 

  * How HTML, CSS, & JavaScript fit together
    * Each language forms a separate layer with a different purpose.
    * <html>
      * CONTENT LAYER
      * .html files
      * This is where the content of the page lives.  The HTML gives the page structure and adds semantics.
    * {css}
      * PRESENTATION LAYER
      * .css files
      * The CSS enhances the HTML page with rules that state how the HTML content is presented (backgrounds, borders, box dimensions, colors, font, etc.)
    * javascript()
      * BEHAVIOR LAYER
      * This is where we can change how the page behaves, adding interactivity.  
  * Progressive Enhancement
    * These three layers form the basis of a popular aproach to building we pages called progressive enhancement.
    * HTML ONLY
      * Starting with the HTML layer allows you to focus on the most important thing about your site: its content
    * HTML & CSS
      * Adding the CSS rules in a separate file keeps rules regarding how the page looks away from the content itself.
    * HTML & CSS & JAVASCRIPT
      * The JavaScript is added last and enhances the usability of the page or the experience of interacting with the site
  * Creating a Basic JavaScript
    * JavaScript is written in plain text, just like HTML and CSS, so you do not need any new tools to write a script.
  * Linking to a JavaScript file from an HTML page
    * When you want to use JavaScript with a web page, you use the HTML <script> element to tell the browser it is coming across a script.
    * Its src attribute tells people where the JavaScript file is stored.
  * The Source Code is not amended
    * If you look at the source code for the example you just created, you will see that the HTML is still exactly the same.
  * Placing the script in the page
    * You may see JavaScript in the HTML between opening <script> and closing </script> tags (but it is better to put scripts in their own files). 
  * How to use objects & methods
    * This one line of JavaScript shows how to use objects and methods.
    * Programmers refer to this as calling a method of an object.
    `document.write('Good afternoon!');`
    * The document object represents the entire web page.  All web browsers implement this object, and you can use it just by giving its name.
    * The write() method of the document object allows new content to be written into the page where the <script> element sits.
    * Member operator
      * The document object has several methods and properties.  They are known as members of that object.
      * You can access the members of an object using a dot betwen the object name and the member you want to access.
      * It is called a member operator.
    * Parameters
      * Whenever a method requires some information in order to work, the data is given inside the parentheses.
      * Each piece of information is called a parameter of the method.  
      * In this case, the write() method needs to know what to write into the page.
  * JavaScript runs where it is found in the HTML
    * When the browser comes across a <script> element, it stops to load the script and then checks to see if it needs to do anything. 
    
