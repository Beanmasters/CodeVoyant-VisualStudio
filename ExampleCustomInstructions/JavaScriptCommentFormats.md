## JavaScript Documentation Comments Specification
These guidelines should be applied to all functions, methods, classes, constructors, and object properties—even when they’re marked as public, private, or static.

### Documentation Block Comments
Documentation block comments begin with `/**` and end with `*/`. They should be placed immediately above the code element they document. This style is commonly used by tools such as JSDoc.

#### 1. @summary / @description  
**Purpose:**  
Provides a concise overview of what the function, class, or property does. Use this as the opening statement. Some documentation systems may use either `@summary` or `@description` (or just an opening sentence) for the brief explanation.

**Example:**
```js
/**
 * Calculates the sum of two numbers.
 */
```

#### 2. @description (Optional)  
**Purpose:**  
Expands on the summary with additional details about behavior, performance implications, or other special considerations.

**Example:**
```js
/**
 * Calculates the sum of two numbers.
 * @description This function takes two numeric parameters and returns their sum.
 */
```

#### 3. @param  
**Purpose:**  
Describes each parameter for functions or constructors. Use one `@param` tag per parameter, specifying the type, name, and a brief description.

**Syntax:**  
`@param {Type} parameterName - Description of the parameter.`

**Example:**
```js
/**
 * Adds two numbers together.
 * @param {number} a - The first number.
 * @param {number} b - The second number.
 */
function add(a, b) {
  return a + b;
}
```

#### 4. @returns / @return  
**Purpose:**  
Documents the return value of a function. Only include if the function returns a value.

**Syntax:**  
`@returns {Type} Description of the return value.`

**Example:**
```js
/**
 * Adds two numbers.
 * @param {number} a - The first number.
 * @param {number} b - The second number.
 * @returns {number} The sum of the two numbers.
 */
function add(a, b) {
  return a + b;
}
```

#### 5. @example  
**Purpose:**  
Provides code examples that demonstrate how to use the function, class, or property.

**Example:**
```js
/**
 * Calculates the sum of two numbers.
 * @param {number} a - The first number.
 * @param {number} b - The second number.
 * @returns {number} The resulting sum.
 * @example
 * // Returns 15
 * add(5, 10);
 */
function add(a, b) {
  return a + b;
}
```

#### 6. @throws  
**Purpose:**  
Documents any exceptions or errors that the function might throw.

**Syntax:**  
`@throws {ErrorType} Description of the error condition.`

**Example:**
```js
/**
 * Divides two numbers.
 * @param {number} numerator - The numerator.
 * @param {number} denominator - The denominator.
 * @returns {number} The quotient.
 * @throws {Error} Thrown when the denominator is zero.
 */
function divide(numerator, denominator) {
  if (denominator === 0) {
    throw new Error("Denominator cannot be zero.");
  }
  return numerator / denominator;
}
```

#### 7. @see  
**Purpose:**  
Creates a link or reference to another function, class, or documentation page that is related.

**Example:**
```js
/**
 * Calculates the sum of two numbers.
 * @see subtract
 */
```

#### 8. Access Modifiers: @private, @public, @protected  
**Purpose:**  
Indicates the intended access level of the documented element. While JavaScript does not enforce these modifiers natively, they help clarify usage.

**Example:**
```js
/**
 * @private
 * Multiplies two numbers.
 * @param {number} a - The first number.
 * @param {number} b - The second number.
 * @returns {number} The product of a and b.
 */
function multiply(a, b) {
  return a * b;
}
```

#### 9. @typedef and @property  
**Purpose:**  
Used to document custom object types. `@typedef` defines a new type and `@property` is used within that definition to describe its properties.

**Example:**
```js
/**
 * A point in 2D space.
 * @typedef {Object} Point
 * @property {number} x - The x-coordinate.
 * @property {number} y - The y-coordinate.
 */
```

### Inline Comments in Executable Code Blocks
Inline comments begin with `//` and are used within code blocks to explain complex logic, clarify intent, or note important information. They should be used sparingly and kept concise.

**Example:**
```js
function add(a, b) {
  // Validate that both parameters are numbers
  if (typeof a !== 'number' || typeof b !== 'number') {
    throw new Error('Both parameters must be numbers.');
  }
  
  // Return the sum of a and b
  return a + b;
}
```

## Complete Example
Here’s a complete example showing a function documented with all the key elements:

```js
/**
 * Calculates the sum of two numbers.
 *
 * @summary Performs addition of two numeric values.
 * @description This function takes two numbers and returns their sum.
 *              It validates the input to ensure both parameters are numbers.
 * @param {number} a - The first number to add.
 * @param {number} b - The second number to add.
 * @returns {number} The sum of a and b.
 * @throws {Error} Thrown when either a or b is not a number.
 * @example
 * // Returns 15
 * add(5, 10);
 */
function add(a, b) {
  // Validate input parameters
  if (typeof a !== 'number' || typeof b !== 'number') {
    throw new Error('Both parameters must be numbers.');
  }
  
  // Calculate and return the sum
  return a + b;
}
```