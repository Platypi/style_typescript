# TypeScript Style Guide

This is the TypeScript style guide that we use internally at Platypi! It is *semi-reasonable*, but it's more important that we keep a consistent look/feel of our code.


## Table of Contents

  1. [Introduction](#introduction)
  1. [Browser Compatibility](#browser-compatibility)
  1. [File Naming Conventions](#file-naming-conventions)
  1. [Indentation](#indentation)
  1. [Line Length](#line-length)
  1. [Quotes](#quotes)
  1. [Comments](#comments)
    1. [Class](#class)
    1. [Inline](#inline)
    1. [Todo and XXX](#todo-and-xxx)
  1. [Variable Declarations](#variable-declarations)
  1. [Function Declarations](#function-declarations)
    1. [Anonymous Functions](#anonymous-functions)
  1. [Names](#names)
    1. [Variables, Modules, and Functions](#variables-modules-and-functions)
    1. [Classes](#classes)
    1. [Interfaces](#interfaces)
    1. [Constants](#constants)
  1. [Statements](#statements)
    1. [Simple](#simple)
    1. [Compound](#compound)
    1. [Return](#return)
    1. [If](#if)
    1. [For](#for)
    1. [While](#while)
    1. [Do While](#do-while)
    1. [Switch](#switch)
    1. [Try](#try)
    1. [Continue](#continue)
    1. [Throw](#throw)
  1. [Whitespace](#whitespace)
  1. [Object and Array Literals](#object-and-array-literals)
  1. [Assignment Expressions](#assignment-expressions)
  1. [=== and !== Operators](#===-and-!==-Operators)
  1. [Eval](#eval)

## Introduction
When developing software as an organization, the value of the software produced is directly affected by the quality of the codebase. Consider a project that is developed over many years and handled/seen by many different people. If the project uses a consistent coding convention it is easier for new developers to read, preventing a lot of time/frustration spent figuring out the structure and characteristics of the code. For that purpose, we need to make sure we adhere to the same coding conventions across all of our products. This will not only help new developers, but it will also aid in quickly identifying potential flaws in the code, thereby reducing the brittleness of the code.

**[top](#table-of-contents)**

## Browser Compatibility
  - Target modern browsers (>=ie9)

**[top](#table-of-contents)**

## File Naming Conventions
  - All TypeScript files must have a ".ts" extension.
  - They should be all lower case, and only include letters, numbers, and periods. 
  - It is OK (even recommended) to separate words with periods (e.g. `my.view.html`).

**[top](#table-of-contents)**

## Indentation
  - The unit of indentation is four spaces. 
  - **Never use tabs**, as this can lead to trouble when opening files in different IDEs/Text editors. Most text editors have a configuration option to change tabs to spaces.

**[top](#table-of-contents)**

## Line Length
  - Lines must not be longer than 140 characters. 
  - When a statement runs over 140 characters on a line, it should be broken up, ideally after a comma or operator.

**[top](#table-of-contents)**

## Quotes
  - Use single-quotes `''` for all strings, and use double-quotes `""` for strings within strings.

  ```typescript
  // bad
  var greeting = "Hello World!";
  
  // good
  var greeting = 'Hello World!';
  
  // bad
  var html = "<div class='bold'>Hello World</div>";
  
  // bad
  var html = '<div class=\'bold\'>Hello World</div>';
  
  // good
  var html = '<div class="bold">Hello World</div>';
  ```

**[top](#table-of-contents)**

## Comments
  - Comments are strongly encouraged. It is very useful to be able to read comments and understand the intentions of a given block of code. 
  - Comments need to be clear, just like the code they are annotating. 
  - Make sure your comments are meaningful. 

The following example is a case where a comment is completely erroneous, and can actually make the code harder to read.

  ```typescript
  // Set index to zero.
  var index = 0;
  ```
    
  - All public functions must have a comment block `/**...*/` using [JSDoc](http://usejsdoc.org/) style comments. 

JSDocs can be interpreted by IDEs for better intellisense. Below is an example of a JSDoc comment block for a function.

  ```typescript
  /**
   * Takes in a name and returns a greeting string.
   * 
   * @param name The name of the greeted person.
   */
  function getGreeting(name: string) {
      return 'Hello ' + name + '!';
  }
  ```

### Class

  - All classes must have block comments `/**...*/` for all public variables and functions. 
  - All public functions should use [JSDoc](http://usejsdoc.org/) style comments. 
  - Functions need to have a comment explaining what the function does, and all of the input parameters need to be annotated with `@param`. 
  - The class should include a block comment containing the description of the class
  - The constructor should contain a JSDoc comment annotating any input parameters.

  ```typescript
  /**
   * Contains properties of a Person.
   */
  class Person {
      /**
       * Returns a new Person with the specified name.
       * 
       * @param name The name of the new Person.
       */
      static GetPerson(name: string) {
          return new Person(name);
      }
      
      /**
       * @param name The name of the new Person.
       */
      constructor(public name: string) { }

      /**
       * Instructs this Person to walk for a certain amount 
       * of time.
       *
       * @param millis The number of milliseconds the Person 
       * should walk.
       */
      walkFor(millis: number) {
          console.log(this.name + ' is now walking.');
          
          setTimeout(() => {
              console.log(this.name + ' has stopped walking.');
          }, millis);
      }
  }
  ```

### Inline

  - Inline comments are comments inside of complex statements (loops, functions, etc). 
  - Use `//` for all inline comments. 
  - Keep comments clear and concise. 
  - Place inline comments on a newline above the line they are annotating
  - Put an empty line before the comment.

  ```typescript
  // bad
  var lines: Array<string>; // Holds all the lines in the file.
  
  // good
  // Holds all the lines in the file.
  var lines: Array<string>;
  
  // bad
  function walkFor(name: string, millis: number) {
      console.log(name + ' is now walking.');
      // Wait for millis milliseconds to stop walking
      setTimeout(() => {
          console.log(name + ' has stopped walking.');
      }, millis);
  }
  
  // good
  function walkFor(name: string, millis: number) {
      console.log(name + ' is now walking.');
      
      // Wait for millis milliseconds to stop walking
      setTimeout(() => {
          console.log(name + ' has stopped walking.');
      }, millis);
  }
  ```

### Todo and XXX

`TODO` and `XXX` annotations help you quickly find things that need to be fixed/implemented. 

  - Use `// TODO:` to annotate solutions that need to be implemented. 
  - Use `// XXX:` to annotate problems the need to be fixed. 
  - It is best to write code that doesn't need `TODO` and `XXX` annotations, but sometimes it is unavoidable. 

**[top](#table-of-contents)**

## Variable Declarations

  - All variables must be declared prior to using them. This aids in code readability and helps prevent undeclared variables from being hoisted onto the global scope. 
  
  ```typescript
  // bad
  console.log(a + b);

  var a = 2,
      b = 4;

  // good
  var a = 2,
      b = 4;
      
  console.log(a + b);
  ```

  - Implied global variables should never be used. 
  - You should never define a variable on the global scope from within a smaller scope.
  
  // bad
  function add(a: number, b: number) {
      // c is on the global scope!
      c = 6;
      
      return a + b + c;
  }

**[top](#table-of-contents)**

## Function Declarations

### Anonymous Functions

**[top](#table-of-contents)**

## Names

### Variables, Modules, and Functions

### Classes

### Interfaces

### Constants

**[top](#table-of-contents)**

## Statements

### Simple

### Compound

### Return

### If

### For

### While

### Do While

### Switch

### Try

### Continue

### Throw

**[top](#table-of-contents)**

## Whitespace

**[top](#table-of-contents)**

## Object and Array Literals

**[top](#table-of-contents)**

## Assignment Expressions

**[top](#table-of-contents)**

## === and !== Operators

**[top](#table-of-contents)**

## Eval

**[top](#table-of-contents)**
