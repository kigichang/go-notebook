# Go 第二版筆記

[Go Go 已經 15 歲了](https://go.dev/blog/15years)，由於[先前的筆記](https://github.com/kigichang/go_course)累積了很多歷史的進程，再加上近幾年工作關係，對 Go 的體驗有新的想法。因此重新整理筆記，移除過時汰除的內容，並且新增近幾年新的經驗。

新的筆記會由目前 1.23 版本開始，會與之前的版本有所不同；因此建議一同升版至 1.23 版本。如果想了解之前 Go 功能的變化，可以參考[先前的筆記](https://github.com/kigichang/go_course)。

## 資源

- [Go 官網](https://go.dev/)
- [Tutorials](https://go.dev/doc/tutorial/)
- [Go Wiki](https://go.dev/wiki/)
- [Effective Go](https://go.dev/doc/effective_go) (必讀)

## 開發環境

- Go: 1.23.3
- Apple M1 Pro
- 開發工具: [VSCode](https://code.visualstudio.com/)

## 筆記內容

### Go 基礎

1. *[Hello World](hello_world/README.md)
    - IDE 環境
    - Go 專案管理
    - Hello World
    - 跨平台編譯
    - Go 語言特性與 Rust, Scala 比較
1. 資料型別與流程控制
    - Primitive Type and Zero Value
    - Control Flow
    - Function
1. 進階資料型別與介面
    - Array and Slice
    - String and Rune
    - Map
    - Type, Alias and Enum
    - Struct and Method
1. Pointer and Interface
    - Struct and Pointer
    - Call by Value in Fuction and Method
    - Interface
    - Type Assertion
    - Type Switch
1. Package and OOP
    - Package and Encapsulation
    - Anonymous Field
    - Fake Inheritance
1. Defer and Error Handling
    - Error
    - Panic and Recover
    - Defer
1. Testing
    - Test
    - Benchmark
    - Example

## Go Concurrency

1. Goroutine, WaitGroup and Mutex
1. Channel and Select
1. Context

### Go 應用

1. JSON and Struct Tag
1. Command Line Tool: Cobra
1. Configuration: Viper and TOML
1. Database and MySQL
1. Text/Hmtl Template
1. Embed
1. Gorilla Web Tookit and WebSocket
1. Echo Web Framework
1. RESTful Service with Echo
1. GoCron
1. GRPC

### Go 進階

1. Build Constraints
1. Generic
1. Reflection
1. CGO
1. WebAssembly (不建議使用)
