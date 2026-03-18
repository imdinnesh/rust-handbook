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

# Hash Maps (HashMap<K, V>)

The type HashMap<K, V> stores a mapping of keys of type K to values of type V using a hashing function, which determines how it places these keys and values into memory. 

Many programming languages support this kind of data structure, but they often use a different name, such as hash, map, object, hash table, dictionary, or associative array, just to name a few.

### Creating a New Hash Map

```rust
use std::collections::HashMap;

let mut scores = HashMap::new();

scores.insert(String::from("Blue"), 10);
scores.insert(String::from("Yellow"), 50);
```

### Accessing Values in a Hash Map

```rust
use std::collections::HashMap;

let mut scores = HashMap::new();

scores.insert(String::from("Blue"), 10);
scores.insert(String::from("Yellow"), 50);

let team_name = String::from("Blue");
let score = scores.get(&team_name).copied().unwrap_or(0);
```

```rust
use std::collections::HashMap;

let mut scores = HashMap::new();

scores.insert(String::from("Blue"), 10);
scores.insert(String::from("Yellow"), 50);

for (key, value) in &scores {
    println!("{key}: {value}");
}
```

### Managing Ownership in Hash Maps

```rust
use std::collections::HashMap;

let field_name = String::from("Favorite color");
let field_value = String::from("Blue");

let mut map = HashMap::new();
map.insert(field_name, field_value);
// field_name and field_value are invalid at this point, try using them and
// see what compiler error you get!
```

### Updating a Hash Map

Although the number of key and value pairs is growable, each unique key can only have one value associated with it at a time (but not vice versa: 

For example, both the Blue team and the Yellow team could have the value 10 stored in the scores hash map).

When you want to change the data in a hash map, you have to decide how to handle the case when a key already has a value assigned.

You could replace the old value with the new value, completely disregarding the old value.
 
You could keep the old value and ignore the new value, only adding the new value if the key doesn’t already have a value. Or you could combine the old value and the new value. 


### Overwriting a Value

```rust
use std::collections::HashMap;

let mut scores = HashMap::new();

scores.insert(String::from("Blue"), 10);
scores.insert(String::from("Blue"), 25);

println!("{scores:?}");
```

### Adding a Key and Value Only If a Key Isn’t Present

```rust
use std::collections::HashMap;

let mut scores = HashMap::new();
scores.insert(String::from("Blue"), 10);

scores.entry(String::from("Yellow")).or_insert(50);
scores.entry(String::from("Blue")).or_insert(50);

println!("{scores:?}");
```

### Updating a Value Based on the Old Value

```rust
use std::collections::HashMap;

let text = "hello world wonderful world";

let mut map = HashMap::new();

for word in text.split_whitespace() {
    let count = map.entry(word).or_insert(0);
    *count += 1;
}

println!("{map:?}");
```


















