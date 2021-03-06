# APUE 阅读笔记

<center>![apue](./img/apue.jpg)</center>


APUE是[《Advanced Programming in the UNIX® Environment》](http://www.apuebook.com)一书的简称，中文翻译为《Unix环境高级编程》:


IT书籍的名字有一个比较有趣的地方，至少我自己觉得 —— 凡是名字中说高级的（Advanced等）一般都属于基础容易懂得，凡是名字中说基础、引导的(Prime、Introduction等)对于一般人来说看起来都比较难以理解甚至晕头转向。APUE就属于那种很经典很基础很容易理解的所谓“高级”哪类。

APUE阅读起来其实没什么难度，需要的只是耐心（毕竟是个能当枕头的砖头书），至少比《算法导论》读起来要少废很多脑细胞。


本书网站的FAQ:

1. UNIX System和Unix system之间有什么区别？

When we speak of the UNIX System itself as an entity, we capitalize the 'S' in System. When we are speaking about a possible implementation of the UNIX System or a particular UNIX system, we use a lower-case 's'.

2. Unix和UNIX之间有什么区别？

The Unix operating system was developed at AT&T Bell Laboratories. When AT&T registered the name as a trademark, they capitalized the name to UNIX. Today the trademark is owned by The Open Group. For a system to call itself UNIX, it needs to meet certain criteria, pass conformance tests, and license the name.

3. Mac OS X 是UNIX系统吗？

As of version 10.5, Mac OS X has been formally certified to be a UNIX system.

4. FreeBSD 是UNIX系统吗？
While FreeBSD resembles a UNIX system and provides a UNIX-compatible environment, it has not yet been formally certified as a UNIX system. On the other hand, if it looks like a duck, walks like a duck, and quacks like a duck, then it's probably a duck.

5. Linux 是UNIX系统吗？

While Linux resembles a UNIX system and provides a UNIX-compatible environment, it has not yet been formally certified as a UNIX system. On the other hand, if it looks like a duck, walks like a duck, and quacks like a duck, then it's probably a duck.

6. Solaris 是UNIX系统吗？

Yes, Solaris has been formally certified to be a UNIX system.

7. 为什么链接到`-lbsd`的示例代码不能在我的系统上编译
The BSD compatibility library might not be installed on your system by default. For example, on Ubuntu, you need to install the libbsd-dev package.

我个人人为阅读本书需要一些先置条件：

+ 有一定的C基础
+ 有一台安装Linux/Unix操作系统计算机
+ 计算机上安装着gcc/clang和趁手的文本编辑器
+ 下载本书涉及到的[源码](http://www.apuebook.com/src.3e.tar.gz)

APUE的章节安排如下：

+ 第1章 UNIX基础知识
    1.1 引言
    1.2 UNIX体系结构
    1.3 登录
    1.4 文件和目录
    1.5 输入和输出
    1.6 程序和进程
    1.7 出错处理
    1.8 用户标识
    1.9 信号
    1.10 时间值
    1.11 系统调用和库函数
    1.12 小结
    习题
+ 第2章 UNIX标准及实现
    2.1 引言
    2.2 UNIX标准化
    2.2.1 ISO C
    2.2.2 IEEE POSIX
    2.2.3 Single UNIX Specification
    2.2.4 FIPS
    2.3 UNIX系统实现
    2.3.1 SVR4
    2.3.2 4.4BSD
    2.3.3 FreeBSD
    2.3.4 Linux
    2.3.5 Mac OS X
    2.3.6 Solaris
    2.3.7 其他UNIX系统
    2.4 标准和实现的关系
    2.5 限制
    2.5.1 ISO C限制
    2.5.2 POSIX限制
    2.5.3 XSI限制
    2.5.4 函数sysconf、pathconf和fpathconf
    2.5.5 不确定的运行时限制
    2.6 选项
    2.7 功能测试宏
    2.8 基本系统数据类型
    2.9 标准之间的冲突
    2.10 小结
    习题
+ 第3章 文件I/O
    3.1 引言
    3.2 文件描述符
    3.3 函数open和openat
    3.4 函数creat
    3.5 函数close
    3.6 函数lseek
    3.7 函数read
    3.8 函数write
    3.9 I/O的效率
    3.10 文件共享
    3.11 原子操作
    3.12 函数dup和dup2
    3.13 函数sync、fsync和fdatasync
    3.14 函数fcntl
    3.15 函数ioctl
    3.16 /dev/fd
    3.17 小结
    习题
+ 第4章 文件和目录
    4.1 引言
    4.2 函数stat、fstat、fstatat和lstat
    4.3 文件类型
    4.4 设置用户ID和设置组ID
    4.5 文件访问权限
    4.6 新文件和目录的所有权
    4.7 函数access和faccessat
    4.8 函数umask
    4.9 函数chmod、fchmod和fchmodat
    4.10 粘着位
    4.11 函数chown、fchown、fchownat和lchown
    4.12 文件长度
    4.13 文件截断
    4.14 文件系统
    4.15 函数link、linkat、unlink、unlinkat和remove
    4.16 函数rename和renameat
    4.17 符号链接
    4.18 创建和读取符号链接
    4.19 文件的时间
    4.20 函数futimens、utimensat和utimes
    4.21 函数mkdir、mkdirat和rmdir
    4.22 读目录
    4.23 函数chdir、fchdir和getcwd
    4.24 设备特殊文件
    4.25 文件访问权限位小结
    4.26 小结
    习题
+ 第5章 标准I/O库
    5.1 引言
    5.2 流和FILE对象
    5.3 标准输入、标准输出和标准错误
    5.4 缓冲
    5.5 打开流
    5.6 读和写流
    5.7 每次一行I/O
    5.8 标准I/O的效率
    5.9 二进制I/O
    5.10 定位流
    5.11 格式化I/O
    5.12 实现细节
    5.13 临时文件
    5.14 内存流
    5.15 标准I/O的替代软件
    5.16 小结
    习题
+ 第6章 系统数据文件和信息
    6.1 引言
    6.2 口令文件
    6.3 阴影口令
    6.4 组文件
    6.5 附属组ID
    6.6 实现区别
    6.7 其他数据文件
    6.8 登录账户记录
    6.9 系统标识
    6.10 时间和日期例程
    6.11 小结
    习题
+ 第7章 进程环境
    7.1 引言
    7.2 main函数
    7.3 进程终止
    7.4 命令行参数
    7.5 环境表
    7.6 C程序的存储空间布局
    7.7 共享库
    7.8 存储空间分配
    7.9 环境变量
    7.10 函数setjmp和longjmp
    7.11 函数getrlimit和setrlimit
    7.12 小结
    习题
+ 第8章 进程控制
    8.1 引言
    8.2 进程标识
    8.3 函数fork
    8.4 函数vfork
    8.5 函数exit
    8.6 函数wait和waitpid
    8.7 函数waitid
    8.8 函数wait3和wait4
    8.9 竞争条件
    8.10 函数exec
    8.11 更改用户ID和更改组ID
    8.12 解释器文件
    8.13 函数system
    8.14 进程会计
    8.15 用户标识
    8.16 进程调度
    8.17 进程时间
    8.18 小结
    习题
+ 第9章 进程关系
    9.1 引言
    9.2 终端登录
    9.3 网络登录
    9.4 进程组
    9.5 会话
    9.6 控制终端
    9.7 函数tcgetpgrp、tcsetpgrp和tcgetsid
    9.8 作业控制
    9.9 shell执行程序
    9.10 孤儿进程组
    9.11 FreeBSD实现
    9.12 小结
    习题
+ 第10章 信号
    10.1 引言
    10.2 信号概念
    10.3 函数signal
    10.4 不可靠的信号
    10.5 中断的系统调用
    10.6 可重入函数
    10.7 SIGCLD语义
    10.8 可靠信号术语和语义
    10.9 函数kill和raise
    10.10 函数alarm和pause
    10.11 信号集
    10.12 函数sigprocmask
    10.13 函数sigpending
    10.14 函数sigaction
    10.15 函数sigsetjmp和siglongjmp
    10.16 函数sigsuspend
    10.17 函数abort
    10.18 函数system
    10.19 函数sleep、nanosleep和clock_nanosleep
    10.20 函数sigqueue
    10.21 作业控制信号
    10.22 信号名和编号
    10.23 小结
    习题
+ 第11章 线程
    11.1 引言
    11.2 线程概念
    11.3 线程标识
    11.4 线程创建
    11.5 线程终止
    11.6 线程同步
    11.6.1 互斥量
    11.6.2 避免死锁
    11.6.3 函数pthread_mutex_timedlock
    11.6.4 读写锁
    11.6.5 带有超时的读写锁
    11.6.6 条件变量
    11.6.7 自旋锁
    11.6.8 屏障
    11.7 小结
    习题
+ 第12章 线程控制
    12.1 引言
    12.2 线程限制
    12.3 线程属性
    12.4 同步属性
    12.4.1 互斥量属性
    12.4.2 读写锁属性
    12.4.3 条件变量属性
    12.4.4 屏障属性
    12.5 重入
    12.6 线程特定数据
    12.7 取消选项
    12.8 线程和信号
    12.9 线程和fork
    12.10 线程和I/O
    12.11 小结
    习题
+ 第13章 守护进程
    13.1 引言
    13.2 守护进程的特征
    13.3 编程规则
    13.4 出错记录
    13.5 单实例守护进程
    13.6 守护进程的惯例
    13.7 客户进程-服务器进程模型
    13.8 小结
    习题
+ 第14章 高级I/O
    14.1 引言
    14.2 非阻塞I/O
    14.3 记录锁
    14.4 I/O多路转接
    14.4.1 函数select和pselect
    14.4.2 函数poll
    14.5 异步I/O
    14.5.1 System V异步I/O
    14.5.2 BSD异步I/O
    14.5.3 POSIX异步I/O
    14.6 函数readv和writev
    14.7 函数readn和writen
    14.8 存储映射I/O
    14.9 小结