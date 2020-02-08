# RustKit
Fast and ergonomic Rust bindings for ObjC APIs

RustKit is currently under development. Please try it if you want to contribute or provide feedback on the generated bindings.

## Prerequisites
clang / llvm 9.0.1 from homebrew
```
brew install llvm
```
Make sure that the appropriate llvm-config is in your path

## Example

```
extern crate rustkit;

use rustkit::NSObject;

fn main() {
    let obj = NSObject::new();
    
    let desc = NSObject::description();
    let desc = desc.unwrap();
    let desclen = desc.length();
    let ruststr: String =
        (0..desclen).map(|i|
                         std::char::from_u32(desc.characterAtIndex_(i) as u32).
                         unwrap()).collect();
    println!("NSObject::description(): {}", ruststr);
}
```
