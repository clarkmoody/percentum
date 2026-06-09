# Percentum

> **_per centum_** - "by a hundred"

A sane Percentage data type for Rust that encodes the underlying numeric representation explicitly.

```rust
let p = Percentage::from_fraction(0.55);
let q = Percentage::from_points(55.0);

assert_eq!(p, q);
```

## Feature Flags

- `bincode`: Implements `Encode` and `Decode`
- `decimal`: Implementation for `rust_decimal::Decimal`
- `serde`: Modules for serde operations on percentage points or fractions

```rust
#[derive(serde::Deserialize)]
struct Data {
    #[serde(with = "serde_fraction")]
    rate: Percentage<f64>,
}

let d = serde_json::from_str(r#"{ "rate": 0.55 }"#).unwrap();
assert_eq!(d.rate, Percentage::from_points(55.0));
```

## Supported Number Types

The `Number` trait is implemented for:

| Type                    | Feature Flag         |
| ----------------------- | -------------------- |
| `f32`                   | _(always available)_ |
| `f64`                   | _(always available)_ |
| `rust_decimal::Decimal` | `decimal`            |

## License

MIT
