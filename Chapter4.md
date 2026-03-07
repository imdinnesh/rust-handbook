# Chapter 4: Understanding Ownership

Memory managemnt is done usually in 2 ways 

- Manual Allocation and Deallocation (C)
- Garbage Collection (Go,Java)

Rust brings a new concept of Ownership,Borrowing,References that makes it memory safe without the need of GC

### Stack and Heap

- Stack is fast, Heap is Slower
- Data size is known at compile time for Stack, Data size is unknown at compile time for Heap
- Stack is LIFO, Heap is Unordered

### Ownership Rules

- Each value in Rust has an owner.
- There can only be one owner at a time.
- When the owner goes out of scope, the value will be dropped.

### The Rules of References

- At any given time, you can have either one mutable reference or any number of immutable references.
- References must always be valid.

### The Slice Type

- Slices let you reference a contiguous sequence of elements in a collection.
- A slice is a kind of reference, so it does not have ownership.

```rust
    let s = String::from("hello world");
    let hello = &s[0..5];
    let world = &s[6..11];
```





