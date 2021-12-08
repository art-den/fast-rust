# fast-rust
Small rust lang handbook

## Literals
```rust
// ascii strings:
let byte = b'a';
let byte_string = b"hello";
let raw_byte_string = br#"hello"#;

// unicode strings:
let charaster = 'c';
let string = "str \x41 \n \r \t \\ \0";
let raw_string = r#"hello"#;
```

## Types and structures
```rust
// Tuples
let tup = (500, 6.4, 1);
let tup: (i32, f64, u8) = (500, 6.4, 1);

// Arrays
let a = [1, 2, 3, 4, 5];
let a: [i32; 5] = [1, 2, 3, 4, 5];
let a = [3; 5]; // [3, 3, 3, 3, 3]

// Slices
let arr = [1, 2, 3, 4, 5];
let slice = &arr[..2];
let slice = &arr[2..];
let slice = &arr[0..2];

// Structs
struct Struct(i32);
struct Struct2 { fld1: i32, fld2: f64, }
let s = Struct2 { fld1: 10, fld2: 42.0 };
let Struct2 { fld1: a, fld2 : b, } = s;

// Enums
enum Enum { V1, V2(String), V3(i32, i32), V4 { i: i32, f: f32, } }
let e1 = Enum::V1;
let e2 = Enum::V2("s".to_string());
let e3 = Enum::V3(999, 888);
let e4 = Enum::V4 { i: 123, f: 146.0, };


```
