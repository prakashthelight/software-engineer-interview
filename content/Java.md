# Java

## Java Virtual Machine (JVM)

- Article explaining internal architecture of [JVM Internal](http://blog.jamesdbloom.com/JVMInternals.html)

## Garbage Collection

## Concurrency & Multithreading

## Autoboxing & Unboxing
- Java compiler makes an automatic conversion between primitive types and corresponding object wrapper classes i.e. `int` --> `Integer` [Autoboxing] and `Double` --> `double` [Unboxing]
- Compiler use `valueOf` autoboxing and `intValue` for unboxing
- For arithmatic operation with corresponding wrapper classes, internally unboxing and autoboxing is used
- Equality checks with `==` does not unbox, so use `equals`
