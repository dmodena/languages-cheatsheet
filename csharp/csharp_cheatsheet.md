C# Cheatsheet
===

This is a summary of a few important aspects of the language and the .Net platform.

**C# version:** 10.0  
**.Net version:** 6.0

Content
---
1. [Creating a project](#creating-a-project)
1. [Running a project](#running-a-project)

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
