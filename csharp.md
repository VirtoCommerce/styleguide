# C# Coding Conventions
We created this style guide to keep the code in Virto Commerce consistent.

The goal is to help library designers ensure API consistency and ease of use by providing a unified programming model that is independent of the programming language used for development.

These guidelines are based on C# and Microsoft conventions.

We recommend that you follow these design guidelines when developing classes and components that extend the .NET Framework. Inconsistent library design adversely affects developer productivity and discourages adoption.

<details>
    <summary><b>These guidelines are organized as simple recommendations prefixed with the terms</b></summary>

**Do** is one that should always be followed. Always might be a bit too strong of a word. Guidelines that literally should always be followed are extremely rare. On the other hand, you need a really unusual case for breaking a Do guideline.

**Consider** guidelines should generally be followed. If you fully understand the meaning behind the guideline and have a good reason to deviate, then do so. Please strive to be consistent.

**Avoid** indicates something you should almost never do. Code examples to avoid have an unmistakable red header.

**Do not** Just don't do it.

**Why?** gives reasons for following the previous recommendations.
</details>

**Note:** A guideline is flexible and can be adjusted and improved.

## Fix Issues Before They Exist
This is a set of tools and extension that helps you to detect and fix quality issues as you write your code.
You must use these tools and fix the errors before commit to repository.

<details>
    <summary><b>Use PowerCommands For Visual Studio</b></summary>

[Install Productivity Power Tools](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.PowerCommandsforVisualStudio)

Go to “Tools > Options > Productivity Power Tools > PowerCommands” and Enable “Format documents on save” and “Remove and Sort Usings on save”.
</details>

<details>
    <summary><b>Use SonarLint and SonarQube</b></summary>

