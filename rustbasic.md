> The String Type
> https://doc.rust-lang.org/book/ch04-01-what-is-ownership.html#ownership-rules

The Rust Programming Language
Foreword
Introduction
# 1. Getting Started
## 1.1. Installation
## 1.2. Hello, World!
## 1.3. Hello, Cargo!
# 2. Programming a Guessing Game
# 3. Common Programming Concepts
## 3.1. Variables and Mutability
### `mut`

`let x = 5;`   `let mut x = 5;`

### `constant`

`const THREE_HOURS_IN_SECONDS: u32 = 60 * 60 * 3;`

name convention:`THREE_HOURS_IN_SECONDS`

### Shadowing
> shadowing可以相同名字不同数据类型
```
fn main() {
    let x = 5;

    let x = x + 1;

    {
        let x = x * 2;
        println!("The value of x in the inner scope is: {x}");
    }

    println!("The value of x is: {x}");
}
```
## 3.2. Data Types
### Scalar Types
1. Integer Types
   
   Rust’s defaults are generally good places to start: integer types default to `i32`
   
   ```
   Length	Signed	Unsigned
    8-bit	i8	    u8
    16-bit	i16	    u16
    32-bit	i32	    u32
    64-bit	i64	    u64
    128-bit	i128	u128
    arch	isize	usize
   ```
   
2. Floating-Point Types

   Rust’s floating-point types are `f32` and `f64`

   The default type is `f64`

   ```
   fn main() {
    let x = 2.0; // f64

    let y: f32 = 3.0; // f32
    }
   ```
   
3. The Boolean Type
   
   ```
   fn main() {
    let t = true;

    let f: bool = false; // with explicit type annotation
    }
   ```
4. The Character Type
   > Note that we specify `char` literals with `single quotes`,as opposed to `string literals`

   `char`

   ```
   fn main() {
    let c = 'z';
    let z: char = 'ℤ'; // with explicit type annotation
    let heart_eyed_cat = '😻';
    }
   ```


5. Numeric Operations
   ```
   fn main() {
    // addition
    let sum = 5 + 10;

    // subtraction
    let difference = 95.5 - 4.3;

    // multiplication
    let product = 4 * 30;

    // division
    let quotient = 56.7 / 32.2;
    // Integer division truncates toward zero to the nearest integer
    let truncated = -5 / 3; // Results in -1

    // remainder
    let remainder = 43 % 5;
    }
   ```  

###  compound Types
1. The Tuple Type

   `Tuples` have a `fixed length`: once declared, they cannot grow or shrink in size.

   ```
   fn main() {
    let tup: (i32, f64, u8) = (500, 6.4, 1);
    }
   ```

   To get the individual values out of a tuple:

   ```
   fn main() {
    let tup = (500, 6.4, 1);

    let (x, y, z) = tup;

    println!("The value of y is: {y}");
    }
   ```

   access a tuple element directly by using a period (.) 

   ```
   fn main() {
    let x: (i32, f64, u8) = (500, 6.4, 1);

    let five_hundred = x.0;

    let six_point_four = x.1;

    let one = x.2;
    }      
   ```

   空元组（`Unit`）
   
   表示方式: 空元组用 `()` 表示,它类似于其他语言中的 null 或 void

   类型: 空元组的类型也是 `()`
   
3. The Array Type

   > every element of an `array` must have the `same type`
   > An `array` isn’t as flexible,have a `fixed number of elements`
   > 类似类型`vector`元素数量可变
   

   ```
   fn main() {
    let a = [1, 2, 3, 4, 5];
    }
   ```

   `let a: [i32; 5] = [1, 2, 3, 4, 5];`

   `let a = [3; 5];`: 这行代码定义了一个数组 a，并将其初始化为包含 5 个元素的数组，每个元素的值都是 3。

    ```
    fn main() {
    let a = [1, 2, 3, 4, 5];

    let first = a[0];
    let second = a[1];
    }
    ```
## 3.3. Functions
`main` function: the entry point of many programs

name convention: `another_function`

```
fn main() {
    println!("Hello world!");

    first_function();

    second_function(5, 'y');

    let x = third_function();
    println!("{x}");

    let y = fourth_function(6);
    println!("{y}");

    let z = fifth_function(7);
    println!("{z}");
}

fn first_function() {
    println!("another");
}

fn second_function(value: i32, uint_label: char) {
    println!("The measurement is: {value}{uint_label}");
}

fn third_function() -> i32 {
    5      //后面没有 ；
}

fn fourth_function(x: i32) -> i32 {
    x + 1 //后面没有 ；
}

fn fifth_function(x: i32) -> i32 {
    if x < 0 {
        return 0;
    }

    if x > 10 {
        return 10;
    }

    x
}
```
statement：`let y = 6;`   Statements do not return values,therefore, you can’t assign a let statement to another variable

expression: `x + 1`

## 3.4. Comments
```
// It is a comment
fn main() {
    // It is a comment
    println!("Hello world!");  // It is a comment

}
```
## 3.5. Control Flow
### `if`

