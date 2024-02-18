C# Cheatsheet
===

This is a summary of a few important aspects of the language and the .Net platform.

**C# version:** 10.0  
**.Net version:** 6.0

Content
---
1. [Creating a project](#creating-a-project)
1. [Running a project](#running-a-project)
1. [Naming conventions](#naming-conventions)
1. [String interpolation](#string-interpolation)
1. [String escaping](#string-escaping)
1. [Arrays](#arrays)
1. [Dictionaries](#dictionaries)

## Creating a project

To list the templates:  
`dotnet new --list`

Create a new solution:  
`dotnet new sln -n <solution_name> -o <path>`

**Note:** you can omit the `-m` flag if the path and the project or solution have the same name.

Create a new project defining name and folder:  
`dotnet new <project_type> -n <project_name> -o <path>`

Common project types:  
`console | webapi | mvc | blasorwasm | xunit`

Add project to solution:  
`dotnet sln [<solution_name>] add <project_path> [<project_path>...]`

List projects in a solution:  
`dotnet sln [<solution_name>] list`

**Note:** the solution name is optional if you are in the same folder as the .sln file, and there is only one .sln file in the folder.

## Running a project

To run a project:  
`cd <project_name> && dotnet run`

## Naming conventions

Classes and Methods are PascalCase:  
`public class MyClass`  
`public string SayHello()`

Variables and arguments are camelCase:  
`string lastName;`
`string SayHello(string lastName)`

Constants are PascalCase:  
`const string Hey = "Hey";`

Public properties are PascalCase:  
`customer.City = "Frankfurt";`

Private properties are camelCase and start with _ (underscore):  
`private ILogger _logger;`

Interface names start with the letter I:  
`public interface IRepository`

## String interpolation

Defining some values for string interpolation:  
```C#
int age = 25;
var name = "Ellen";
```

Using String.Format():  
`string str = String.Format("Her name is {0} and she is {1} years old.", name, age);`

Using `$` literal:  
`string str = $"Her name is {name} and she is {age} years old.";`

## String escaping

Using `\` (backslash):  
`string folder = "\\home\\ellen\\";`  
`string str = "He said \"Hello!\"";`

Using `@` literal:  
`string folder = @"\home\ellen\";`  
`string str = @"He said ""Hello!""";`

**Note:** for escaping quotes with the @ literal, the quotes need to be duplicated.

Interpolation and escaping:  
```C#
var name = "Ellen";
var str = $@"Her name is {name} and she said ""Hello!""";
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

Declaring a two-dimensional array:  
`int[,] matrix1;`

**Note:** arrays can be multidimensional.

Defining an array of size 5:  
`int[] array1 = new int[5];`

Defining an array of arrays of size 3:  
`int[][] arrays1 = new int[3][];`

**Note:** for an array of arrays, each sub-array can have a different size, hence the number of columns is not specified during definition.

Defining a 2D array of size 3x3:  
`int[,] matrix1 = new int[3,3];`

**Note:** arrays defined without values will be initialized to their default values (i.e. 0, false, null).

Declaring and initializing an array of size 5:  
`int[] array1 = { 1, 2, 3, 4, 5 };`

Declaring and initializing an array of arrays:
```C#
int[][] arrays1 = {
    new int[] { 1, 2, 3, 4 },
    new int[] { 2, 4, 6, 8 },
    new int[] { 5, 10, 15, 20, 25}
};
```

Declaring and initializing a two-dimensional array:
```C#
int [,] matrix1 = {
    { 1, 2, 3 },
    { 2, 4, 6 },
    { 3, 6, 9 }
};
```

To get the number of dimensions that a multidimensional array has:  
`matrix1.Rank;`

To get the length of the array:  
`array1.Length;`

Multidimensional arrays will return the total number of elements for their lengths:  
```C#
int[] arr1 = { 1, 2, 3 };
int[,] arr2D = { { 1, 2, 3 }, { 4, 5, 6 } };
Console.WriteLine(arr1.Length); // 3
Console.WriteLine(arr2D.Length); // 6
```

Get number of columns for a row in an array of arrays:
```C#
arrays1[0].Length;
arrays1[1].Length;
```

Get the size of each dimension in a multidimensional array:
```C#
multi1.GetLength(0);
multi1.GetLength(1);
multi1.GetLength(2);
```

Iterate through simple array:
```C#
for (var i = 0; i < array1.Length; i++)
    var number = array1[i];
```

Iterate through array of arrays:
```C#
for (var i = 0; i < arrays1.Length; i++) {
    for (var j = 0; j < arrays1[i].Length; j++) {
        var number = arrays1[i][j];
    }
}
```

Iterate through 2D array:
```C#
for (var i = 0; i < matrix1.GetLength(0); i++) {
    for (var j = 0; j < matrix1.GetLength(1); j++) {
        var number = matrix1[i,j];
    }
}
```

Getting element by position:
```C#
array1[2];
arrays1[1][2];
matrix1[1,2];
```

Update element at position:
```C#
array1[2] = 42;
arrays1[1][2] = 42;
matrix2[1,2] = 42;
```

**Note:** arrays are fixed-sized structures, so it is not possible to append, prepend and delete items easily. If you want to append an item, for instance, you first need to resize your array, then add the item to the last index. Prepending would require manual relocation of all items. If your algorithm requires frequent appending, you could probably use a List instead of the array.

Append item to array:  
```C#
int[] array1 = { 1, 2, 3 };
Array.Resize(ref array1, array1.Length + 1);
array[3] = 4;
```

## Dictionaries

To create a typed dictionary, include its namespace:  
```C#
using System.Collections.Generic;
```

Declaring a new Dictionary:  
```C#
var romanNumerals = new Dictionary<int, string>();
```

Adding new entries:  
```C#
romanNumerals.Add(1, "I");
romanNumerals.Add(5, "V");
```

Declaring and adding values at once:  
```C#
var romanNumerals = new Dictionary<int, string>() {
    { 1, "I" },
    { 5, "V" },
    // ...
}
```

Get value from known key:  
```C#
var valueOfFive = romanNumerals[5];
```

Check if a key exists:  
```C#
var exists = romanNumerals.ContainsKey(10);
```

Get value if key exists:  
```C#
var exists = romanNumerals.TryGetValue(10, out var roman);

if (exists)
    Console.WriteLine($"10 = {roman}");
```

Update existing value:  
```C#
romanNumerals[50] = "L";
```

Iterate through entries:  
```C#
foreach(var entry in romanNumerals) {
    Console.WriteLine($"Value of {entry.Key} is {entry.Value}");
}
```
