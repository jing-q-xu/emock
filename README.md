# [English README](./README_en.md)

## `emock`自述

- `emock`是基于`mockcpp`改进的跨平台全能C++ mock库

## 正在开发

- **【唯一】**类似反射功能支持，无需声明即可mock（支持不可见的静态全局函数和动态库内部函数）
- 支持mock带有异常约束的函数
- 提供malloc的mock最佳实践方案

## 为什么选择`emock`?

- **【使用简单】** 学习成本低，仅一个宏
- **【没有依赖】** 除了STL和系统库函数
- **【跨平台】**   支持主流32位、64位系统（Linux、Windows）
- **【完全支持】** 支持mock所有类型的函数
- **【非侵入设计】** 不需要调整设计或待测代码

## 特性矩阵

#### 下面是和一些主流mock库的对比（如有错误，不吝指正）

<table style="text-align: center">
   <tr>
      <td></td>
      <td colspan="2">平台</td>
      <td colspan="3">成员函数</td>
      <td colspan="3">普通函数</td>
      <td>杂项</td>
   </tr>
   <tr>
      <td>库</td>
      <td>Linux</td>
      <td>Windows</td>
      <td>虚(不需要IoC)</td>
      <td>普通</td>
      <td>静态</td>
      <td>全局</td>
      <td>变参</td>
      <td>模板</td>
      <td>无需修改</td>
   </tr>
   <tr>
      <td><a href="https://github.com/ez8-co/emock"><strong>emock</strong></a></td>
      <td>:heavy_check_mark:</td>
      <td>:heavy_check_mark:</td>
      <td>:heavy_check_mark:(:heavy_check_mark:)</td>
      <td>:heavy_check_mark:</td>
      <td>:heavy_check_mark:</td>
      <td>:heavy_check_mark:</td>
      <td>:heavy_check_mark:</td>
      <td>:heavy_check_mark:</td>
      <td>:heavy_check_mark:</td>
   </tr>
   <tr>
      <td><a href="https://github.com/cpputest/cpputest">CppUMock</a></td>
      <td>:heavy_check_mark:</td>
      <td>:heavy_check_mark:</td>
      <td>:heavy_check_mark:(:x:<sup>[0]</sup>)</td>
      <td>:x:</td>
      <td>:heavy_check_mark:</td>
      <td>:heavy_check_mark:</td>
      <td>:heavy_check_mark:</td>
      <td>:heavy_check_mark:</td>
      <td>:grey_exclamation:<sup>[0]</sup></td>
   </tr>
   <tr>
      <td><a href="https://github.com/sinojelly/mockcpp">mockcpp</a></td>
      <td>:heavy_check_mark:</td>
      <td>:heavy_check_mark:</td>
      <td>:heavy_check_mark:(:x:<sup>[1]</sup>)</td>
      <td>:x:</td>
      <td>:heavy_check_mark:</td>
      <td>:heavy_check_mark:</td>
      <td>:x:</td>
      <td>:heavy_check_mark:</td>
      <td>:grey_exclamation:<sup>[1]</sup></td>
   </tr>
   <tr>
      <td><a href="https://github.com/google/googletest/tree/master/googlemock">googlemock</a></td>
      <td>:heavy_check_mark:</td>
      <td>:heavy_check_mark:</td>
      <td>:heavy_check_mark:(:x:<sup>[2]</sup>)</td>
      <td>:x:</td>
      <td>:x:</td>
      <td>:x:</td>
      <td>:x:</td>
      <td>:x:</td>
      <td>:grey_exclamation:<sup>[2]</sup></td>
   </tr>
   <tr>
      <td><a href="https://github.com/tpounds/mockitopp">mockitopp</a></td>
      <td>:heavy_check_mark:</td>
      <td>:heavy_check_mark:</td>
      <td>:heavy_check_mark:(:x:<sup>[1]</sup>)</td>
      <td>:x:</td>
      <td>:x:</td>
      <td>:x:</td>
      <td>:x:</td>
      <td>:x:</td>
      <td>:grey_exclamation:<sup>[1]</sup></td>
   </tr>
   <tr>
      <td><a href="https://github.com/hjagodzinski/C-Mock">C-Mock</a></td>
      <td>:heavy_check_mark:</td>
      <td>:x:</td>
      <td>:heavy_check_mark:(:x:<sup>[1]</sup>)</td>
      <td>:heavy_check_mark:</td>
      <td>:heavy_check_mark:</td>
      <td>:heavy_check_mark:</td>
      <td>:x:</td>
      <td>:x:</td>
      <td>:grey_exclamation:<sup>[1]</sup></td>
   </tr>
   <tr>
      <td><a href="https://github.com/gzc9047/CppFreeMock">CppFreeMock</a></td>
      <td>:heavy_check_mark:</td>
      <td>:x:</td>
      <td>:heavy_check_mark:(:x:<sup>[1]</sup>)</td>
      <td>:heavy_check_mark:</td>
      <td>:heavy_check_mark:</td>
      <td>:heavy_check_mark:</td>
      <td>:heavy_check_mark:</td>
      <td>:heavy_check_mark:</td>
      <td>:grey_exclamation:<sup>[1]</sup></td>
   </tr>
