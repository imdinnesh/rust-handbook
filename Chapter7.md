# Chapter 7: Understanding Packages, Crates, and Modules

### Packages, Crates

A Crate can be in two forms 
- A Library Crate
- A Binary Crate 

A Binary Crate is a crate that can be compiled to an executable file.

A Library Crate is a crate that can be used as a library by other crates.

A package is a bundle of one or more crates that provides a set of functionality.

A package contains a Cargo.toml file that describes how to build those crates.

Cargo is actually a package that contains the binary crate for the command line tool you’ve been using to build your code.

The Cargo package also contains a library crate that the binary crate depends on.

Other projects can depend on the Cargo library crate to use the same logic the Cargo command line tool uses.

A package can contain as many binary crates as you like, but at most only one library crate. 

A package must contain at least one crate, whether that’s a library or binary crate.



