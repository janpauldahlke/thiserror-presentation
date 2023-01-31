my questions to jörn

* how did you learn all the background information about rust and the rfc and the error trait?

my learnings
* thiserror crate for systemdevelopment
  * it compiles out of the program, so it can not log in the program runtime

* anyhow crate for application development: 
  * keeps errors in program, so it can be seen in program runtime

* given this example:
  i find it nice, that by the conventation of the order we get the error for free

```rust
use thiserror::Error as ThisError;
const MIN_TEMP: usize = 10;

#[derive(Debug, ThisError)]
pub enum MyEnumError {
    #[error("things simply didn't work")]
    SimpleVariant,
    #[error("found only {0} entries")]
    NotEnoughEntries(usize),
    #[error("Not warm enough: {temperature} {unit} < {}", MIN_TEMP)]
    Temperature { temperature: usize, unit: String },
}
```

* i find it nice, that you return to the example of last week

```rust
fn foo() -> Result<(), FooError> {
  Ok(bar()?)
}

fn bar() -> Result<(), BarError> {
  Ok(baz()?)
}

fn baz() -> Result<(), BazError> {
  Err(BazError{})
}
```
