# Chapter 2: Overview of Rust

### Guess the Number Game

**Take a look at the below code to get a feel for the language.**

```rust
use std::cmp::Ordering;
use std::io;

use rand::Rng;

fn main() {
    println!("Guess the number!");

    let secret_number = rand::thread_rng().gen_range(1..=100);

    loop {
        println!("Please input your guess.");

        let mut guess = String::new();

        io::stdin()
            .read_line(&mut guess)
            .expect("Failed to read line");

        let guess: u32 = match guess.trim().parse() {
            Ok(num) => num,
            Err(_) => continue,
        };

        println!("You guessed: {guess}");

        match guess.cmp(&secret_number) {
            Ordering::Less => println!("Too small!"),
            Ordering::Greater => println!("Too big!"),
            Ordering::Equal => {
                println!("You win!");
                break;
            }
        }
    }
}
```


### Explanation of the Code

**Import the standard library modules and external crate that we need.**

```rust
use std::cmp::Ordering; // Standard library
use std::io; // Standard library

use rand::Rng; // External crate
```

**Main Function**
```rust
fn main(){
    // fn Body
}
```

- This is the entry point of the program. 
- It doesnt take any arguments and returns nothing.

**Println Macro**
```rust
println!("Guess the number!");
```

- This is a macro that prints text to the console.
- Macros are denoted by the exclamation mark (!) after the macro name.
- Macros are similar to functions, but they are expanded at compile time.
- Macros are defined using the macro_rules! keyword.

**Variables**
```rust
let secret_number = rand::thread_rng().gen_range(1..=100);
```

- This is a variable that stores the secret number.
- The let keyword is used to declare a variable.
- The secret_number is the name of the variable.
- The rand::thread_rng().gen_range(1..=100) is the value of the variable.
- The :: is the scope operator.
- The thread_rng() is a function that returns a random number generator.
- The gen_range(1..=100) is a function that returns a random number in the range 1 to 100.


**Loop**
```rust
loop {
    // loop body
}
```

- This is a loop that runs indefinitely.
- The loop keyword is used to declare a loop.
- The loop body is the code that is executed in each iteration of the loop.
- continue, break, and return are used to control the flow of the loop.

Variables and Mutability
```rust
let mut guess = String::new();
```

- This is a variable that stores the guess.
- The mut keyword is used to declare a mutable variable.
- By default, variables are immutable in Rust.
- The String::new() is the value of the variable.
- The :: is the scope operator.
- The new() is a function that returns a new empty string.


**Input/Output**
```rust
io::stdin().read_line(&mut guess).expect("Failed to read line");
```

- This is a function that reads a line of input from the user.
- The io::stdin() is the standard input stream.
- The read_line() is a function that reads a line of input from the user.
- The &mut guess is a mutable reference to the guess variable.
- The expect() is a function that returns a Result type.
- The "Failed to read line" is the error message.

**Shadowing and Result Enum**
```rust
let guess: u32 = match guess.trim().parse() {
    Ok(num) => num,
    Err(_) => continue,
};
```

- This is a function that converts the guess to a number.
- The match keyword is used to match the result of the parse function.
- The Ok(num) is the result of the parse function.
- The Err(_) is the error of the parse function.
- The num is the value of the guess variable.
- The _ is a placeholder for the error value.

**Match**

```rust
match guess.cmp(&secret_number) {
    Ordering::Less => println!("Too small!"),
    Ordering::Greater => println!("Too big!"),
    Ordering::Equal => {
        println!("You win!");
        break;
    }
}
```

- This is a function that compares the guess to the secret number.
- The match keyword is used to match the result of the cmp function.
- The following are the possible results of the cmp function:
    - Ordering::Less
    - Ordering::Greater
    - Ordering::Equal


**Loop Control**

- continue is used to skip the current iteration of the loop.
- break is used to exit the loop.
- return is used to exit the function.

- In this code, the loop is used to keep the program running until the user guesses the correct number.

```rust
Ordering::Equal => 
{
    println!("You win!");
    break;
}
```