> If the condition isn’t a bool, we’ll get an error.

1.第一类:`if`
```
fn main() {
    let number = 3;

    if number < 5 {
        println!("condition was true");
    } 
}
```

2.第二类:`if else`
```
fn main() {
    let number = 3;

    if number < 5 {
        println!("condition was true");
    } else {
        println!("condition was false");
    }
}
```

3.第三类:`if    else if   else`
```
fn main() {
    let number = 11;

    if number % 4 == 0 {
        println!("number is divisible by 4");
    } else if number % 3 == 0 {
        println!("number is divisible by 3");
    } else if number % 2 == 0 {
        println!("number is divisible by 2");
    } else {
        println!("number is not divisible by 4, 3, or 2");
    }
}
```

4.第四类：`if`  +  `let`
```
fn main() {
    let condition = true;
    let number = if condition { 5 } else { 6 };   //  { 5 } 与 { 6 } 必须是同一个数据类型

    println!("The value of number is: {number}");
}
```

5.第五类：`match`

其他章节会详细讲解，类似于`if    else if   else`，但看上去更简洁


### `loop`
1.第一类：无限`loop`
```
fn main() {
    loop {
        println!("again!");
    }
}
```

2.第二类： `loop` + `continue` or `break`

3.第三类： `loop` 通过`break`去返回值
```
fn main() {
    let mut counter = 0;

    let result = loop {
        counter += 1;

        if counter == 10 {
            break counter * 2;   // 返回的值是counter * 2
        }
    };

    println!("The result is {result}");
}
```

4.第四类：`loop` + `label`

```
fn main() {
    let mut count = 0;
    'counting_up: loop {
        println!("count = {count}");
        let mut remaining = 10;

        loop {
            println!("remaining = {remaining}");
            if remaining == 9 {
                break;
            }
            if count == 2 {
                break 'counting_up;
            }
            remaining -= 1;
        }

        count += 1;
    }
    println!("End count = {count}");
}
```
### `while`
```
fn main() {
    let mut number = 3;

    while number != 0 {
        println!("{number}!");

        number -= 1;
    }

    println!("LIFTOFF!!!");
}
```

```
fn main() {
    let a = [10, 20, 30, 40, 50];
    let mut index = 0;
    
    while index < 5 {
        println!("the value is: {}", a[index]);

        index += 1;
    }
}
```
### `for`
```
fn main() {
    let a = [10, 20, 30, 40 ,50];

    for element in a {
        println!("the value is: {element}");
    }
}
```
`for` + `range` + `rev()`:

```
fn main() {
    for number in (1..4).rev() {
        println!("{number}!");
    }
    println!("LIFTOFF!!!");
}
```
# 4. Understanding Ownership
## 4.1. What is Ownership?
> Ownership is a set of rules that govern how a Rust program manages memory.

> `Pushing` to the `stack` is `faster` than allocating on the `heap`
> `Accessing` data in the `heap` is `slower` than accessing data on the `stack`

> `stack`上的所有数据必须具有已知且固定的大小。在编译时大小未知或大小可能变化的数据必须存储在`heap`上
### Stack & Heap
`stack`
1.The stack stores values in the order it gets them and removes the values in the opposite order.

2.` last in, first out`

3.Think of a stack of plates: when you add more plates, you put them on top of the pile, and when you need a plate, you take one off the top.

4.Adding data:` pushing onto`

  removing data：` popping off `

5.All data stored on the stack must have a known, fixed size

`heap`
`allocating on the heap`

指针：指向堆的指针是一个已知且固定大小的值，**因此可以存储在栈上**。当你需要实际数据时，你必须通过指针来访问它。

### Ownership Rules
a.Each value in Rust has an owner.
```
fn main() {
    let x = 42;  // x 是值 42 的所有者
}
```

b.There can only be one owner at a time
```
fn main() {
    let x = String::from("hello");  // x 是字符串 "hello" 的所有者
    let y = x;  // 所有权从 x 转移到 y
    // 现在 y 是字符串 "hello" 的所有者，x 不再有效
    // println!("{}", x);  // 这会导致编译错误，因为 x 不再有效
}
```
c.When the owner goes out of scope, the value will be dropped
```
fn main() {
    {
        let x = String::from("hello");  // x 是字符串 "hello" 的所有者
        // x 在这里有效
    }  // x 超出作用域，字符串 "hello" 被丢弃
    // x 在这里不再有效
}
```

### Variable Scope
```
    {                      // s is not valid here, it’s not yet declared
        let s = "hello";   // s is valid from this point forward

        // do stuff with s
    }                      // this scope is now over, and s is no longer valid
```

### The String Type
`string literals`: 不可变，固定大小，可存储在`stack`

`String`:          可变，非固定大小，可存储在`heap`

```
fn main() {
    let mut s = String::from("hello");

    s.push_str(",world!");

    println!("{s}");
}
```

### `move`
```
fn main() {
    let s1 = String::from("hello");
    let s2 = s1;

    println!("{s1}, world!");
}
```
> `let s2 = s1;`使得s1 `move` 到 s2,s1就失效，`println!("{s1}, world!");`就失效

