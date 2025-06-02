**Day 1 Mistakes:**

### 1. Syntax Rules Are Strict in Rust

**Mistake:**  
```rust
use std::cmp::Ordering  // Missing semicolon
```
**Takeaway:**  
Always end statements (like `use`, `let`, `fn`) with a semicolon. Missing semicolons are a common beginner mistake.

**Tip:**  
If you see “expected ;, found…” in an error, scan for missing semicolons above.

---

### 2. Call Functions with `()`

**Mistake:**  
```rust
rand::rng.random_range(1..=100);  // `rng` is a function, not a module
```
**Takeaway:**  
You must call functions with `()` before using their return values.  
Correct: `rand::rng().random_range(...)`

**Tip:**  
If you’re chaining methods and get an error like “method not found,” check whether you forgot to add `()` to a function call.

---

### 3. Use Curly Braces or Commas in `match` Arms

**Mistake:**  
```rust
match ... {
    Ordering::Less => println!("too small");
    // ↑ This semicolon is invalid!
}
```
**Takeaway:**  
- Use `,` if it’s a one-liner.
- Use `{}` if it has multiple lines.
- Never end match arms with `;` — use `,` instead.

**Tip:**  
If the compiler complains about a match arm not having a body, you likely used a semicolon (`;`) instead of a comma (`,`) or forgot braces.

---

### 4. Use Proper String Interpolation

**Mistake:**  
```rust
println!("the number is you guessed is {guess}");
```
**Takeaway:**  
Rust doesn't interpolate variables inside strings directly.  
Use:
```rust
println!("You guessed: {}", guess);
```

**Tip:**  
Always use `{}` and pass variables outside the string in `println!`.

---

### 5. Pay Attention to Deprecation Warnings

**Warning:**  
```
warning: use of deprecated function `rand::thread_rng`: Renamed to `rng`
```
**Takeaway:**  
Rust tooling gives helpful warnings—read and act on them. Deprecation means the method still works, but you should use the updated one.

**Tip:**  
After updating crates, check the changelog or run `cargo clippy` to spot modern alternatives.

---

### 6. Use Compiler Help

**What You Did Right:**  
The compiler told you:
```
help: use parentheses to call this function
```
**Takeaway:**  
Rust’s compiler is your friend. When you hit an error, always read:
- The message
- The line/column number
- The “help” section

---

### 🧠 Summary: Rust Coding Checklist Based on Your Experience

| Checklist Item                       | Why It Matters                        |
|-------------------------------------- |---------------------------------------|
| Always end statements with `;`        | Prevents syntax errors                |
| Call functions with `()`              | Enables method chaining correctly     |
| Use `{}` or `,` in match arms         | Keeps match logic valid               |
| Format strings with `{}` + variables  | Prevents runtime errors and unclear output |
| Watch for and fix deprecation         | Keeps your code modern and compatible |
| Read compiler error messages fully    | They give actionable fixes            |
| Use a linter like clippy              | For best practices and cleaner code   |