# F# Documentation Comments Specification
F# supports XML documentation comments similar to C#, and these styles should be applied to all public, private, internal, and module-level declarations, including functions, methods, properties, types, and modules.

---

## Programming Construct Header Comments
F# documentation comments begin with triple slashes (`///`) and are placed immediately above modules, types, let-bound functions, methods, properties, and other declarations. They provide metadata that can be extracted by documentation tools such as F# Formatting or Visual Studio’s IntelliSense.

Before using documentation comments (e.g. `///`), verify that the code fragment is a complete function, method, or type declaration. For non-declaration comments inside executable code, use inline comments as described below.

### 1. `<summary>`
Describes the purpose or functionality of the member. It is typically the first tag in a documentation comment.
```fsharp
/// <summary>
/// Provides a brief overview of the function or type.
/// </summary>
```

### 2. `<remarks>`
Offers additional details about the member’s behavior, usage, or any special considerations. This tag is used for more in-depth explanation than `<summary>`.
```fsharp
/// <remarks>
/// This function uses recursion to calculate the factorial of a number.
/// Consider using tail recursion for very large inputs.
/// </remarks>
```

### 3. `<param>`
Documents each parameter for functions or methods. Use one `<param>` tag per parameter and specify the parameter’s name using the name attribute.
```fsharp
/// <param name="x">The first integer for the calculation.</param>
/// <param name="y">The second integer for the calculation.</param>
```

### 4. `<returns>`
Describes the return value of a function. This tag is applicable for functions that produce a result.
```fsharp
/// <returns>The sum of the two integers.</returns>
```

### 5. `<value>`
Used with properties to describe what the property represents. This is similar to `<returns>` but is intended for property documentation.
```fsharp
/// <value>
/// Gets or sets the name of the product.
/// </value>
```

### 6. `<example>`
Provides code examples demonstrating how to use the function or type. This tag is especially useful when included within `<remarks>`.
```fsharp
/// <example>
/// <code>
/// let result = add 5 10
/// printfn "%d" result  // Output: 15
/// </code>
/// </example>
```

### 7. `<exception>`
Documents any exceptions that a function or method might raise. Use the cref attribute to specify the exception type.
```fsharp
/// <exception cref="System.ArgumentException">
/// Thrown when an invalid argument is passed.
/// </exception>
```

### 8. `<see>`
Creates a link to another member within the documentation. This is useful for referencing related functions, types, or modules.
```fsharp
/// <see cref="AdvancedCalculator"/>
```

You can also use `<seealso>` to add references to related content in a separate section if needed.

### 9. `<paramref>`
Refers to a parameter by name within the comments, often used in `<remarks>` or `<returns>` to improve clarity.
```fsharp
/// <returns>The sum of <paramref name="x"/> and <paramref name="y"/>.</returns>
```

### 10. `<typeparam>`
Describes a generic type parameter for generic types or functions.
```fsharp
/// <typeparam name="T">The type of elements in the collection.</typeparam>
```

---

## Executable Code Block Comments
For comments within executable code, F# uses single-line comments with `//` and block comments using `(* ... *)`.

### Single-Line Comments
Placed immediately above or on the same line as a code statement.
```fsharp
let result = add 5 10 // Calculate the sum of 5 and 10
```

### Block Comments
Used for longer explanations or temporarily disabling code.
```fsharp
(* 
   This block comment provides detailed insight
   into the logic behind the recursive algorithm.
*)
let rec factorial n =
    if n <= 1 then 1
    else n * factorial (n - 1)
```

---

## Full Example
Below is a complete example that shows how these documentation and inline comments can be used together in an F# function.

```fsharp
/// <summary>
/// Calculates the sum of two integers.
/// </summary>
/// <remarks>
/// This function performs a simple addition operation. For more advanced arithmetic,
/// see <see cref="AdvancedCalculator"/>.
/// </remarks>
/// <param name="a">The first integer to add.</param>
/// <param name="b">The second integer to add.</param>
/// <returns>The sum of <paramref name="a"/> and <paramref name="b"/>.</returns>
/// <exception cref="System.ArgumentException">
/// Thrown when either <paramref name="a"/> or <paramref name="b"/> is negative.
/// </exception>
/// <example>
/// <code>
/// let result = add 5 10
/// printfn "%d" result  // Output: 15
/// </code>
/// </example>
let add a b =
    // Check that both numbers are non-negative
    if a < 0 || b < 0 then
        invalidArg "a or b" "Both numbers must be non-negative"
    // Return the sum of a and b
    a + b
```