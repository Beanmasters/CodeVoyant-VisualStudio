# C++ Documentation Comments Specification
These comment styles apply to all public, protected, private, and static members, functions, methods, and classes. The preferred style follows Doxygen conventions.

## Programming Construct Header Comments
Documentation comments can begin with `///` (triple-slash) or with a block comment style using `/** ... */` and are placed immediately above classes, constructors, methods, functions, variables, enums, or other code elements.

1. **@brief**  
   Provides a short description of the member’s purpose.  
   ```cpp
   /// @brief Brief description of the class, function, or variable.
   ```
   
2. **@details**  
   Offers additional details on behavior, usage, or special considerations beyond the brief summary.  
   ```cpp
   /// @details This function implements a complex algorithm with multiple steps.
   ```

3. **@param**  
   Describes each parameter for functions or methods. Use one `@param` tag per parameter, specifying its name.  
   ```cpp
   /// @param a The first integer parameter.
   /// @param b The second integer parameter.
   ```

4. **@return**  
   Describes the return value of a function. Only applicable to functions with non-void return types.  
   ```cpp
   /// @return The sum of a and b.
   ```

5. **@example**  
   Provides example code demonstrating the usage of the function or class.  
   ```cpp
   /// @example
   /// @code
   /// int result = Add(5, 10);
   /// std::cout << result;
   /// @endcode
   ```

6. **@throws**  
   Documents any exceptions that the function might throw.  
   ```cpp
   /// @throws std::invalid_argument Thrown if either parameter is negative.
   ```

7. **@see**  
   Creates a reference link to another member or function for additional context.  
   ```cpp
   /// @see AdvancedCalculator
   ```

8. **@tparam**  
   Describes a template type parameter for template classes or functions.  
   ```cpp
   /// @tparam T The type used for the collection elements.
   ```

## Executable Code Block Comments
Inline comments use `//` for single-line comments and `/* ... */` for block comments. These should be placed immediately above an executable code block or at the end of a code line to explain logic or variable usage.

```cpp
int Add(int a, int b)
{
    int quarter_start = ((std::chrono::system_clock::to_time_t(std::chrono::system_clock::now()) % 12) / 3) * 3 + 1; // Determine start month for the quarter

    // Check that both parameters are non-negative
    if (a < 0 || b < 0)
    {
        throw std::invalid_argument("Parameters must be non-negative");
    }
    
    // Return the sum of the parameters
    return a + b;
}
```

## Full Example
```cpp
/// @brief Calculates the sum of two integers.
/// @details This function performs a simple addition. It checks that both parameters are non-negative
/// before performing the operation. For more advanced arithmetic, refer to @see AdvancedCalculator.
/// @param a The first integer to add.
/// @param b The second integer to add.
/// @return The sum of a and b.
/// @throws std::invalid_argument Thrown when either a or b is negative.
/// @example
/// @code
/// int result = Add(5, 10);
/// std::cout << result; // Output: 15
/// @endcode
int Add(int a, int b)
{
    // Validate that a and b are non-negative
    if (a < 0 || b < 0)
    {
        throw std::invalid_argument("Parameters must be non-negative");
    }
    
    // Calculate and return the sum
    return a + b;
}
```