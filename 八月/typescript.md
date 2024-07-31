# *TypeScript 入门

## ts安装及运行

安装TypeScript：

```npm install -g typescript```

安装完成后我们可以使用 tsc 命令来执行 TypeScript 的相关代码，以下是查看版本号：
```
tsc -v
Version 5.5.4
```

通常来说，需要将 TypeScript 代码编译成 JavaScript 才能运行。这是因为 TypeScript 是一种静态类型的编程语言，而 JavaScript 是一种动态类型的语言。我们需要使用`tsc yourtsfile.ts`命令来把ts转化成js语言来运行。这个时候会在同一目录下生成一个叫yourtsfile.js的文件。
但我们通常不这么做，当我们需要频繁编译调试文件内容时，这种方法就很容易生成大量无用的js文件。那我们需要怎么做呢？我这里只写出自己使用的方法，并不是唯一或者最好的解决方案。

我们这里使用vscode编译器来学习TypeScript。首先我们先在扩展里面安装Code Runner。

![Code Runner]()

接着我们在终端安装 ts-node 以及Node.js 的类型定义：

```npm i ts-node @types/node@* -g```

成功以后我们直接点击vscode右上角的运行即可直接运行ts文件并输出结果了。例如：

![hellots]()

## TypeScript 基础语法

### 变量声明

TypeScript 变量的命名规则：

    - 变量名称可以包含数字和字母。

    - 除了下划线 _ 和美元 $ 符号外，不能包含其他特殊字符，包括空格。

    - 变量名不能以数字开头。

规范声明为：var [变量名] : [类型] = 值;
但是实际上，类型和值是可以省略的。

### 特殊项(只代表本人)

1. 组合类型（联合和泛型）
    - 联合
        比如说一个 boolean 类型可以描述为 ture 或者 flase：
      
        `type MyBool = true | false;`
        
    - 泛型
        泛型（Generics）是指在定义函数、接口或类的时候，不预先指定具体的类型，而在使用的时候再指定类型的一种特性。
      
        在typescript官方文档中有个例子：
       ```
       interface Backpack<Type> {
         add: (obj: Type) => void;
         get: () => Type;
       }
 
        // 这一行是一个简写，可以告诉 TypeScript 有一个常量，叫做`backpack`，并且不用担心它是从哪
        // 里来的。
        declare const backpack: Backpack<string>;
 
        // 对象是一个字符串，因为我们在上面声明了它作为 Backpack 的变量部分。
        const object = backpack.get();
 
        // 因为 backpack 变量是一个字符串，不能将数字传递给 add 函数。
        backpack.add(23);
```
        最后一行会报错，报错如下：
            Argument of type 'number' is not assignable to parameter of type 'string'. 







