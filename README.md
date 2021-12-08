# fast-rust
Small rust lang handbook

## Types and structures
```rust
// Structs
struct Struct(i32);
struct Struct2 { fld1 : i32, fld2 : f64, }
let s = Struct2 { fld1:10, fld2: 42.0 };
let Struct2 { fld1: a, fld2 : b, } = s;

// Enums
enum Enum { V1, V2(String), V3(i32, i32), V4 { i: i32, f: f32, } }
let e1 = Enum::V1;
let e2 = Enum::V2("s".to_string());
let e3 = Enum::V3(999, 888);
let e4 = Enum::V4 { i: 123, f: 146.0, };


```
