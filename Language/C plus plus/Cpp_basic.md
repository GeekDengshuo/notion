
## __cdecl,__stdcall,__fastcall

### __cdecl,__stdcall,__fastcall  表示函数的调用规范，规定了参数出入栈的顺序和方法

- 在与C++等其他语言进行通信时，只有使用相同的方法才能调用成功
- printf接受可变参数的函数，只有cdecl才能实现

### 1.__cdecl

C Declaration  表示C语言默认的函数调用方法

Place the __**cdecl** modifier before a variable or a function name. Because the C naming and calling conventions are the default, the only time you need to use __**cdecl** is when you have specified the /Gz (stdcall) or /Gr (fastcall) compiler option. The [/Gd](http://blog.csdn.net/aweilark/article/details/2944549) compiler option forces the **__cdecl** calling convention.

***__cdecl*** 是默认的调用方式，所以只有在打开*/Gz(stdcall)*或*/Gr(fastcall)*开关时才需要加上，*/Gd*开关打开表示需要强制加上***__cdecl***

### 2.__cdecl,__stdcall

- __cdecl C Declaration; 所有参数从右向左依次入栈，参数由调用者清除，称为手动清栈
- __stdcall Standard Call ,是C++的标准调用方式 ，所有参数从右向左依次入栈，如果是调用类成员，最后一个入栈的是this指针，这些堆栈的参数由被调用的函数在返回后清除，称为自动清栈
    - 函数在编译的时候就必须确定参数个数，并且调用者必须严格控制参数的生成。

### 3.__fastcall

__fastcall 是编译器指定的快速调用方式，由于大多数的函数参数个数很少，使用堆栈传递比较费时

__fastcall规定将前两个或若干个参数由寄存器传递，其余参数函数堆栈传递

---

参考文档：

1.__cdecl

```
      编译器的命令行参数是/Gd。__cdecl方式是C/C++编译器默认的函数调用约定，所有非C++成员函数和那些没有用__stdcall或 __fastcall声明的函数都默认是__cdecl方式，它使用C函数调用方式，函数参数按照从右向左的顺序入栈，函数调用者负责清除栈中的参数，由于每次函数调用都要由编译器产生清除（还原）堆栈的代码，所以使用__cdecl方式编译的程序比使用__stdcall方式编译的程序要大很多，但是 __cdecl调用方式是由函数调用者负责清除栈中的函数参数，所以这种方式支持可变参数，比如printf和windows的API wsprintf就是__cdecl调用方式。对于C函数，__cdecl方式的名字修饰约定是在函数名称前添加一个下划线；对于C++函数，除非特别使用extern "C"，C++函数使用不同的名字修饰方式。

```

2.__fastcall

```
      编译器的命令行参数是/Gr。__fastcall函数调用约定在可能的情况下使用寄存器传递参数，通常是前两个 DWORD类型的参数或较小的参数使用ECX和EDX寄存器传递，其余参数按照从右向左的顺序入栈，被调用函数在返回之前负责清除栈中的参数。编译器使用两个@修饰函数名字，后跟十进制数表示的函数参数列表大小，例如：@function_name@number。需要注意的是__fastcall函数调用约定在不同的编译器上可能有不同的实现，比如16位的编译器和32位的编译器，另外，在使用内嵌汇编代码时，还要注意不能和编译器使用的寄存器有冲突。

```

3.__stdcall

```
    编译器的命令行参数是/Gz，__stdcall是Pascal程序的缺省调用方式，大多数Windows的API也是__stdcall调用约定。 __stdcall函数调用约定将函数参数从右向左入栈，除非使用指针或引用类型的参数，所有参数采用传值方式传递，由被调用函数负责清除栈中的参数。对于C函数，__stdcall的名称修饰方式是在函数名字前添加下划线，在函数名字后添加@和函数参数的大小，例如：_functionname@number

```

4.thiscall

```
      thiscall只用在C++成员函数的调用，函数参数按照从右向左的顺序入栈，类实例的this指针通过ECX寄存器传递。需要注意的是thiscall不是C++的关键字，不能使用thiscall声明函数，它只能由编译器使用。

```

5.naked call

```
        采用前面几种函数调用约定的函数，编译器会在必要的时候自动在函数开始添加保存ESI，EDI，EBX，EBP寄存器的代码，在退出函数时恢复这些寄存器的内容，使用naked call方式声明的函数不会添加这样的代码，这也就是为什么称其为naked的原因吧。naked    call不是类型修饰符，故必须和_declspec共同使用。

        VC的编译环境默认是使用__cdecl调用约定，也可以在编译环境的Project Setting...菜单－》C/C++ ＝》Code    Generation项选择设置函数调用约定。也可以直接在函数声明前添加关键字__stdcall、__cdecl或__fastcall等单独确定函数的调用方式。在Windows系统上开发软件常用到WINAPI宏，它可以根据编译设置翻译成适当的函数调用约定，在WIN32中，它被定义为 __stdcall

```


