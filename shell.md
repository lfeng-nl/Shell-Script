# 本文介绍shel及shell脚本相关问题

## 1.shell

### a.管道

### b.重定向

## 2.shell脚本

### a.变量

- shell 中的变量无须事先声明，默认情况下，所有变量都被认为是字符串类型；注意变量的赋值，`=`号前后无空格：

  ```shell
  test="Hi lfeng"
  ```

- 在变量名前加`$`可以获取变量内容；

- 单引号和双引号：单引号的`$`变量名不会读取变量内容，双引号会读取`$`后的变量内容；

  ```shell
  #!/bin/bash
  test="Hi lfeng"
  echo "$test"			
  #输出：Hi lfeng
  echo '$test'
  #输出：$test
  echo "\$test"
  #输出：$test
  ```

- 环境变量：系统已经初始化好的具有特殊意义的变量；
  - `$HOME`：当前用户的家目录；
  - `$PATH`：用冒号`:`分隔的用来搜索命令的目录列表；
  - `$PS1`：命令提示符号，通常是`$`
  - `$PS2`：二级提示符号，通常是`>`
  - `$IFS`：输入分隔符号；
  - `$0`：shell脚本的名字
  - `$1`：第一个参数；
  - `$#`：shell脚本参数的个数；
  - `$$`：shell脚本的进程号，（可以用它来生成唯一的临时文件）；

- 参数变量

  - `$1、$2`：脚本的参数；
  - `$*`：所有参数，以`$IFS`分隔；
  - `$@`：所有参数，以空格分隔，不依靠`$IFS`，比较可靠，推荐使用；

### b.条件

shell中使用`test`或`[ ]`命令来进行判断，可以对==文件类型==和==值==（字符串和算数比较）进行比较；

- 字符串比较

  ```shell
  string1 = string2
  #相等为真
  string1 != string2
  #不等为真
  -n string
  #不为空为真
  -z string
  #空串为真
  ```

- 算数比较

  ```shell
  expression1 -eq expression2
  # 两个表达式相等为真
  expression1 -ne expression2
  # 两个表达式不相等为真
  expression1 -gt expression2
  # expression1 大于 expression2为真
  expression1 -ge expression2
  # expression1 大于等于 expression2为真
  expression1 -lt expression2
  # expression1 小于 expression2为真
  expression1 -le expression2
  # expression1 小于等于 expression2为真
  ！expression1
  ```

- 文件测试

  ```shell
  -f file
  # 文件是否存在
  ```

### c.控制语句

  - if语句

    ```shell
    if [...]
    then
        ...
    elif [...]
    then
        ...
    else
        ...
    if
    ```

- for语句

  ```shell
  for variable in values
  do
  	...
  done
  ```

### d.命令

### f.here文档
