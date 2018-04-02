<!-- MarkdownTOC -->

- [JAVA 基础知识](#JAVA-基础知识)
    - [1. 概念](#1-概念)
        - [1.1 方法签名](#11-方法签名)
    - [2. 类型](#2-类型)
        - [2.1 基本类型成员变量初始化默认值](#21-基本类型成员变量初始化默认值)
- [JVM](#JVM)
    - [1. JVM参数](#1-JVM参数)
        - [1.1 Tomcat参数设置](#11-Tomcat参数设置)
        - [1.2 Tomcat　UTF-8编码设置](#12-Tomcat　UTF-8编码设置)
- [常见异常](#常见异常)
    - [1. Tomcat部署异常](#1-Tomcat部署异常)
        - [1.1 java.net.UnknownHostException:xxx:xxx: 未知的名称或服务](#11-javanetUnknownHostExceptionxxxxxx-未知的名称或服务)
- [关键字](#关键字)
    - [transient](#transient)

<!-- /MarkdownTOC -->
## JAVA 基础知识
### 1. 概念
#### 1.1 方法签名
方法签名　=　方法名称　+　参数列表(类型，个数，顺序)
### 2. 类型
#### 2.1 基本类型成员变量初始化默认值
| 基本类型 |     默认值     |
|----------|----------------|
| boolean  | false          |
| char     | '\u0000'(null) |
| byte     | (byte)0        |
| short    | (short)0       |
| int      | 0              |
| long     | 0L             |
| float    | 0.0f           |
| double   | 0.0d           |

>*只有作为类的成员变量时才初始化为上述默认值，作为局部变量时为任意值(**基本局部变量未初始化赋值，在被使用时会报错**)．*

## JVM

### 1. JVM参数

#### 1.1 Tomcat参数设置
在catalina.sh的第一行加上:
```sh
JAVA_OPTS="-Xms512m -Xmx1536m -Xss1024K -XX:PermSize=256m 
-XX:MaxPermSize=2048m   -Djava.util.Arrays.useLegacyMergeSort=true"
```
#### 1.2 Tomcat　UTF-8编码设置
在conf/server.xml添加如下
```xml
<Connector URIEncoding="UTF-8"/>
```

## 常见异常
### 1. Tomcat部署异常
#### 1.1 java.net.UnknownHostException:xxx:xxx: 未知的名称或服务

```shell
    hostname   #查看host
    hostname -i #查看host映射
    vim /etc/hosts  #维护host映射关系
```

## 关键字

### transient
> 使声明的属性不进行序列化, 不能持久化, 只能修饰类的属性