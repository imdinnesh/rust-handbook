# Chapter 3: Common Programming Concepts

### Variables and Mutability

- By default the variables are immutable

```rust
fn main() {
    let x = 5;
    println!("The value of x is: {x}");
    x = 6;
    println!("The value of x is: {x}");
    // cannot assign twice to immutable variable
}
```

Adding mutability

```rust
fn main() {
    let mut x = 5;
    println!("The value of x is: {x}");
    x = 6;
    println!("The value of x is: {x}");
}
```

Declaring Constants

Like immutable variables, constants are values that are bound to a name and are not allowed to change, but there are a few differences between constants and variables.

- mut is not allowed incase of constants 
- const is used instead of let
- constants can be declared in any scope, including the global scope

```rust
const THREE_HOURS_IN_SECONDS: u32 = 60 * 60 * 3;
```

Shadowing

- you can declare a new variable with the same name as a previous variable.

```rust
fn main() {
    let x = 5;

    let x = x + 1;

    {
        let x = x * 2;
        println!("The value of x in the inner scope is: {x}");
    }

    println!("The value of x is: {x}");
}
```

### Data Types

Rust has 4 scalar data types (Single Value)
- Bool 
- Char 
- Integers 
- Floating point numbers

Compound Data Types (Hold Multiple Values in one type)

- Tuples

    A tuple is a general way of grouping together a number of values with a variety of types into one compound type.

    Tuples have a fixed length: Once declared, they cannot grow or shrink in size.

    ```rust
    fn main() {
        let tup: (i32, f64, u8) = (500, 6.4, 1);
    }
    ```

    Use either dot (.) operator or destructuring to extract the individual values 

- Arrays

    Every element of an array must have the same type. 

    Unlike arrays in some other languages, arrays in Rust have a fixed length.

    ```rust
    fn main() {
    let a = [1, 2, 3, 4, 5];
    }
    ```

