</table>

- 注:
  - <sup>[0]</sup>: 需要IoC接口，派生并实现待测类的虚成员函数
  - <sup>[1]</sup>: 需要定义接口（只有纯虚成员函数）不支持混合类（同时包含虚成员函数和普通成员函数的类）
  - <sup>[2]</sup>: 需要IoC接口（无法测试类内嵌对象或者引用），需要声明含有待测虚成员函数的派生类（相同参数列表和返回类型） 

#### 与使用API HOOK技术的库对比

<table style="text-align: center">
   <tr>
      <td>库</td>
      <td>跳转安全</td>
      <td>this指针可见[Windows]</td>
      <td>备注</td>
   </tr>
   <tr>
      <td><a href="https://github.com/ez8-co/emock"><strong>emock</strong></a></td>
      <td>:heavy_check_mark:</td>
      <td>:heavy_check_mark:</td>
      <td>使用蹦床将远跳变为短跳</td>
   </tr>
   <tr>
      <td><a href="https://github.com/sinojelly/mockcpp">mockcpp</a></td>
      <td>:x:</td>
      <td>:x:</td>
      <td>x64下直接使用14字节的远跳</td>
   </tr>
   <tr>
      <td><a href="https://github.com/gzc9047/CppFreeMock">CppFreeMock</a></td>
      <td>:x:</td>
      <td>:x:</td>
      <td>x64下直接使用14字节的远跳</td>
   </tr>
</table>

- `emock`理论上也支持UNIX, Android, MacOS和iOS等\*nix系统，但可能需要少量改动

## 最新支持

- 统一的`MOCKER`宏（虚函数不再需要用户进行控制反转支持）
- 支持mock可变参数函数，例如：`int test(int a, ...)`
- 支持mock重载的成员函数（Windows系统）
- 解决老的获取成员函数方法会有警告问题（Linux系统）
- 使用蹦床使得this指针可见（Windows系统）
- :clap: 使用短跳+蹦床的方法解决x64下非期望覆盖较小函数的问题

## 快速概览

  ```cpp
      MOCKER(function)
        .stubs() / defaults() / expects(never() | once() | exactly(3) | atLeast(3) | atMost(3) )
        [.before("some-mocker-id")]
        [.with( any() | eq(3) | neq(3) | gt(3) | lt(3) | spy(var_out) | check(check_func)
                | outBound(var_out) | outBoundP(var_out_addr, var_size) | mirror(var_in_addr, var_size)
                | smirror(string) | contains(string) | startWith(string) | endWith(string) )]
        [.after("some-mocker-id")]
        .will( returnValue(1) | repeat(1, 20) | returnObjectList(r1, r2)
                | invoke(func_stub) | ignoreReturnValue()
                | increase(from, to) | increase(from) | throws(exception) | die(3))
        [.then(returnValue(2))]
        [.id("some-mocker-id")]
  ```

## 使用手册

- [访问wiki学习如何使用`emock`](https://github.com/ez8-co/emock/wiki)

## 衷心感谢

- `emock`是基于`mockcpp`完善而来的
- 向`mockcpp`的作者和主要贡献者致敬:
  - [Darwin Yuan: darwin.yuan@gmail.com](https://github.com/godsme)
  - [Chen Guodong: sinojelly@gmail.com](https://github.com/sinojelly)
- 最原始版本从[mockcpp@bitbucket](https://bitbucket.org/godsme/mockcpp)导入

## 已知问题

- 和`valgrind`一起使用
  - 请添加`--smc-check=all`选项禁用缓存来防止动态修改机器码（API HOOK技术）部分失效导致不可预期的错误
  - 暂时无法mock `syscall`（系统调用）相关函数 （例如 `gettimeofday`）

## 写在最后

- 欢迎使用`emock`，并期待您的反馈！[创建issues](https://github.com/ez8-co/emock/issues/new)