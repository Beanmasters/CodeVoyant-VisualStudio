# Visual Basic Documentation Comments Specification
These comment styles should be applied to all public, protected, private, and shared members, functions, methods, and classes.

## Programming Construct Header Comments
Visual Basic XML documentation comments begin with three apostrophes (''' ) and are placed immediately above classes, constructors, functions, methods, properties, fields, enumerations, or other code elements.  
Before applying header comments (e.g., '''), verify that the provided code fragment represents a complete function, method, or class. For incomplete or inline code, use executable code block comments (single apostrophe).

1. **`<summary>`**  
   Describes the purpose or functionality of the member. It is typically the first tag in a documentation comment.
   ```vb
   ''' <summary>
   ''' Provides a brief summary of the class, function, or property.
   ''' </summary>
   ```

2. **`<remarks>`**  
   Provides additional details about the member’s behavior, usage, or any special considerations. This section allows for more in-depth explanations than `<summary>`.
   ```vb
   ''' <remarks>
   ''' This function performs a complex calculation using multiple steps.
   ''' Use it only when necessary due to its high performance cost.
   ''' </remarks>
   ```

3. **`<param>`**  
   Describes each parameter for functions or constructors. Use one `<param>` tag per parameter and specify the parameter’s name with the `name` attribute.
   ```vb
   ''' <param name="a">The first integer for the operation.</param>
   ''' <param name="b">The second integer for the operation.</param>
   ```

4. **`<returns>`**  
   Describes the return value of a function. This tag is only applicable for functions that return a value.
   ```vb
   ''' <returns>The result of adding the two integers.</returns>
   ```

5. **`<value>`**  
   Used with properties to describe what the property represents. It is similar to `<returns>`, but specifically for properties.
   ```vb
   ''' <value>
   ''' Gets or sets the name of the product.
   ''' </value>
   ```

6. **`<example>`**  
   Provides code examples demonstrating how to use the class or function. It is often included within `<remarks>`.
   ```vb
   ''' <example>
   ''' <code>
   ''' Dim result As Integer = Calculator.Add(5, 10)
   ''' Console.WriteLine(result)
   ''' </code>
   ''' </example>
   ```

7. **`<exception>`**  
   Documents exceptions that a function might throw. Use the `cref` attribute to specify the exception type.
   ```vb
   ''' <exception cref="System.ArgumentNullException">
   ''' Thrown when a required argument is null.
   ''' </exception>
   ```

8. **`<see>`**  
   Creates a link to another member within the documentation. This is useful for referencing related functions, classes, or properties. Use the `cref` attribute to specify the reference.
   ```vb
   ''' <see cref="SomeRelatedMethod"/>
   ```
   You may also use `<seealso>` to add references to related content in a separate section.

9. **`<paramref>`**  
   Refers to a parameter by name within the comments to improve readability, often used in `<remarks>` or `<returns>` sections.
   ```vb
   ''' <returns>The result of adding <paramref name="a"/> and <paramref name="b"/>.</returns>
   ```

10. **`<typeparam>`**  
    Describes a generic type parameter for generic classes or functions.
    ```vb
    ''' <typeparam name="T">The type of elements in the collection.</typeparam>
    ```

## Executable Code Block Comments
Executable code block comments in Visual Basic begin with a single apostrophe (') and are placed immediately above an executable code block or at the end of a code line.

```vb
Public Function Add(ByVal a As Integer, ByVal b As Integer) As Integer
    Dim startMonth As Integer = ((DateTime.Today.Month - 1) \ 3 * 3) + 1 ' Start months: Jan(1), Apr(4), Jul(7), Oct(10).

    ' Verify a or b is greater than zero
    If a < 0 OrElse b < 0 Then
        Throw New ArgumentOutOfRangeException()
    End If

    Logger.InfoFormat($"{startMonth}: {a} + {b}")

    ' Return the sum
    Return a + b
End Function
```

## Full Example
Here’s a full example showing how the documentation comments are used together:

```vb
''' <summary>
''' Calculates the sum of two integers.
''' </summary>
''' <remarks>
''' This function performs a simple addition operation. Use it when you need a quick calculation
''' with minimal overhead. For more complex calculations, see <see cref="AdvancedCalculator"/>.
''' </remarks>
''' <param name="a">The first integer to add.</param>
''' <param name="b">The second integer to add.</param>
''' <returns>The sum of <paramref name="a"/> and <paramref name="b"/>.</returns>
''' <exception cref="System.ArgumentOutOfRangeException">
''' Thrown when either parameter is out of the allowable range.
''' </exception>
''' <example>
''' <code>
''' Dim result As Integer = Calculator.Add(5, 10)
''' Console.WriteLine(result) ' Output: 15
''' </code>
''' </example>
Private Function Add(ByVal a As Integer, ByVal b As Integer) As Integer
    ' Verify a or b is greater than zero
    If a < 0 OrElse b < 0 Then
        Throw New ArgumentOutOfRangeException()
    End If

    ' Return the sum
    Return a + b
End Function
```