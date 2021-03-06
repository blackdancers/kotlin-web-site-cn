---
type: doc
layout: reference
category: "Syntax"
title: "包"
---

# 包

源文件通常以包声明开头:

``` kotlin
package foo.bar

fun baz() {}

class Goo {}

// ……
```

源文件所有内容（无论是类还是函数）都包含在声明的包内。
所以上例中 `baz()` 的全名是 `foo.bar.baz`、`Goo` 的全名是 `foo.bar.Goo`。

如果没有指明包，该文件的内容属于无名字的默认包。

## 默认导入

有多个包会默认导入到每个 Kotlin 文件中：

- kotlin.*
- kotlin.annotation.*
- kotlin.collections.*
- kotlin.comparisons.*  （自 1.1 起）
- kotlin.io.*
- kotlin.ranges.*
- kotlin.sequences.*
- kotlin.text.*

根据目标平台还会导入额外的包：

- JVM:
  - java.lang.*
  - kotlin.jvm.*

- JS:    
  - kotlin.js.*

## 导入

除了默认导入之外，每个文件可以包含它自己的导入指令。
导入语法在[语法](grammar.html#import)中讲述。

可以导入一个单独的名字，如.

``` kotlin
import foo.Bar // 现在 Bar 可以不用限定符访问
```

也可以导入一个作用域下的所有内容（包、类、对象等）:

``` kotlin
import foo.* // “foo”中的一切都可访问
```

如果出现名字冲突，可以使用 *as*{: .keyword } 关键字在本地重命名冲突项来消歧义：

``` kotlin
import foo.Bar // Bar 可访问
import bar.Bar as bBar // bBar 代表“bar.Bar”
```

关键字 `import` 并不仅限于导入类；也可用它来导入其他声明：

  * 顶层函数及属性
  * 在[对象声明](object-declarations.html#对象声明)中声明的函数和属性;
  * [枚举常量](enum-classes.html)

与 Java 不同，Kotlin 没有单独的 "import static" 语法； 所有这些声明都用 `import` 关键字导入。

## 顶层声明的可见性

如果顶层声明是 *private*{: .keyword } 的，它是声明它的文件所私有的（参见 [可见性修饰符](visibility-modifiers.html)）。
