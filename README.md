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
    1. [Classes](#classes)
    1. [Inline](#inline)
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
Target modern browsers (>=ie9)

**[top](#table-of-contents)**

## File Naming Conventions
All TypeScript files must have a ".ts" extension. They should be all lower case, and only include letters, numbers, and periods. It is OK (even recommended) to separate words with periods (e.g. `my.view.html`).

**[top](#table-of-contents)**

## Indentation
The unit of indentation is four spaces. **Never use tabs**, as this can lead to trouble when opening files in different IDEs/Text editors. Most text editors have a configuration option to change tabs to spaces.

**[top](#table-of-contents)**

## Line Length
Lines must not be longer than 140 characters. When a statement runs over 140 characters on a line, it should be broken up, ideally after a comma or operator.

**[top](#table-of-contents)**

## Quotes
Use single-quotes `''` for all strings, and use double-quotes `""` for strings within strings.

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

### Classes

### Inline

**[top](#table-of-contents)**

## Variable Declarations

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
