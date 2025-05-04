# Python Documentation Comments Specification
These guidelines apply to modules, classes, functions, methods, properties, and inline code blocks.

## Docstrings
Use triple double quotes (`"""`) immediately after a module, class, or function definition.

### Summary
- **Purpose:** Provide a brief description of the module, class, or function.
- **Example:**
  ```python
  """Calculates the sum of two integers."""
  ```

### Extended Description
- **Purpose:** Detail functionality, usage notes, or special considerations.
- **Example:**
  ```python
  """
  Calculates the sum of two integers.
  This function validates that both inputs are integers before adding.
  """
  ```

### Parameters (Args)
- **Purpose:** List each parameter with its type and description.
- **Format:**
  ```python
  Args:
      a (int): The first integer.
      b (int): The second integer.
  ```

### Return Value
- **Purpose:** Describe the return value and its type.
- **Format:**
  ```python
  Returns:
      int: The sum of the two integers.
  ```

### Exceptions (Raises)
- **Purpose:** Document any exceptions that may be raised.
- **Format:**
  ```python
  Raises:
      ValueError: If either input is not an integer.
  ```

### Example Usage
- **Purpose:** Provide code examples demonstrating how to use the function or class.
- **Format:**
  ```python
  Example:
      >>> add(5, 10)
      15
  ```

## Inline Comments
Use the `#` symbol for single-line or inline comments. Place these above or next to code lines to explain logic or steps.

- **Example:**
  ```python
  def add(a: int, b: int) -> int:
      # Validate inputs
      if not isinstance(a, int) or not isinstance(b, int):
          raise ValueError("Both parameters must be integers")
      
      # Return the computed sum
      return a + b
  ```

## Full Example
```python
def add(a: int, b: int) -> int:
    """
    Calculates the sum of two integers.

    This function adds two integer values after validating the inputs.
    
    Args:
        a (int): The first integer.
        b (int): The second integer.
    
    Returns:
        int: The sum of a and b.
    
    Raises:
        ValueError: If either a or b is not an integer.
    
    Example:
        >>> add(5, 10)
        15
    """
    # Validate that inputs are integers
    if not isinstance(a, int) or not isinstance(b, int):
        raise ValueError("Both parameters must be integers")
    
    # Return the computed sum
    return a + b
```