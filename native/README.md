# Kotlin In Depth For Native

## Prepare

- Follow the [setup](https://www.jetbrains.com/help/kotlin-multiplatform-dev/multiplatform-setup.html) to set environment.
- Download a KMP project template from [KMP Wizard](https://kmp.jetbrains.com/)
- Open the KMP project using Idea or Android Studio, and it will download the kotlin native automatically.

## Hello World

Let's following the tutorial of [Kotlin Native Debug](https://kotlinlang.org/docs/native-debugging.html)

hello.kt:
```kotlin
fun main(args: Array<String>) {
  println("Hello world")
  println("I need your clothes, your boots and your motocycle")
}
```

Compile it

```shell
~/.konan/kotlin-native-prebuilt-macos-aarch64-2.1.0/bin/konanc -g hello.kt -o terminator
```

Let's see what are the compile results:

```shell
ls -al
drwxr-xr-x@ 5 sarace  staff      160 Mar  2 12:09 .
drwxr-xr-x@ 4 sarace  staff      128 Mar  2 12:10 ..
-rw-r--r--@ 1 sarace  staff      123 Mar  2 12:08 hello.kt
-rwxr-xr-x@ 1 sarace  staff  1302240 Mar  2 12:09 terminator.kexe
drwxr-xr-x@ 3 sarace  staff       96 Mar  2 12:09 terminator.kexe.dSYM
```

At the last line, we can see that there is a `_main`, let's begin to debug it.

```shell
lldb terminator.kexe
```

And let's set the breakpoint at `_main` and run it:

```shell
b main
r
```

