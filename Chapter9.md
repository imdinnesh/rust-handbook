# Error Handling

Rust groups errors into two major categories: recoverable and unrecoverable errors. 

For a recoverable error, such as a file not found error, we most likely just want to report the problem to the user and retry the operation. 

Unrecoverable errors are always symptoms of bugs, such as trying to access a location beyond the end of an array, and so we want to immediately stop the program.

Rust doesn’t have exceptions. Instead, it has the type Result<T, E> for recoverable errors and the panic! macro that stops execution when the program encounters an unrecoverable error.

### Unrecoverable Errors with panic!

Unrecoverable Errors with `panic!` in Rust
Overview
-  `panic!` macro: Used when an unrecoverable error occurs and the program cannot continue.

-  Causes:

   1. Code actions: e.g., accessing an array/vector index out of bounds.

   2. Explicit calls: Calling `panic!("message")` directly.

-  Default Behavior: Prints a failure message, unwinds the stack, cleans up memory, and quits.

Unwinding vs. Aborting
-  Unwinding (Default): Rust walks back up the stack and cleans up data from each function. This is more thorough but requires more work.

- Aborting: Immediately ends the program without cleanup (OS handles memory recovery).

  - Benefit: Results in a smaller binary.

  - Configuration: Add `panic = 'abort'` to `[profile.release]` in `Cargo.toml`.

Debugging Panics
- Error Message: Provides the specific file, line, and character where the panic originated (e.g., `src/main.rs:2:5`).

- Backtrace: A list of all functions called leading up to the error.

  - How to enable: Set environment variable `RUST_BACKTRACE=1`.

  - How to read: Start from the top and look for the first file you wrote. Lines above it are library/internal calls; lines below are what called your code.

  - Requirement: Debug symbols must be enabled (default in `dev` profile; disabled in `--release`).


Rust vs. C (Safety)
- C behavior: Out-of-bounds access is undefined behavior (buffer overread), leading to potential security vulnerabilities.

- Rust behavior: Stops execution immediately to prevent unauthorized memory access.
