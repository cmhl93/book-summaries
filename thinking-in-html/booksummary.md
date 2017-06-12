##  Document Contents

[Getting started with HTML](#getting-started-with-html)

##  Getting started with HTML

  * HTML is a markup language and includes a set of markup tags. 
  * Basically, an HTML document has HTML tags and content. 
  * Let's have a look at the following code and understand its structure:
    ```
    <!DOCTYPE html>
    <html>
    <body>
    <p> Welcome to Packt </p>
    <p> Packt Lessons </p>
    </body>
    </html>
    ```
  * In the preceding code sample, <!Doctype html> is a declaration and lets the browser know that you are using HTML5. 
  * In HTML, tags are keywords surrounded by angular brackets (<>). They usually come in pairs. 
    * For example, html is the opening tag and closing tag. 
    * Similarly, p is the opening tag and closing tag. 
  * The <html> tag tells the browser that everything between it and the closing </html> tag is an HTML document.
  * The tags between <html> and </html> are also called elements. 
  * The tags do not get displayed in the browser; instead, they determine the manner in which content is presented to the user. 
  * The text between the <body> and </body> tags is the content that is presented to the user. 
  * The <p> tag is used to define paragraphs where you want to break up two streams of information. 
  * However, there is an exception to the rule; some tags such as br and hr do not have a closing tag. 
  
### The <head> element

  * The <head> and </head> tags appear before the <body> element. 
  * The <head> element gives you information about the web page, and the information doesn't get displayed in the browser.
  * The <head> tag is used to include script files responsible for styling and interactivity of the page. 
  
### Headers

  * Heading tags are used to differentiate the heading of a web page from the rest of the content.
  * There is a hierarchy, which means the content in h1 is the most important, and that in h6 is the least important one.
  * Headings are useful for Search Engine Optimization (SEO) purposes. 
  * Heading tags help describe what the web page is all about, and the search engine spiders look for specific information from the 
  heading tags, along with the content. 
