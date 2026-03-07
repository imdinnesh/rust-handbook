# Chapter 6: Understanding Enums and Pattern Matching

### Defining an Enum

```rust
    enum IpAddr {
        V4(u8, u8, u8, u8),
        V6(String),
    }

    let home = IpAddr::V4(127, 0, 0, 1);

    let loopback = IpAddr::V6(String::from("::1"));
```

### The Option<T> Enum

```rust
    enum Option<T> {
        None,
        Some(T),
    }
```

### The match Control Flow Construct

```rust
    match value {
        pattern1 => expression1,
        pattern2 => expression2,
        _ => expression3,
    }
```

```rust
enum Coin {
    Penny,
    Nickel,
    Dime,
    Quarter,
}

fn value_in_cents(coin: Coin) -> u8 {
    match coin {
        Coin::Penny => 1,
        Coin::Nickel => 5,
        Coin::Dime => 10,
        Coin::Quarter => 25,
    }
}
```