[SonarLint](https://www.sonarlint.org/) is an IDE extension that helps you detect and fix quality issues as you write code.
Like a spell checker, SonarLint squiggles flaws so that they can be fixed before committing code.

[Install SonarLint in Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)

[List of C# rules](https://rules.sonarsource.com/csharp)
</details>

<details>
    <summary><b>Use Visual Studio Code Analysis</b></summary>

We recommend to use the Microsoft Rules rule set to focus on the most critical problems in your code, including potential security holes, application crashes, and other important logic and design errors.

Go to "Visual Studio > Analyze > Run Code Analysis > On Solution".

[List of rules](https://docs.microsoft.com/en-us/visualstudio/code-quality/all-rules-rule-set?view=vs-2017)
</details>

## C# CODING CONVENTIONS - BASIC RECOMMENDATIONS
Read [Coding Conventions](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)

## C# FRAMEWORK DESIGN GUIDELINES
Read [Design Guidelines](https://docs.microsoft.com/en-us/dotnet/standard/design-guidelines/)

These guidelines are excerpted from the book FRAMEWORK DESIGN GUIDELINES: CONVENTIONS, IDIOMS, AND PATTERNS FOR REUSABLE .NET LIBRARIES, 2ND EDITION, by Krzysztof Cwalina and Brad Abrams.

## VIRTO COMMERCE C# CODING CONVENTIONS

### Naming
Naming conventions are hugely important for maintainability and readability. This guide recommends naming conventions for the file names and the symbol names.

<details>
    <summary><b>Names should be clear and meaningful</b></summary>

1. Names should be clear and meaningful.
1. Good names replace comments in most cases.
1. Good names allow to read the code like a book.

**Bad**

```csharp
var dataFromDb = db.GetData();
```

**Good**

```csharp
var employees = employeeService.GetEmployees();
```
</details>

<details>
    <summary><b>Use full words instead of shortened ones</b></summary>

**Do** Use full words instead of shortened one.

**Bad**

```csharp
var empl = ...
var val = ...
var resp = ...
```

**Good**

```csharp
var employees = ...
var value = ...
var response = ...
```
</details>

<details>
    <summary><b>Names of private fields and constants should start with `_` and lowercase letter</b></summary>

**Do** Names of private fields and constants should start with `_` and lowercase letter.
This is the only case when `_` should be used in names.

**Bad**

```csharp
private const int Batch_Size;
private char[] delimiters = { ',', ';' };
```

**Good**

```csharp
private const int _batchSize;
private char[] _delimiters = { ',', ';' };
```
</details>

<details>
    <summary><b>Don't add `Impl` suffix to interface implementations</b></summary>

**Don't** add `Impl` suffix to interface implementations.

**Bad**

```csharp
public class CatalogServiceImpl: ICatalogService
```

**Good**

```csharp
public class CatalogService: ICatalogService
```
</details>

<details>
    <summary><b>Use `result` instead of `retVal`</b></summary>

**Do** Use `result` instead of `retVal`.

**Bad**

```csharp
var retVal = ...;
```

**Good**

```csharp
var result = ...;
```
</details>

<details>
    <summary><b>Use C# keywords instead of classes</b></summary>

**Do** Use C# keywords instead of classes:

**Bad**

```csharp
String fullName = ...;
Int32 counter = ...;
```

**Good**

```csharp
string fullName = ...;
int counter = ...;
```
</details>

### Coding conventions

<details>
    <summary><b>Don't use regions, especially in small files</b></summary>

**Don't** use regions (#region), especially in small files.

**Why?** You have to expand each region before reading the code.
</details>

<details>
    <summary><b>Combine class properties in logical groups</b></summary>

**Consider** Combine class properties in logical groups.
</details>

<details>
    <summary><b>Initialize properties in the same order as they are declared in the class</b></summary>

**Do** Initialize properties in the same order as they are declared in the class.
</details>

<details>
    <summary><b>Simplify complex conditions and expressions</b></summary>

**Do** Simplify complex conditions and expressions by creating intermediate variables with clear and meaningful names.
</details>

<details>
    <summary><b>Check simple values in conditions first</b></summary>

**Consider** Check simple values in conditions first.

**Bad**

```csharp
if (GetSomeValue() > 0 && isActive)
```

**Good**

```csharp
if (isActive && GetSomeValue() > 0)
```
</details>

<details>
    <summary><b>Split complex methods into multiple short methods with clear and meaningful names</b></summary>

**Do** Split complex methods into multiple short methods with clear and meaningful names.
</details>

<details>
    <summary><b>Place calling method before the one being called</b></summary>

**Do** If one method calls another, place calling method before the one being called.
</details>

<details>
<summary><b>Each method should have only one return at the end</b></summary>

**Do** Each method should have only one return at the end.

**Bad**

```csharp
if(!isActive)
    return null;
...
return ...;
```

**Good**

```csharp
var result = null;
if(isActive)
{
    ...
    result = ...;
}
return result;
```
</details>

<details>
    <summary><b>Avoid calling .ToList() or .ToArray() when you really need IEnumerable</b></summary>

**Don't** Call `.ToList()` or `.ToArray()` when you really need IEnumerable.
</details>

<details>
    <summary><b>Don't use Single()</b></summary>

**Don't** use `Single()`. Or if you do, handle exceptions

**Bad**

```csharp
var employee = _employeeService.GetEmployees().Single();
```

**Good**

```csharp
var employee = _employeeService.GetEmployees().FirstOrDefault();
```
</details>

<details>
    <summary><b>Don't make API calls in a loop</b></summary>

**Don't** make API calls in a loop.
</details>

<details>
    <summary><b>Use kebab notation for API URLs</b></summary>

**Do** Use kebab notation for API URLs.

**Bad**

```
fulfillmentCenters
```

**Good**

```
fulfillment-centers
```
</details>

<details>
    <summary><b>API methods with [ResponseType(typeof(void))] attribute should return HttpStatusCode.NoContent</b></summary>

**Do** Return StatusCode(HttpStatusCode.NoContent), not Ok()
</details>

### Formatting
<details>
    <summary><b>Your text editor must support .editorconfig</b></summary>

**Do** Your text editor must support .editorconfig.
</details>

<details>
    <summary><b>Automatically format documents when saving</b></summary>

**Do** Automatically format documents when saving:

1. Install PowerCommandsforVisualStudio
1. Go to Tools > Options > Productivity Power Tools > PowerCommands
1. Enable Format documents on save and Remove and Sort Usings on save
</details>

<details>
    <summary><b>Place `System` directives first when sorting usings</b></summary>

**Do** Place `System` directives first when sorting usings

**Bad**

```csharp
using Nest;
using VirtoCommerce.Domain.Search
using System.Globalization;
```

**Good**

```csharp
using System.Globalization;
using Nest;
using VirtoCommerce.Domain.Search
```
</details>

<details>
    <summary><b>Whitespaces at the end of the line are not allowed</b></summary>

**Don't** Whitespaces at the end of the line are not allowed.
</details>

<details>
    <summary><b>Use the following order of members in a class</b></summary>

**Consider** Use the following order of members in a class:

1. constants
1. private fields
1. constructors
1. public properties
1. protected properties
1. public methods
1. protected methods
1. private methods
</details>

<details>
    <summary><b>Use two empty lines to separate public, protected and private method blocks from each other</b></summary>

**Do** Use two empty lines to separate public, protected and private method blocks from each other.
</details>

<details>
    <summary><b>Bodies of if, for, etc. should be enclosed in braces</b></summary>

**Do** Bodies of `if`, `for`, etc. should be enclosed in braces.
</details>

<details>
	<summary><b>Multi-line blocks of code should be separated with empty line from other code</b></summary>

**Do** Multi-line blocks of code should be separated with empty line from other code.
</details>

<details>
    <summary><b>Separate `return` at the end of the method with empty line from other code</b></summary>

**Do** Separate return at the end of the method with empty line from other code.
</details>

<details>
    <summary><b>Don't put condition and action on one line</b></summary>

**Don't** put condition and action on one line.
</details>

<details>
    <summary><b>Avoid breaking the line if it does not exceed 170 characters</b></summary>

**Avoid** breaking the line if it does not exceed 170 characters.
</details>

<details>
    <summary><b>Break complex (hard to read) LINQ expressions into multiple lines</b></summary>

**Do** Break complex (hard to read) LINQ expressions into multiple lines

**Good**

```csharp
var names = repository.Items
    .Where(x => x.IsActive && ids.Contains(x.Id)
    .Select(x => x.Name)
    .ToArray();
```
</details>

<details>
    <summary><b>Put `where` on a separate line</b></summary>

**Do** Put `where` on a separate line

**Good**
```csharp
public void Parse<T>(string input)
    where T: new()
```
</details>

<details>
    <summary><b>Put a call to `base` or `this` constructor on a separate line</b></summary>

**Do** Put a call to `base` or `this` constructor on a separate line

**Good**

```csharp
public MyClass(string argument)
    : base(argument)
{
...
}
```
</details>

<details>
    <summary><b>Don't nest multiple using (...), put them on the same level:</b></summary>

**Don't** nest multiple using (...), put them on the same level:

**Good**

```csharp
using(var disposable1 = ...)
using(var disposable2 = ...)
{
    ...
}
```
</details>

<details>
    <summary><b>Add `,` at the end of the line in object initializers</b></summary>

**Do** Add `,` at the end of the line in object initializers.

**Why?** This will reduce the number of modified lines in the next pull request.

**Good**

```csharp
var criteria = new SearchCriteria
{
    Skip = 0,
    Take = 10,
};
```
</details>

<details>
    <summary><b>Don't add `SubType Designer`. Use VS 2019, where this bug is fixed</b></summary>

**Don't** add `<SubType>Designer</SubType>`. Use VS 2019, where this bug is fixed.
</details>

### Testing

<details>
    <summary><b>Use Assert.Equal</b></summary>

**Do** Use `Assert.Equal(expected, actual)` instead of `Assert.True(actual == expected)`.
</details>

### Virto Commerce
<details>
    <summary><b>Custom modules must use the same versions of NuGet packages as in platform or in VC modules</b></summary>

**Do** Custom modules must use the same versions of NuGet packages as in platform or in VC modules.
</details>

<details>
    <summary><b>module.manifest should contain the same dependencies as packages.config</b></summary>

**Do** module.manifest should contain the same dependencies as packages.config.
</details>

<details>
    <summary><b>Web.config and app.config in modules should contain only the assemblyBinding section</b></summary>

**Do** Web.config and app.config in modules should contain only the assemblyBinding section
</details>

<details>
    <summary><b>`bin` directroy of the module.zip should not contain files that exist in platform or in dependencies</b></summary>

**Do** `bin` directroy of the module.zip should not contain files that exist in platform or in dependencies. Use `module.ignore` to exclude them from the ZIP.
</details>

<details>
    <summary><b>All API actions should have [CheckPermission] attribute</b></summary>

**Do** All API actions should have `[CheckPermission]` attribute.

**Good**

```csharp
[CheckPermission(Permission = ThumbnailPredefinedPermissions.Create)]
public IHttpActionResult Create(ThumbnailOption option)
{
    _thumbnailOptionService.SaveOrUpdate(new[] { option });
    return Ok(option);
}
```
</details>

<details>
    <summary><b>Compare IDs and SKUs with `EqualsInvariant()`</b></summary>

**Do** Compare IDs and SKUs with `EqualsInvariant()`.

</details>

<details>
    <summary><b>Don't call `repository.GetByIds(ids)` if `ids` is empty</b></summary>

**Don't** call `repository.GetByIds(ids)` if `ids` is empty.
</details>

## Templates
<details>
    <summary><b>Short description</b></summary>

**Do** Long description

**Bad**

```csharp
// Bad code example
```

**Good**

```csharp
// Good code example
```
</details>
