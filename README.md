# 每天掌握一个新知识点

* 2017.3.3：
 * 1.了解了一致性hash算法 
 * 2.初步学习了Go语言的基本语法

* 2017.3.4-3.5：周末有私事未学习

* 2017.3.6：
    * 1.尝试编写Node扩展，借助于 ```uv_queue_work``` 和 ```uv_async``` 构建了一个简单的tcp通信模块，并且该模块借助于信号量可以在js阻塞时继续工作。

* 2017.3.7
	* 1.工作比较忙，只有空闲了解了下RSA加密算法的原理

* 2017.3.8
	* 1.女神节陪老婆了，未学习

* 2017.3.9
	* 1.仔细了解下v8的两种GC算法，针对新生代的Scavenge算法（分成From和To两个部分，空间换时间）；以及针对老生代的Mark-Sweep/Mark-Compact算法（三色标记，由每一个内存页上的空洞情况决定是单纯清除死亡对象还是把存活对象复制到新的内存页上）

* 2017.3.10
	* 1.研究了在regexp的贪婪匹配模式下出现的灾难性回溯，长正则运算时v8提供的cpu-profiler时不时无法正常工作的原因，尚未找到结果

* 2017.3.11~3.12: 周末私事未学习

* 2017.3.13：
	* 1.定位编写的c++扩展模块运行偶尔会出现 **Check failed: AllowJavascriptExecution::IsAllowed(isolate).** 的错误。

* 2017.3.14：
    * 1.基本判断出了问题所在，signal和alarm误用，扩展中注册到c++扩展中的js函数执行前忘记使用 ```Nan::TryCatch``` 做保护，以及最关键的是 ```child_process.spawn``` 调用中出现异常导致子进程挂掉，而父进程中依旧维持了IPC管道通信，导致出现核心错误。
    * 2.了解了JIT技术，以及编译器生成汇编的原理，文章参考如下：
    	* [JavaScript Just-in-time (JIT) 工作原理](https://zhuanlan.zhihu.com/p/25669120)
    	* [编译器如何生成汇编](https://zhuanlan.zhihu.com/p/25718411)

* 2017.3.15:
	* 了解了webassembly对比js的一些优势：
		* 二进制文件体积小，下载快
		* 本身就是中间码，省却了js解释成抽象语法树在解析成中间码的过程
		* llvm阶段进行了大部分的优化，类型确定，所以在JIT阶段不会有js动态导致的同一段代码被编译成多个版本，以及重复优化-去优化的过程。
		* 垃圾回收手动控制，js则是由GC自动回收，效率更高。
	* 具体效果如何等待真正铺开后试用吧，听起来是很美好的。

* 2017.3.16: 有私事未学习
* 2017.3.17:
	* 作为一个伪前端，终于在工作之余尝试编写和了解一些css部分的知识，前端还是很奇妙的。
* 2017.3.18-3.19: 周末参与了南京Node.js地下铁活动
* 2017.3.20: 研究了下在fork模式下，如何传递参数为函数的方式，找到了解决办法，稍微有一点麻烦。
* 2017.3.21: 在做Easy-Monitor的文档整理，未学习新东西
* 2017.3.22: 身体不舒服，未学习
* 2017.3.23: 学习了v8的堆内内存结构组成与数据解析
* 2017.3.24: 解析了heapdump的包日志，大致已经完成，剩余以下难点:
	* (p1, p2, ...)->node->(c1, c2, ...)时，如何判断引用链对应
	* GC节点间的持有关系展示
* 2017.3.25-3.26: 周末有私事未学习
* 2017.3.27: 引用链对应的问题解决，剩下的重点：
	* 可定制化的可视化展示
	* 在单独一份heapdump数据的情况下定位疑似泄漏点
	* 在有多份间隔输出的heapdump数据的情况下定位疑似泄漏点