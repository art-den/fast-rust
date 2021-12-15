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
let string = "str \x41 \n \r \t \\ \u{7FFF} \' \" \0";
let raw_string = r#"hello"#;

// Integer
let i = 98_222 + 0xff + 0o77 + 0b1111_0000;
let i = 123i32;
let u = 123u32 + 123_u32;

// Float
let f = 1.0 + 1.0f32 + 1.0_f32;
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
fn process_slice(s: &[i32]) {}

// Structs
struct Struct(i32);
struct Struct2 { fld1: i32, fld2: f64, }
let s = Struct2 { fld1: 10, fld2: 42.0 };
let Struct2 { fld1: a, fld2: b, } = s;

// Enums
enum Enum { V1, V2(String), V3(i32, i32), V4 { i: i32, f: f32, } }
let e1 = Enum::V1;
let e2 = Enum::V2("s".to_string());
let e3 = Enum::V3(999, 888);
let e4 = Enum::V4 { i: 123, f: 146.0, };
```

## Methods
```rust
struct Rectangle { width: u32, height: u32, }

impl Rectangle {
    fn area(&self) -> u32 {
        self.width * self.height
    }

    fn can_hold(&self, other: &Rectangle) -> bool {
        self.width > other.width && self.height > other.height
    }
}
```

## Generic Data Types
```rust
fn same<T>(value: T) -> T {
    value
}

struct Point<T> { x: T, y: T, }

impl <T> Point<T> {
    fn some_fun(&self) {}
}

impl<T: Display> Point<T> {
    fn print(&self) {}
}

impl<T> Point<T> where T: Display {
    fn print(&self) {}
}

impl Point<f64> {
    fn dist(&self) -> f64 {}
}

let pt = Point { x: 1.0, y: 4.0 };
pt.print();
```

## Traits (interfaces)
```rust
trait Summary {
    fn summarize(&self) -> String;
}

struct Tweet { username: String, }

impl Summary for Tweet {
    fn summarize(&self) -> String {
        format!("{}", self.username)
    }
}

fn notify(item: &impl Summary) {}          // 1
fn notify<T: Summary>(item: &T) {}         // 2
fn notify<T>(item: &T) where T: Summary {} // 3

fn notify(item: &(impl Summary + Display)) {}         // 1
fn notify<T: Summary + Display>(item: &T) {}          // 2
fn notify<T>(item: &T) where T: Summary + Display {}  // 3
```

## Match
```rust
Some(50) => println!("Got 50"),
Some(y) => println!("{}", y),
//...
1 | 2 => println!("one or two"),
//...
1..=5 => println!("one through five"),
//...
Point { x, y: 0 } => println!("On the x axis at {}", x),
Point { x: 0, y } => println!("On the y axis at {}", y),
Point { x, y } => println!("On neither axis: ({}, {})", x, y),
//...
Message::Move { x, y } => ...
Message::ChangeColor(r, g, b) => ...
//...
Point { x, .. } => println!("{}", x),
Point { .., x } => println!("{}", x),
(first, .., last) => ...
//...
Some(x) if x < 5 => println!("less than five: {}", x),
4 | 5 | 6 if y => println!("yes"),
//...
Message::Hello { id: id_variable @ 3..=7, } => println!("{}", id_variable),
Message::Hello { id: 10..=12 } => ...

```
