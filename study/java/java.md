<!-- MarkdownTOC -->

- [JVM](#user-content-jvm)
    - [1. JVM参数](#user-content-1-jvm参数)
        - [1.1 Tomcat参数设置](#user-content-11-tomcat参数设置)
- [常见异常](#user-content-常见异常)
    - [1. Tomcat部署异常](#user-content-1-tomcat部署异常)
        - [1.1 java.net.UnknownHostException:xxx:xxx: 未知的名称或服务](#user-content-11-javanetunknownhostexceptionxxxxxx-未知的名称或服务)

<!-- /MarkdownTOC -->
## JVM

### 1. JVM参数

#### 1.1 Tomcat参数设置
在catalina.sh的第一行加上:
```sh
JAVA_OPTS="-Xms512m -Xmx1536m -Xss1024K -XX:PermSize=256m 
-XX:MaxPermSize=2048m   -Djava.util.Arrays.useLegacyMergeSort=true"
```

## 常见异常
### 1. Tomcat部署异常
#### 1.1 java.net.UnknownHostException:xxx:xxx: 未知的名称或服务

```sh
    hostname   //查看host
    hostname -i //查看host映射
    vim /etc/hosts  //维护host映射关系
```