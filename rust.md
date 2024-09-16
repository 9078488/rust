## 学习资料
https://doc.rust-lang.org/book/


`rustup update`:获取最新版本的 Rust

`rustup self uninstall`:卸载

`cargo --version`:要检查您是否安装了 Rust 和 Cargo，可以在终端中运行

`cargo build`: 可以构建项目

`cargo run`: 可以运行项目:build and run a project in one step

`cargo test`: 可以测试项目

`cargo doc`: 可以为项目构建文档

`cargo publish`: 可以将库发布到 crates.io。

`cargo check`: This command quickly checks your code to make sure it compiles but doesn’t produce an executable:

## 创建新项目
`cargo new``cargo new hello-rust`

`Cargo.toml`:为 Rust 的清单文件。其中包含了项目的元数据和依赖库

`src/main.rs`: 为编写应用代码的地方

## dependencies
`crates`: https://crates.io/

1.Cargo.toml中添加
```rust
[dependencies]
ferris-says = "0.2"
```

2.`cargo build`:生成`Cargo.lock`-该文件记录了本地所用依赖库的精确版本

3.引用：
`use ferris_says::say;`

### Anatomy of a Rust Program
```rust
fn main() {

}
```
The `main` function is special: it is always the first code that runs in every executable Rust program

### rustfmt
https://doc.rust-lang.org/book/appendix-04-useful-development-tools.html
`rustc`


### rustc main.rs
是 Rust 编译器的命令，用于编译一个名为 main.rs 的 Rust 源文件

`println!`:For now, you just need to know that using a ! means that you’re calling a macro instead of a normal function and that macros don’t always follow the same rules as functions.

Rust style is to indent with four spaces, not a tab.
