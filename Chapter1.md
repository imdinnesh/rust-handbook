# Chapter 1 Rust Installation and Setup

### Rust Insallation 

Follow the official docs for [installing Rust](https://rust-lang.org/tools/install/).

### Verify Installation

Check the Rust version by running the following command:

```bash
rustc --version
```

Check the Cargo version by running the following command:

```bash
cargo --version
```

### VS CODE Extension (Optional)

Install the [rust-analyzer](https://marketplace.visualstudio.com/items?itemName=rust-lang.rust-analyzer) extension for VS Code.

### Hello World

Create a new file called `main.rs` and add the following code:

```rust
fn main() {
    println!("Hello, world!");
}
```


### Creating a Project with Cargo

```bash
cargo new <project_name>
cd <project_name>
cargo run
```


- We can create a project using **cargo new**.

- We can build a project using **cargo build**.

- We can build and run a project in one step using **cargo run**.

- We can build a project without producing a binary to check for errors using **cargo check**.

Instead of saving the result of the build in the same directory as our code, Cargo stores it in the **target/debug** directory.


