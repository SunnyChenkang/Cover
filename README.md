### Cover是什么
cover是一个用c写的`web开发框架`，目前正在开发中(后期可能考虑用面向对象的方式进行开发或者使用C++进行开发)，其目的是为喜欢C语言或者C++编程语言的开发者提供一个web开发的框架，使他们能够更专注的处理业务逻辑而不必过多的考虑HTTP协议的问题，由于属于开发框架，所以关于数据库，关于交换数据格式等均不做处理

### Cover的设计思想
cover的设计思想主要来源与Golang的开源项目gin和beego。其目的是给C程序员一个相对简单的开发框架，让C程序员更简单的做后台接口开发。当然，目前还属于实验阶段，还未从实验室走向工程。如果需要更加稳定，成熟服务器端接口开发框架，建议使用Beego进行开发，beego和gin这类golang框架是基于golang标准库进行封装的。而标准库是基于协议进行抽象的，这点是Cover和beego或者gin不同的地方，Cover是直接基于协议进行的抽象（因为C标准库没有做基于协议的封装，而golang则有，这是进步,所以C程序员用起golang来是双到不能再爽了。。）

### 代码思路
* 读取Cover的配置文件
* 启动监听网络套接字
* 添加url映射关系
* 执行Cover等待连接
* 连接到来，启动线程处理（万事开头难，目前服务器端开发模型采用多线程模型，后续采用更高效的模型或者网络库）
* 解析HTTP协议，根据URL映射关系执行回调函数
* 返回结果 （目前在Cover中还没有编写Response相关的处理，所以开发者需要在业务逻辑中主动send。。）

### 如何使用Cover
具体Demo可以参考CoverServer给出的Demo。
首先，启动Cover,调用CoverInit函数
其次，调用CoverHandler函数添加你的业务相关的模块
最后，启动Cover,调用CoverRun函数

然后你需要进行处理的是针对自己的业务逻辑编写业务处理模块。

`关于CoverHandler中设置的回调函数的问题`
回调函数要求带有两个参数，一个时HTTP结构，定义在Cover中的http.h中，令一个参数是套接字描述符。由于目前只支持Linux环境，所以套接字描述符类型为int类型

### 

###关于作者
* weibo:[@ICKelin]http://weibo.com/u/2621944791
* Email:15077305083@163.com

