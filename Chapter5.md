# Chapter 5: Understanding Structs

### Defining and Instantiating Structs

A struct, or structure, is a custom data type that lets you package together and name multiple related values that make up a meaningful group.

If you’re familiar with an object-oriented language, a struct is like an object’s data attributes. 

```rust
struct User {
    active: bool,
    username: String,
    email: String,
    sign_in_count: u64,
}

fn main() {
    let user1 = User {
        email: String::from("someone@example.com"),
        username: String::from("someusername123"),
        active: true,
        sign_in_count: 1,
    };
}
```

```rust
fn main() {
    // --snip--

    let user2 = User {
        email: String::from("another@example.com"),
        ..user1
    };
}
```

### Creating Different Types with Tuple Structs

Tuple structs have the added meaning the struct name provides but don’t have names associated with their fields;

rather, they just have the types of the fields. 

```rust
struct Color(i32, i32, i32);
struct Point(i32, i32, i32);

fn main() {
    let black = Color(0, 0, 0);
    let origin = Point(0, 0, 0);
}
```

### Ownership of Struct Data

In the User struct definition,we used the owned String type rather than the &str string slice type. 

This is a deliberate choice because we want each instance of this struct to own all of its data and for that data to be valid for as long as the entire struct is valid.

It’s also possible for structs to store references to data owned by something else, but to do so requires the use of lifetimes. 

Lifetimes ensure that the data referenced by a struct is valid for as long as the struct is.


### Refactoring using Structs

Main Code

```rust
fn main() {
    let width1 = 30;
    let height1 = 50;

    println!(
        "The area of the rectangle is {} square pixels.",
        area(width1, height1)
    );
}

fn area(width: u32, height: u32) -> u32 {
    width * height
}
```

Refactoring with Tuples

```rust
fn main() {
    let rect1 = (30, 50);

    println!(
        "The area of the rectangle is {} square pixels.",
        area(rect1)
    );
}

fn area(dimensions: (u32, u32)) -> u32 {
    dimensions.0 * dimensions.1
}
```


Refactoring with Structs

```rust
struct Rectangle {
    width: u32,
    height: u32,
}

fn main() {
    let rect1 = Rectangle {
        width: 30,
        height: 50,
    };

    println!(
        "The area of the rectangle is {} square pixels.",
        area(&rect1)
    );
}

fn area(rectangle: &Rectangle) -> u32 {
    rectangle.width * rectangle.height
}
```

### Methods

Methods are functions that are defined within the context of a struct or an enum or a trait object.

Their first parameter is always self, which represents the instance of the struct the method is being called on.

```rust
struct Rectangle {
    width: u32,
    height: u32,
}

impl Rectangle {
    fn area(&self) -> u32 {
        self.width * self.height
    }
}

fn main() {
    let rect1 = Rectangle {
        width: 30,
        height: 50,
    };

    println!(
        "The area of the rectangle is {} square pixels.",
        rect1.area()
    );
}
```


Dot and -> Operator from C/C ++ World

Dot (.) operator is used to call the methods directly on the object

-> operator is used to call the methods on the reference of the object

```cpp
// Similar things
object->something()
(*object).something().
```

### Associated Functions

All functions defined within an impl block are called associated functions because they’re associated with the type named after the impl. 

Unlike methods, associated functions don’t take self as a parameter. 

Associated functions that aren’t methods are often used for constructors that will return a new instance of the struct. 

These are often called new, but new isn’t a special name and isn’t built into the language

```rust
impl Rectangle {
    fn square(size: u32) -> Self {
        Self {
            width: size,
            height: size,
        }
    }
}
```









