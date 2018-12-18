# C# Coding Conventions
We created this style guide to keep the code in Virto Commerce consistent.

The goal is to help library designers ensure API consistency and ease of use by providing a unified programming model that is independent of the programming language used for development.

These guidelines are based on C# and Microsoft conventions.

We recommend that you follow these design guidelines when developing classes and components that extend the .NET Framework. Inconsistent library design adversely affects developer productivity and discourages adoption.

These guidelines are organized as simple recommendations prefixed with the terms: 

**Do** is one that should always be followed. Always might be a bit too strong of a word. Guidelines that literally should always be followed are extremely rare. On the other hand, you need a really unusual case for breaking a Do guideline.

**Consider** guidelines should generally be followed. If you fully understand the meaning behind the guideline and have a good reason to deviate, then do so. Please strive to be consistent.

**Avoid** indicates something you should almost never do. Code examples to avoid have an unmistakable red header.

**Do not** Just don't do it.

**Why?** gives reasons for following the previous recommendations.

Note: A guideline is flexible and can be adjusted and improved.

## Fix Issues Before They Exist
This set of tools and extension that helps you detect and fix quality issues as you write code. 
You must use these tools and fix the errors before commit to repository.

### Use PowerCommands For Visual Studio
[Install Productivity Power Tools](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.PowerCommandsforVisualStudio)

Go to “Tools > Options > Productivity Power Tools > PowerCommands” and Enable “Format documents on save” and “Remove and Sort Usings on save”.

### Use SonarLint
[SonarLint](https://www.sonarlint.org/) is an IDE extension that helps you detect and fix quality issues as you write code.
Like a spell checker, SonarLint squiggles flaws so that they can be fixed before committing code.

[Install SonarLint in Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)

[List of C# rules](https://rules.sonarsource.com/csharp)

### Use Visual Studio Code Analyzes
We recommend to use  use the Microsoft Rules rule set to focus on the most critical problems in your code, including potential security holes, application crashes, and other important logic and design errors. 

Go to "Visual Studio > Analyze > Run Code Analysis > On Solution".

[List of rules](https://docs.microsoft.com/en-us/visualstudio/code-quality/all-rules-rule-set?view=vs-2017)

## C# CODING CONVENTIONS - BASIC RECOMMENDATIONS
Read [Coding Conventions](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)

## C# FRAMEWORK DESIGN GUIDELINES
Read [Design Guidelines](https://docs.microsoft.com/en-us/dotnet/standard/design-guidelines/)

These guidelines are excerpted from the book FRAMEWORK DESIGN GUIDELINES: CONVENTIONS, IDIOMS, AND PATTERNS FOR REUSABLE .NET LIBRARIES, 2ND EDITION, by Krzysztof Cwalina and Brad Abrams. 

## VIRTO COMMERCE C# CODING CONVENTIONS

### Naming
Naming conventions are hugely important to maintainability and readability. This guide recommends naming conventions for the file name and the symbol name.

**Do** Names of private fields and constants should start with `_` and lowercase letter

**Don't** add `Impl` suffix to interface implementations

**Do** Place `System` directives first when sorting usings

**Consider** Use the following order of members in a class:
-	constants
-	private fields
-	constructors
-	public properties
-	protected properties
-	public methods
-	protected methods
-	private methods
   
**Do** Use two empty lines to separate public, protected and private method blocks from each other.

**Do** Multi-line blocks of code should be separated with empty line from other code.

**Do** Put a call to `base` or `this` constructor on a separate line:

```
public MyClass(string argument):
    base(argument)
```

### Coding conventions	
**Consider** Check simple values in conditions first

**Noncompliant Code Example**
```
if (GetSomeValue() > 0 && isActive)
```

**Compliant Solution**
```
if (isActive && GetSomeValue() > 0)
```


**Don't** use Single(). Or if you do, handle exceptions

**Do** API methods with [ResponseType(typeof(void))] attribute should return

**Do** Return StatusCode(HttpStatusCode.NoContent), not Ok()

### Virto Commerce
**Do** Custom modules must use the same versions of NuGet packages as in platform or in VC modules.

**Do** Compare IDs and SKUs with EqualsInvariant()


## Templates
### Descirbe Custom rule name
**Do** describe custom rule name.

**Why?** gives reasons for following the previous recommendations.

**Noncompliant Code Example**
```
//// TODO: Noncompliant Code Example
```

**Compliant Solution**
```
//// TODO: Compliant Solution
```