### `clone`
```
fn main() {
    let s1 = String::from("hello");
    let s2 = s1.clone();

    println!("s1 = {s1}, s2 = {s2}!");
}
```
### `copy`
> 任何一组简单的标量值都可以实现 Copy 特性
> 而那些需要分配内存或涉及某种资源的类型则不能实现 Copy 特性

以下是一些实现了 Copy 特性的类型：

所有整数类型，如 `u32`。

布尔类型 `bool`，其值为 `true` 和 `false`。

所有浮点类型，如 `f64`。

字符类型`char`。

`元组`，如果它们只包含也实现了 Copy 特性的类型。例如，(i32, i32) 实现了 Copy，但 (i32, String) 没有。

## 4.2. References and Borrowing
## 4.3. The Slice Type
# 5. Using Structs to Structure Related Data
## 5.1. Defining and Instantiating Structs
## 5.2. An Example Program Using Structs
## 5.3. Method Syntax
# 6. Enums and Pattern Matching
## 6.1. Defining an Enum
## 6.2. The match Control Flow Construct
## 6.3. Concise Control Flow with if let
# 7. Managing Growing Projects with Packages, Crates, and Modules
## 7.1. Packages and Crates
## 7.2. Defining Modules to Control Scope and Privacy
## 7.3. Paths for Referring to an Item in the Module Tree
## 7.4. Bringing Paths Into Scope with the use Keyword
## 7.5. Separating Modules into Different Files
# 8. Common Collections
## 8.1. Storing Lists of Values with Vectors
## 8.2. Storing UTF-8 Encoded Text with Strings
## 8.3. Storing Keys with Associated Values in Hash Maps
# 9. Error Handling
## 9.1. Unrecoverable Errors with panic!
## 9.2. Recoverable Errors with Result
## 9.3. To panic! or Not to panic!
# 10. Generic Types, Traits, and Lifetimes
## 10.1. Generic Data Types
## 10.2. Traits: Defining Shared Behavior
## 10.3. Validating References with Lifetimes
# 11. Writing Automated Tests
## 11.1. How to Write Tests
## 11.2. Controlling How Tests Are Run
## 11.3. Test Organization
# 12. An I/O Project: Building a Command Line Program
## 12.1. Accepting Command Line Arguments
## 12.2. Reading a File
## 12.3. Refactoring to Improve Modularity and Error Handling
## 12.4. Developing the Library’s Functionality with Test Driven Development
## 12.5. Working with Environment Variables
## 12.6. Writing Error Messages to Standard Error Instead of Standard Output
# 13. Functional Language Features: Iterators and Closures
## 13.1. Closures: Anonymous Functions that Capture Their Environment
## 13.2. Processing a Series of Items with Iterators
## 13.3. Improving Our I/O Project
## 13.4. Comparing Performance: Loops vs. Iterators
# 14. More about Cargo and Crates.io
## 14.1. Customizing Builds with Release Profiles
## 14.2. Publishing a Crate to Crates.io
## 14.3. Cargo Workspaces
## 14.4. Installing Binaries from Crates.io with cargo install
## 14.5. Extending Cargo with Custom Commands
# 15. Smart Pointers
## 15.1. Using Box<T> to Point to Data on the Heap
## 15.2. Treating Smart Pointers Like Regular References with the Deref Trait
## 15.3. Running Code on Cleanup with the Drop Trait
## 15.4. Rc<T>, the Reference Counted Smart Pointer
## 15.5. RefCell<T> and the Interior Mutability Pattern
## 15.6. Reference Cycles Can Leak Memory
# 16. Fearless Concurrency
## 16.1. Using Threads to Run Code Simultaneously
## 16.2. Using Message Passing to Transfer Data Between Threads
## 16.3. Shared-State Concurrency
## 16.4. Extensible Concurrency with the Sync and Send Traits
# 17. Object Oriented Programming Features of Rust
## 17.1. Characteristics of Object-Oriented Languages
## 17.2. Using Trait Objects That Allow for Values of Different Types
## 17.3. Implementing an Object-Oriented Design Pattern
# 18. Patterns and Matching
## 18.1. All the Places Patterns Can Be Used
## 18.2. Refutability: Whether a Pattern Might Fail to Match
## 18.3. Pattern Syntax
# 19. Advanced Features
## 19.1. Unsafe Rust
## 19.2. Advanced Traits
## 19.3. Advanced Types
## 19.4. Advanced Functions and Closures
## 19.5. Macros
# 20. Final Project: Building a Multithreaded Web Server
## 20.1. Building a Single-Threaded Web Server
## 20.2. Turning Our Single-Threaded Server into a Multithreaded Server
## 20.3. Graceful Shutdown and Cleanup
# 21. Appendix
## 21.1. A - Keywords
## 21.2. B - Operators and Symbols
## 21.3. C - Derivable Traits
## 21.4. D - Useful Development Tools
## 21.5. E - Editions
## 21.6. F - Translations of the Book
## 21.7. G - How Rust is Made and “Nightly Rust”
