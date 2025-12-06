# AGENTS.md

## Commands

### Build & Run
- `cargo build` - Build the project
- `cargo run` - Run the application
- `cargo check` - Quick compilation check

### Testing
- `cargo test` - Run all tests
- `cargo test test_function_name` - Run a single test
- `cargo test -- --nocapture` - Run tests with output

### Code Quality
- `cargo clippy` - Run linter
- `cargo fmt` - Format code
- `cargo clippy -- -D warnings` - Treat warnings as errors

## Code Style Guidelines

### Architecture
- Follow clean architecture: entities → repositories → usecases → handlers
- Entities: Domain models with business logic
- Repositories: Data access layer (async-trait for mocking)
- Usecases: Application business logic
- Handlers: HTTP request/response handling (Axum)

### Async & Error Handling
- Use async/await throughout
- Return `Result<T, sqlx::Error>` for database operations
- Use `?` operator for error propagation
- Wrap shared state in `Arc<>`

### Types & Naming
- Use `snake_case` for functions and variables
- Use `PascalCase` for types and structs
- Append `_getting()` to getter methods (e.g., `url_getting()`)
- Use `chrono` for date/time handling
- Use `uuid` for identifiers

### Imports
- Group imports: std → external crates → internal modules
- Use crate:: prefix for internal modules

### Testing
- Use `mockall` for mocking repositories
- Test files: `*_test.rs` in same directory as implementation
- Write unit tests for usecases, integration tests for handlers