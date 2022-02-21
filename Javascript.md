# INBOX
* windows clipboard history: `Win+V`
* running unsigned powershell scripts:
  * run powershell as admin
  * `Unblock-File <filename> 
* `window.getComputedStyle(block).backgroundColor`
* log how I added event listeners to the table
* Good video on arrays I should check out ("Wes Bos Array Cardio" - https://www.youtube.com/watch?v=HB1ZC7czKRs&t=233s)





# GIT/GITHUB
* **branch management:**
  * create and switch to a new branch with `git checkout -b <branch-name>`
  * switch to an existing branch with `git checkout <branch-name>`
  * merge a branch:
    1. commit and push all changes
    1. switch into the branch you would like to merge into 
    1. verify in correct branch
    2. `git merge <branch-to-be-merged>`


# JAVASCRIPT

<hr>

## **== Basics ==**

* **Variables**
    * Use `let` not `var`
    * string, BigInt, bool, number, object, undefined (no value assigned), null (baiscally `None`)
        * get type: `typeof <var>`
* **Comparisons**
    * `==` uses type coercion (converts to same type before comparing), `===` does not
* **Increment/decrement**
    * `++`/ `--` can be placed before after a variable. This affects the return value
        * before = normal += behaviour (value after increment is returned)
        * after = returns the value of the variable before incrementing
* **String syntax**:
    * `"` and `'` do the same thing
    * bacticks (```) denote a concatentation string, where a variable name can be included. See following code snippet:
        
    ```jsx
    const name = 'Chris';
    const greeting = `Hello, ${name}`;
    console.log(greeting); // "Hello, Chris"
    ```
* **String Manipulation**:
    * `slice(start, end)`: normal-ass slice
    * `substring(start, end)`: slice but worse (can’t accept negative indexes)
    * `substr(start, length)`: gets number of characters after start character. rest of string if no length is specified
* **Math Functions:**
  * rounding: `Math.round(num * 10) / 10`
  * random number: Where max is the number of random numbers you want to generate 
    `Math.floor(Math.random() * max)`
* **Imports/Exports and multi-file projects:**
  * syntax
    ```jsx
    // Importing stuff
    import * as name from "module-name"; // import everything from a module
    import { export1 , export2 } from "module-name"; // import specific functions from a module - presumably this works for classes as well

    // Exporting stuff
    export function() { // Best way is just to prefix everything with export
      do.stuff();
    } 

    export {sayHi as hi, sayBye as bye}; // If you wnat to simplify names you can declare exports at the end using this pattern
    ``` 
  * MASSIVE discussion of JS design patterns: https://softwareengineering.stackexchange.com/questions/180585/are-there-any-oo-principles-that-are-practically-applicable-for-javascript
  * MDN full reference article: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import 

<hr>
<br>

## **==Logic Flows ==**

* **if/else statements:**
  * same thing as python basically
  * syntax: 
    ```jsx
    if (condition1) {
        //  block of code to be executed if condition1 is true
    } else if (condition2) {
        //  block of code to be executed if the condition1 is false and condition2 is true
    } else {
        //  block of code to be executed if the condition1 is false and condition2 is false
    } 
    ```
* **switch statements:**
  * kinda works like if-else
  * syntax:
    * note the need for `break` statements
    ```jsx
    switch (logical expression) {
	case x:
		// if expression resolves to x, execute code block
		break;
	case y:
		// if expression resolves to y, execute code block
		break;
	default:
		// if no matching value found, execute default code block
    }
    ```
* **ternary operator:** 
  * used when assigning a variable based on conditions
  * syntax:
    ```jsx
    let result = condition ? value1 : value2;
    ```






<hr><br>

## **== Functions ==**


* **Basic Functions:**
  * Syntax:
        ```jsx
        function myFunction() {
            alert('hello');
        }       
        ```
  * Works similar to python, in that you can specify default arguments like `function myFunction(name="Default name")
    * Not sure whether you need to specify the parameter name when you give it, though. Not sure what the difference between optional and default is here. Based on the example below, you definitely don't _have_ to specify the variable name.
        ```jsx
        function hello(name='Chris') {
            console.log(`Hello ${name}!`);
        }

        hello('Ari'); // Hello Ari!
        hello();      // Hello Chris!
        ```
  * functions can take any number of arguments. 
    * access them with the `arguments` variable
    * build array from function arguments: 
      ```jsx
      args = Array.from(arguments)
      ```
* **Function Expressions:**
* **Anonymous Functions:**
  * This is super weird. Basically, you can define a function without a name ("anonymous") like so:
  
    ```jsx
    function() {
        alert('hello');
    }
    ```

  * Anonymous functions are often used to pass as parameters to other functions, which are probably expecting to receive functions as parameters.
    *_I still don't see why you wouldn't just give it a name though..._
  * Ah, here's an example. Adding event listeners. With a normal function:
    ```jsx
    function logKey(event) {
        console.log(`You pressed "${event.key}".`);
    }

    textBox.addEventListener('keydown', logKey);
    ```
    
    And now with an anonymous funciton:
    ```jsx
    textBox.addEventListener('keydown', function(event) {
        console.log(`You pressed "${event.key}".`);
    });
    ```

    This lets us define the logic of an eventListener inline, which definitely makes sense/is nicer to read. YAY!
* **Arrow Functions - Summary:**
  * Arrow functions are a nicer, more convenient format for defining anonymous functions.
  * Form:
    * results would equal: `<parameter> => <operation>`
  * The rules are as follows:
    * Remove "function" preceeding the brackets
    * If only 1 line in curly braces, omit curly braces
    * If only 1 parameter, remove brackets around it
    * If only 1 line and returns a value, no need for return statement
* **Arrow Functions - Detail:**
  * Here's the most basic example:
    ```jsx
    textBox.addEventListener('keydown', (event) => { // instead of function(event)
        console.log(`You pressed "${event.key}".`);
    });
    ```
    All it does is remove the "function" preceeding the brackets. Now, let's make it simpler.
  * If there is only one line between the curly braces, we can omit those.
    ```jsx

    textBox.addEventListener('keydown', (event) => console.log(`You pressed "${event.key}".`));
    ```
  * If there is only one parameter, we can omit the brackets around the parameter
    ```jsx
    textBox.addEventListener('keydown', event => console.log(`You pressed "${event.key}".`));
    ``` 
  * And lastly, if the function returns a value and contains only one line, we can omit the `return` statements. So this:
    ```jsx
    function doubleItem(item) {
        return item * 2;
    }
    ``` 
    becomes this:
    ```jsx
    item => item *2
    ```


<hr><br>

## **== Dev Tools ==**

This page has links to a lot of different resources explaning stuff like the network section, checking what scripts are running, emulating different connection speeds, etc: https://www.theodinproject.com/paths/foundations/courses/foundations/lessons/javascript-developer-tools

<hr><br>

## **== Arrays ==**

* Built-in functions:
  * convert to string: `array.toString()`
  * remove + return elements:
    * last element: `array.pop()`
    * first element: `array.shift()`
    * multiple elements (no replacement):
      * `slicedArray = array.slice(startIndex, endIndex)`
      * `endIndex` is optional
      * slice() stops BEFORE `endIndex` (like python string slicing)
    * multiple elements (can also replace with new ones):
      * `deletedItems = array.splice(startPosition, numElements, "newElement1", "newElementN")`
  * add elements to array: 
    * at end: `array.push()`
    * at start: `array.unshift()`
  * change elements: `array[x] = "new value"`
  * concat two arrays: `newArray = array1.concat(array2, array3, "value4")`
  * copy values from array (not reference): `let copyArray = [...originalArray]`
* Custom functions
  * shuffleArray(array): 
      ```jsx
      function shuffleArray(array) {
        for (var i = array.length - 1; i > 0; i--) {
            var j = Math.floor(Math.random() * (i + 1));
            var temp = array[i];
            array[i] = array[j];
            array[j] = temp;
          }
      }
      ```
  
<br><hr>

## **== Loops ==**

* loop logic statements
  * `break`
  * `continue`
  * labels let you use the above statements in outer loops
    * syntax:
      ```jsx
      outer: for (let i = 0; i < 3; i++) {

        for (let j = 0; j < 3; j++) {

          let input = prompt(`Value at coords (${i},${j})`, '');

          // if an empty string or canceled, then break out of both loops
          if (!input) break outer; // (*)

          // do something with the value...
        }
      }

      alert('Done!');
      ```
* for:
  * syntax:
    ```jsx
    for (let i = 0; i < 3; i++) { // shows 0, then 1, then 2
      alert(i);
    }
    ```
  * any part of the while loop can be skipped - this (this article)[https://javascript.info/while-for] for more details.
* while:
  * basic syntax:
    ```jsx
      while (logical statement) {
        do x;
        do y;
      }
    ```
  * if only 1 line, curly braces can be omitted:
    ```jsx 
    while (logic) alert(x);
    ```
* do-while:
  * the condition check can also run at the end of the while loop (guaranteeing that it runs at least once):
    ```jsx
    let i = 0;
    do {
      alert( i );
      i++;
    } while (i < 3);
    ``` 

## **== DOM Manipulation ==**

* **querySelectors vs getElementBy**: 
  * query selector lets me get anything using stylesheet-type identifiers - getElementBy is more limited. 
* **query selectors:**
  * we can use the selectors we would use in CSS to get HTML elements from a webpage using javascript
  * `element.querySelector(selector)` - returns the child of the element which matches the `selector` criteria
  * `element.querySelectorAll(selector)` returns all children matching the `selector`. 
    * NB: A NodeList is returned, not an array. Can be converted using `resultsArray = Array.from(source)`
* **creating element objects:**
  * `document.createElement(tagName, [options])`
  * doesn't put element on the page - just puts the object in memory so we can start to edit it.
* **adding element objects to DOM:**
  * `parentNode.appendChild(childNode)` adds `childNode` as the last node of `parentNode`
  * `parentNode.insertBefore(newNode, referenceNode)` can be used to insert an element at an arbitrary position. It insterts `newNode` before `referenceNode`, where `referenceNode` is a child of `parentNode`.
* **remove elements from DOM:**
  * `parentNode.removeChild(child)` removes `child` from the parent, and returns a reference to it  
* **altering elements:**
  * add inline style
    ```jsx
    div.style.color = 'blue';                                      
    // adds the indicated style rule

    div.style.cssText = 'color: blue; background: white';          
    // adds several style rules

    div.setAttribute('style', 'color: blue; background: white');    
    // adds several style rules
    ```
  * edit attributes
    * attributes are basically the metadata of html tags
      ```jsx
      div.setAttribute('id', 'theDiv');                              
      // if id exists, update it to 'theDiv', else create an id
      // with value "theDiv"

      div.getAttribute('id');                                        
      // returns value of specified attribute, in this case
      // "theDiv"

      div.removeAttribute('id');                                     
      // removes specified attribute
      ```
  * working with classes
    * often better to toggle a class than add inline styling
      ```jsx
      div.classList.add('new');                                      
      // adds class "new" to your new div

      div.classList.remove('new');                                   
      // removes "new" class from div

      div.classList.toggle('active');                                
      // if div doesn't have class "active" then add it, or if
      // it does, then remove it
      ```
  * editing text content
      ```jsx
      div.textContent = 'Hello World!'                               
      // creates a text node containing "Hello World!" and
      // inserts it in div
      ```
  * adding html content
      ```jsx
      div.innerHTML = '<span>Hello World!</span>'; // overwrites element's inner htmlContent with the specified html 
      div.innerHTML += '<span>Hello World!</span>'; // appends specified html string to element's content 
      ```



## **== OBJECTS ==**

* classes 
  * detailed guide here: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes
  * access any defined properties with `.` notation (remember, this is basically just an object)
  * syntax
     ```jsx
     class Rectangle {
        height = 0;
        width;
      constructor(height, width) {
        this.height = height;
        this.width = width;
      }
      // Getter
      get area() {
        return this.calcArea();
      }
      // Method
      calcArea() {
        return this.height * this.width;
      }
    }
    ```
    * specify properties before constructor to make "field declarations", which I'm pretty sure make those properties visible to an IDE
    * doesn't seem necessary to use a variable keyword (like `let`) when declaring properties
    * propertiescan be made private with `#` NOTE: not sure what "private" really means in this context 
  * adding methods
    * 

## **== EVENTS ==**

* basic list of events: 
    click
    dblclick
    keypress
    keydown
    keyup
* more complete list here: https://www.w3schools.com/jsref/dom_obj_event.asp

* add event listener
    ```jsx
    element.addEventListener('<event-type>', function (event-object) {
      console.log(event-object);
    });
    ```
* add event listener to multiple elements
  * first use `querySelectorAll` to get a nodeList
  * then, use `nodeList.forEach` as follows:
    ```jsx 
    // buttons is a node list. It looks and acts much like an array.
    const buttons = document.querySelectorAll('button');

    // we use the .forEach method to iterate through each button
    buttons.forEach((button) => {

      // and for each one we add a 'click' listener
      button.addEventListener('click', () => {
        alert(button.id);
      });
    });
    ```

# CSS

## **== Settings I Like ==**
* fullscreen, dark app:
    ```css
    body, main {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        background-color: #383232;
        font-family: sans-serif;
    }

    main {
        height: 90vh;
    }
    ```


  * background-color: k 


# HTML 

## **== SEMANTIC HTML ==**
  * Link to semantic html elements: https://www.w3schools.com/html/html5_semantic_elements.asp 



# STATIC-SITE GENERATORS

## HEXO

* **installation and setup**
  * to install: `npm install hexo` (full docs: https://hexo.io/docs/#Install-Hexo)
  * to setup site: 
    ```bash
    hexo init <folder>
    cd <folder>
    npm install
    ```
* **directory overview**
  * layout:
    ```
    .
    ├── _config.yml
    ├── package.json
    ├── scaffolds
    ├── source
    |   ├── _drafts
    |   └── _posts
    └── themes 
    ```
  * elements:
    * `config.yml`: configuration file, see (docs)[https://hexo.io/docs/configuration]
    * `package.json`: standard Node stuff
    * `scaffolds`: when a new post is created, Hexo bases the new file on the scaffold (base page layout, basically)
    * `source`: this is where site content goes.
      * hidden files, and files/folders prefixed with `_` are ignored - except for `_posts`
      * renderable posts (HTML/.md) will be processed and put into `public` folder on generation, others will simply be copied 
    * `themes`: affects rendering and layout
* **configuration**
  * 
* **github pages deployment**
  * follow the steps defined in the documentation: https://hexo.io/docs/github-pages#One-command-deployment
    * this essentially creates an automated workflow that builds the Hexo site from the uploaded github project. The site is built on a `gh-pages` branch, which the workflow creates automatically.
  * edit the `url` field in `config.yml` to be the URL supplied by Github Pages
  * change the pages generation branch to `gh-pages`
* **running**
  * `hexo generate` to build static files
  * `hexo server` to start local server 
  * `hexo deploy -g` generates and deploys website (not sure what `deploy` means yet)
* **troubleshooting**
  * "Cannot read property 'nodes' of undefined"
    * Caused by having `#` in the filepath - removed that and it was fixed. 
# STUFF