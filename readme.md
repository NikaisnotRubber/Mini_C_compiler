# Mini C compile

## 使用環境
該項目實現了一個簡單的類`C`語言編譯器，使用`flex,bison和llvm`完成編寫，並使用`clang`進行最後可執行文件的編譯。

* OS：Linux
* flex
* bison
* llvm：10.0.0.1
* clang

配置環境有兩種方法：

1. 直接手動安裝所有的依賴項
2. 我們將必要的`llvm`等組件封裝到了`d1msh1mm32/ccompiler:1.0`的`docker`鏡像中，所以只需要安裝好·，使用 `docker`拉取該鏡像。詳細方法可以查看`docker/readme.md`文件

## 編譯方法

1. 進入`src`文件夾，使用`make`工具編譯，即可生成可執行文件`parser`
2. 運行可執行文件`parser`。通過`./parser xx.c`編譯`.c`文件，生成文件`example.bc`，該文件為二進制文件，可以通過llvm的命令執行。同時，命令行中會打印出對應的llvm IR代碼，以供參閱。
3. 輸入`lli example.bc`即可運行二進制文件`example.bc`
4. 為了查看其輸出，可以使用`echo $?`

## 文件結構

```shell
.
├── MY_C Compiler.pptx
├── docker
│   ├── MY_C_compiler.tar.gz
│   ├── dockerfile
│   └── readme.md
├── readme.md
├── report.md
├── src
│   ├── CodeTran.cpp
│   ├── CodeTran.hpp
│   ├── Makefile
│   ├── example.bc
│   ├── lex_test
│   │   ├── lex_test
│   │   ├── lex_test.cpp
│   │   ├── test
│   │   ├── test.txt
│   │   └── testl.l
│   ├── lexer.l
│   ├── main.cpp
│   ├── node.hpp
│   ├── parser.y
│   ├── test_0.c
│   ├── test_1.c
│   ├── test_2.c
│   └── test_3.c
└── tmp.md
```
