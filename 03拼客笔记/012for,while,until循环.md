#### for循环
```
for val in list
do
    commands
done
```
* list字段分隔符是空格，默认自动换行，echo -n $i实现不自动换行
* unset val使变量失效
* 特殊符号转义或者加“ ”
* seq 1 6    //生成1到6
```
[fht@localhost 25]$ bash for_3.sh  
1
2
3
4
5
6
[fht@localhost 25]$ cat for_3.sh 
#!/bin/bash
for i in `seq 1 6 `
do
        echo $i
done
```

#### 字段分隔符IFS  环境变量
* 
```
[fht@localhost 25]$ set |grep IFS
IFS=$' \t\n'

*********
IFS_OLD=$IFS
IFS=$'\n'

for  xxx
do
    commands
done

IFS=IFS_OLD

```
* 在shell脚本中临时修改字段分隔符，IFS=$'\n'
* 输出文件夹，可用-d判断
```
[fht@localhost 25]$ cat for_4.sh 
#!/bin/bash
for i in /home/fht/*
do
        echo "$i"
done
```
#### while

```
while test commands
do
    other commands
done
```
* 相当于for和if的混合体
* while可以放多个判断条件，判断依据是最后一个命令的退出状态码为准
#### until
```
until test commands
do
    other commands
done
```
```
for ((a=1:a<=3;a++))
do
done
```
* 文件处理
* 字段分隔符、嵌套循环、IFS环境变量
* 控制循环
*   break退出当前循环（退出最近一层），break 2  退出两层
*   continue退出循环的本次迭代
*   exit直接退出脚本
#### 交互输入
*   位置参数 $1 $2 第一个参数、第二个参数 当传入变量超过9时，${10}
```
[fht@localhost 25]$ cat input.sh 
#!/bin/bash
#
#
#
echo $1;echo $2
[fht@localhost 25]$ bash input.sh 3 4
3
4
[fht@localhost 25]$ bash input.sh "dsds" s
dsds
s
```
*   特殊变量  $#获取传入参数的个数
*   echo ${!#}获取最后一个参数
*   $* 将所有命令行参数当成一个变量保存
*   $@ 将所有参数组成一个列表
* 创建函数
* 控制脚本
* 数据I/O

