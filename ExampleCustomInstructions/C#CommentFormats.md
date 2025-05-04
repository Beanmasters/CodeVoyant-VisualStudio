# C# Documentation Comments Specification
These comment styles should be applied to all public, protected, private and static members, methods, functions and classes.

## Programming Construct Header Comments
Begin with "///" and are placed immediately above classes, constructors, methods, properties, fields, enums, or other code elements.
Verify the provided code fragment is a complete function, method, or class before using Programming Construct Header comments (e.g., ///), otherwise use inline Executable Code Block comments (e.g. //).

1. <summary>
Describes the purpose or functionality of the member. It's typically the first tag in a documentation comment.
```csharp
/// <summary>
/// Provides a brief summary of the class, method, or property.
/// </summary>
```
2. <remarks>
Provides additional details about the member’s behavior, usage, or any special considerations. This section is for more in-depth explanations than <summary>.
```csharp
/// <remarks>
/// This method performs a complex calculation using multiple steps.
/// Use it only when necessary due to its high performance cost.
/// </remarks>
```
3. <param>
Describes each parameter for methods or constructors. Use one <param> tag per parameter, specifying the parameter’s name with the name attribute.
```csharp
/// <param name="a">The first integer for the operation.</param>
/// <param name="b">The second integer for the operation.</param>
```
4. <returns>
Describes the return value of a method. Only applicable for methods that return a value (non-void methods).
```csharp
/// <returns>The result of adding the two integers.</returns>
```
5. <value>
Used with properties to describe what the property represents. It’s similar to <returns> but specifically for properties.
```csharp
/// <value>
/// Gets or sets the name of the product.
/// </value>
```
6. <example>
Provides code examples demonstrating how to use the class or method. Commonly used within <remarks>.
```csharp
/// <example>
/// <code>
/// var result = calculator.Add(5, 10);
/// Console.WriteLine(result);
/// </code>
/// </example>
```
7. <exception>
Documents exceptions that a method might throw. Use the cref attribute to specify the exception type.
```csharp
/// <exception cref="System.ArgumentNullException">
/// Thrown when a required argument is null.
/// </exception>
```
8. <see>
Creates a link to another member within the documentation. Useful for references to related methods, classes, or properties. Use the cref attribute to specify the reference.
```csharp
/// <see cref="SomeRelatedMethod"/>
```
You can also use <seealso> to add references to related content in a separate section.
9. <paramref>
Refers to a parameter by name within the comments to improve readability, often used in <remarks> or <returns> sections.
```csharp
/// <returns>The result of adding <paramref name="a"/> and <paramref name="b"/>.</returns>
```
10. <typeparam>
Describes a generic type parameter for generic classes or methods.
```csharp
/// <typeparam name="T">The type of elements in the collection.</typeparam>
Example: Complete Documentation Comment
```

## Executable Code Block Comments
Begin with // and are placed immediately above an executable code block or at the end of a code line.  These comments are sentence fragments and do not end with periods.

```chsarp
public int Add(int a, int b)
{
	int startMonth = ((DateTime.Today.Month - 1) / 3 * 3) + 1; // Start months: Jan(1), Apr(4), Jul(7), Oct(10).

	// Verify a or b is greater than zero
    if (a < 0 || b < 0)
        throw new ArgumentOutOfRangeException();
    
	Logger.InfoFormat($"{startMonth}: {a} + {b}");
	
	// Return the sum
    return a + b;
}
```

## Full Example
Here’s a full example showing how these are used together:

```csharp
/// <summary>
/// Calculates the sum of two integers.
/// </summary>
/// <remarks>
/// This method performs a simple addition operation. Use it when you need a quick calculation
/// with minimal overhead. For more complex calculations, see <see cref="AdvancedCalculator"/>.
/// </remarks>
/// <param name="a">The first integer to add.</param>
/// <param name="b">The second integer to add.</param>
/// <returns>The sum of <paramref name="a"/> and <paramref name="b"/>.</returns>
/// <exception cref="System.ArgumentOutOfRangeException">
/// Thrown when either parameter is out of the allowable range.
/// </exception>
/// <example>
/// <code>
/// var result = calculator.Add(5, 10);
/// Console.WriteLine(result); // Output: 15
/// </code>
/// </example>
private int Add(int a, int b)
{
	// Verify a or b is greater than zero
    if (a < 0 || b < 0)
        throw new ArgumentOutOfRangeException();
    
	// Return the sum
    return a + b;
}
```