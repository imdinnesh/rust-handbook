# Common Collections

The values are stored in heap ,which means the amount of data does not need to be known at compile time and can grow or shrink as the program runs

- A vector allows you to store a variable number of values next to each other.

- A string is a collection of characters. We’ve mentioned the String type previously, but in this chapter, we’ll talk about it in depth.

- A hash map allows you to associate a value with a specific key. It’s a particular implementation of the more general data structure called a map.

### Vectors (Vec<T>)

**Creating a New Vector**

```rust
let v: Vec<i32> = Vec::new();
let v = vec![1, 2, 3]; // macro
```

**Updating a Vector**

```
let mut v = Vec::new();
v.push(5);
v.push(6);
v.push(7);
v.push(8);
```

**Reading Elements of Vectors**

```rust
let v = vec![1, 2, 3, 4, 5];

let third: &i32 = &v[2];
println!("The third element is {third}");

let third: Option<&i32> = v.get(2);
match third {
    Some(third) => println!("The third element is {third}"),
    None => println!("There is no third element."),
}
```

**Find the error**
```rust
let mut v = vec![1, 2, 3, 4, 5];

let first = &v[0];

v.push(6);

println!("The first element is: {first}");
```

```
This error is due to the way vectors work: Because vectors put the values next to each other in memory, adding a new element onto the end of the vector might require allocating new memory and copying the old elements to the new space, if there isn’t enough room to put all the elements next to each other where the vector is currently stored. In that case, the reference to the first element would be pointing to deallocated memory. The borrowing rules prevent programs from ending up in that situation.
```

**Iterating Over the Values in a Vector**

```rust
let v = vec![100, 32, 57];
for i in &v {
        println!("{i}");
}

let mut v = vec![100, 32, 57];
for i in &mut v {
    *i += 50;
}
```

**Dropping a Vector Drops Its Elements**

```rust
{
    let v = vec![1, 2, 3, 4];
    // do stuff with v
} // <- v goes out of scope and is freed here
```

### Storing UTF-8 Encoded Text with Strings

**Creating a New String**

```
let mut s = String::new();
```

```rust
let data = "initial contents";

let s = data.to_string();

// The method also works on a literal directly:
let s = "initial contents".to_string();
```

```rust
let s = String::from("initial contents");
```

**Appending with push_str or push**

```rust
let mut s1 = String::from("foo");
let s2 = "bar";
s1.push_str(s2);
println!("s2 is {s2}");
```














