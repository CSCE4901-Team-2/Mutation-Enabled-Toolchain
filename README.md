# Mutation-Enabled-Toolchain
Mutation-Enabled Toolchain: Extending Go or Rust with Mutation Testing

Mutation testing is a method for evaluating the quality of test suites by introducing small changes (mutants) into the source code and checking whether the existing tests can detect the change. This project requires students to fork the official toolchain of either Go or Rust and add minimal mutation support at the compiler or test execution level. The mutation engine will support scalar operator flips (e.g., `+` to `-`). Each mutation will result in a separate test run to determine whether the test suite fails (killed mutant) or passes (survived mutant).

Features

Command-Line Integration

·           `go test -mutation` or `cargo test --mutation`
·           Mutations are only applied when the flag is enabled
·           Must support basic packages with existing test files
Scalar Mutation Engine

·           Apply simple mutations such as:
·           `+` to `-`
·           `-` to `+`
·           `==` to `!=`
·           `<` to `>=`
·           Only mutate one scalar operator per test run
Mutant Execution

·           For each mutant, compile mutated binary and run test suite
·           Log whether mutant was killed or survived
·           No need to parallelize mutant execution, but output should clearly label results
Reporting

·           Print killed/survived status per mutation
·           Display file and line number for mutation site
·           Optional: mutation summary table or JSON output
Language Choice

Students may choose either of the following:
Go

·           Fork the Go toolchain from https://github.com/golang/go
·           Modify `cmd/go` to introduce mutation flag
·           Use `go/ast` to find and apply scalar mutations
·           Compile and run test binaries per mutation
Rust

·           Fork `cargo` or `rustc`, or wrap via procedural macros
·           Add `--mutation` flag to `cargo test`
·           Use `syn` crate to manipulate AST for scalar ops
·           Compile mutated crate and run tests to verify detection
 
