C# Cheatsheet
===

This is a summary of a few important aspects of the language and the .Net platform.

**C# version:** 10.0  
**.Net version:** 6.0

Content
---
1. [Creating a project](#creating-a-project)
1. [Running a project](#running-a-project)
1. [String interpolation](#string-interpolation)
1. [String escaping](#string-escaping)
1. [Arrays](#arrays)

## Creating a projetct

To list the templates:  
`dotnet new --list`

Create a new project defining name and folder:  
`dotnet new <project_type> -n <project_name> -o <path>`

Common project types:  
`console | webapi | mvc | blasorwasm | xunit`

## Running a project

To run a project:  
`cd <project_name> && dotnet run`

## String interpolation

Defining some values for string interpolation:  
```
int age = 25;
var name = "Ellen";
```

Using String.Format():  
`string str = String.Format("Her name is {0} and she is {} years old.", name, age);`

Using `$` literal:  
`string str = $"Her name is {name} and she is {age} years old.";`

## String escaping

Using `\` (backslash):  
`string folder = "\\home\\ellen\\";`  
`string str = "He said \"Hello!\"";`

Using `@` literal:  
`string folder = @"\home\ellen\";`  
`string str = @"He said "Hello!"";`

Iterpolation and escaping:  
```
var name = "Ellen";
var str = $@"Her name is {name} and she said "Hello!"";
```

## Arrays

Big O time for common operations:

Operation | Time
--------- | ----
Read      | O(1)
Insert    | O(n)

For simplicity, I'll use an array of integers as example.

The size of the array must be specified when the array is initialized.

Declaring an array:  
`int[] array1;`

Declaring an array of arrays:  
`int[][] array1;`

Defining an array of size 5:  
`int[] array1 = new int[5];`

Defining an array of arrays of size 3:  
`int[][] arrays1 = new int[3][];`

**Note:** arrays defined without values will be initialized to their default values (i.e. 0, false, null).

Declaring and initializing an array of size 5:  
`int[] array1 = { 1, 2, 3, 4, 5 };`

Declaring and initializing an array of arrays:
```
int[][] arrays1 = {
    new int[] { 1, 2, 3, 4 },
    new int[] { 2, 4, 6, 8 },
    new int[] { 5, 10, 15, 20, 25}
};
```

**Note:** for an array of arrays, each sub-array can have a different size.
