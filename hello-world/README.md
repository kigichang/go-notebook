  
# Hello World
  
## 1. 開發環境
  
1. 至[官網](https://go.dev/dl/ )下載對應平台的安裝檔。
1. 下載並安裝 [VSCode](https://code.visualstudio.com/ )。
1. 安裝 [Go Extension](https://marketplace.visualstudio.com/items?itemName=golang.Go )。
  
完成以上安裝後，基本的 Go 開發環境就完成了。
  
## 2. Go 專案管理 (Workspace 與 Module)
  
以本專案為例，說明如何使用 Workspace 與 Module 同時管理多個相依專案。如果只是單一專案，可以直接使用 Module。
  
### 2.1 Workspace
  
Workspace 可以同時管理多個相依專案。
  
1. 建立 Workspace 目錄，如: `mkdir go-notebook`。
1. 進入 Workspace 目錄，`cd go-notebook`。
1. 執行 `go work init`，在 **go-notebook** 目錄下，產生 **go.work** 檔案。
1. 當有多個專案加入 Workspace 後，可以使用 `go work sync` 同步 Workspace 中的專案依賴的套件。
  
### 2.2 Module
  
Module 是 Go 1.11 之後的功能，可以讓專案不需要放在 ```$GOPATH``` 下，並且可以有自己的相依套件管理。
  
1. 在 Workspace 目錄下，建立專案目錄，如: `mkdir hello-world`。
1. 進入專案目錄，`cd hello-world`。
1. 執行 `go mod init hello-world`，在 **hello-world** 目錄下，產生 **go.mod** 檔案。
1. 執行 `go work use .`，將 **hello-world** 加入到 Workspace 的 **go.work** 中。
1. 在 **hello_world** 目錄下，建立 `main.go` 檔案，開始第一個程式。
  
## 3. Hello World
  
撰寫以下程式碼：
  
```go
package main
  
import "fmt"
  
func main() {
	println("Hello, World!")
	fmt.Println("Hello, World!")
}
  
```  
  
### 3.1 執行與編譯
  
- 在目錄下，執行 `go run .` 可以看到結果。
- 在目錄下，執行 `go build .` 可以編譯出執行檔。
  
### 3.2 程式說明
  
1. 寫執行檔的程式，檔名不一定要命名成 `main.go`，但主程式建議使用 `main.go`，程式碼的 `package` 宣告一定要是 **main**。
1. 程式的進入點 (Entry point): `func main()`，跟大多數的程式語言一樣，寫執行檔都會需要有一個主函式 **main**
1. 經過編譯之後，產生的執行檔名，會是 Module 的名稱，可以查看 **go.mod** 的 `module` 設定。
1. 使用 `import` 相依的 package 加入。如果使用 Go 內建的 package，自動加入到程式碼中。
1. 如果是第三方套件，就要修改 `go.mod` 加入。加入後，在該目錄下執行 `go mod tidy` 則會自動更新依賴的 package。
  
### 3.3 跨平台編譯
  
Go 支援跨平台，可以編譯不同平台的執行檔。在編譯時，可以指定不同平台的編譯。如編譯 Linux 的執行檔：
  
```bash
$ env GOOS=linux GOARCH=amd64 go build .
```
  
如果要查詢對應的平台，可以執行 `go tool dist list` 查詢。依[官方文件](https://go.dev/doc/install/source#environment )，列出支援的平台有：
  
| ```$GOOS``` | ```$GOARCH``` |
| ----------- | ------------- |
| aix         | ppc64         |
| android     | 386           |
| android     | amd64         |
| android     | arm           |
| android     | arm64         |
| darwin      | amd64         |
| darwin      | arm64         |
| dragonfly   | amd64         |
| freebsd     | 386           |
| freebsd     | amd64         |
| freebsd     | arm           |
| illumos     | amd64         |
| ios         | arm64         |
| js          | wasm          |
| linux       | 386           |
| linux       | amd64         |
| linux       | arm           |
| linux       | arm64         |
| linux       | loong64       |
| linux       | mips          |
| linux       | mipsle        |
| linux       | mips64        |
| linux       | mips64le      |
| linux       | ppc64         |
| linux       | ppc64le       |
| linux       | riscv64       |
| linux       | s390x         |
| netbsd      | 386           |
| netbsd      | amd64         |
| netbsd      | arm           |
| openbsd     | 386           |
| openbsd     | amd64         |
| openbsd     | arm           |
| openbsd     | arm64         |
| plan9       | 386           |
| plan9       | amd64         |
| plan9       | arm           |
| solaris     | amd64         |
| wasip1      | wasm          |
| windows     | 386           |
| windows     | amd64         |
| windows     | arm           |
| windows     | arm64         |
  
如果在 Linux 平台，可以多加 `CGO_ENABLED=0`，不使用目前 Linux 編譯環境上的 GNU C Library，避免在其他 Linux 環境上，出現版本不相容的問題。
  
```bash
$ env GOOS=linux GOARCH=amd64 CGO_ENABLED=0 go build .
```
  
### 3.4 Go 環境變數
  
列出所有 Go 環境變數：
  
```bash
$ go env
```
  
或查看某個環境變數，如 ```$GOOS```:
  
```bash
$ go env GOOS
```
  
## 4. Go 語言重點特性
  
1. Go 是編譯式語言，編譯成機器碼，而不是像 Java 是 Byte Code。
1. Go 是強型別語言，變數宣告後，資料型別固定。
1. Go 可以跨平台執行，前提是沒有使用到平台特有的函式庫。
1. Go 有 Garbage Collection，可以不用自己管理記憶體。
1. Go 有指標 (Pointer)。
1. Go 沒有 OOP 的繼承。
1. Go 的 Visibility，只有 **public**, **private**，使用名稱的第一個字母 **大** (Public)、**小** (Private) 寫來區分。
1. 預設編碼是 UTF-8。因此檔案的編碼，一定要是 UTF-8。
1. 參數傳遞 (Paramenter Passing) 是 **Pass by Value** (Call by Value)。
  
## 5. Rust, Go, Scala 比較
  
以下是我從 Rust, Go, 與 Scala 的過往經驗的比較。筆者 Java 經驗停在 JDK 8 前的版本，之後轉用 Scala；Scala 之後就以 Go 為主。Scala 版本，筆者是停留在 2.11 版本，因此如果對 Scala 的理解有錯，還請指正。
  
:+1: 是我非常喜歡的程式語言特性，Go 在某些方面上，支援度較弱。Go 標榜 **大道至簡** 的精神，沒有太複雜的機制，因此易學易上手，非常適合當作第二程式語言學習。
  
| 比較 | Rust | Go | Scala |
| - | - | - | - |
| Artifact | Machine Code | Machine Code with **Go Runtime**，也因此檔案會比較大 | JVM Bytecode |
| 跨平台 | Y | Y | Y (依賴 JVM) |
| Garbage Collection (GC) | **N** | Y | Y |
| Object-Oriented Programming| N (沒有繼承) | N (沒有繼承) | Y |
| :+1: **Functional Programming (FP)** | **Y** | Y (支援程度不如 Rust / Scala) | Y |
| :+1: **Generic (泛型)** | **Y** | Y (Go 1.18 之後版本，目前還在進步中，支援功能，遠遠不及 Rust / Scala) | Y |
| Unsigned 型別 | Y | Y | N |
| Unit 型別 | **Y** `()` | N | Y `Unit` |
| :+1: **NULL** | **N**, use `Option` instead  | Yes, `nil` | N, use `Option` instead |
| :+1: **Tuple** | **Y** | Y (只支援在 **return** 時回傳多組值) | Y |
| :+1: **Interface** | **Y** (Trait) | Y (Interface) | Y (Trait) |
| :+1: **Default Function in Interface** | **Y** | N (不能在 interface 實作 function) | Y |
| :+1: **Enum** | **Y** | N (只能用 const + iota 模擬) | Y |
| :+1: **Macro** | **Y** | N | Y |
| Inline | **Y** | N (Go compiler 會自動判斷是否要 inline [^go_inline]) | Y |
| :+1: **Pattern Matching** | **Y** | N | Y |
| :+1: **if-then-else** | **expression (可 return 值)** | statement | expression (可 return 值) |
| :+1: **Operator Overloading** | **Y** | N | Y |
| Concurrency / Parallel / Async | thread / async / channel / actor | goroutine / channel / wait group | thread / async / actor |
| :+1: **Error Handling** | **Result** / **Option** | Error | Try / Either / Option |
| Syntactic Sugar (語法糖) | 中 | 弱 | 太強 (會像在寫天書) |
| Package 管理 | 較複雜，但也更有彈性 | 較簡單 | 較簡單 |
| Coding Style | camel (Struct & Trait) and snake (Varible & Function) | camel | camel |
  
[^go_inline]: [Compiler And Runtime Optimizations](https://github.com/golang/go/wiki/CompilerOptimizations#function-inlining )
  