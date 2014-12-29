<a name="appendix_b_glossary" />
# 术语汇编

<a name="AST" />
## 抽象语法树（abstract syntax tree, AST）

抽象语法树（Abstract Syntax Tree，AST）是一种代码表述形式，如果源代码结构良好，则编译器前端可以根据源代码来生成AST。AST中的每个节点都表示高级语言中的一种结构，例如循环或赋值。AST本身的节点不能出现循环结构。

Java字节码是非结构化的，其表现力也强于Java源代码，有时候没办法通过Java字节码来生成AST，因此，会使用JRockit IR是以图，而非树，的形式来展现的。

>参见[IR][IR]。

<a name="access_file" />
## 访问文件（access file）

在JMX中，访问文件用于指定不同角色的访问权限。一般情况下，该文件存放于`JROCKIT_HOME/jre/lib/management/jmxremote.access`。

>参见[密码文件][password_file]和[JMX][JMX]

<a name="adaptive_code_generation" />
## 自适应代码生成（adaptive code generation）

自适应代码生成是指在自适应环境中动态生产代码，例如JIT和混合模式解释执行代码。一般情况下，自适应代码生成会根据运行时反馈信息，对代码做多次优化。JVM是一个自适应环境，可以动态生产代码，而静态编译系统则无法办到。

>参见[JIT][JIT]和[混合模式解释执行][mixed_mode_interpretation]。

<a name="adaptive_memory_management" />
## 自适应内存管理（adaptive memory management）

自动内存管理是指应用某种自适应内存管理技术（例如垃圾回收器）来管理内存。本书中所指的自适应内存管理是指为了提升性能而根据运行时反馈信息来调整垃圾回收器的行为。

<a name="agent" />
## 代理（agent）

本书中的代理有两层含义，分别是JMX代理和JFR引擎，具体是哪个需要根据语境来判断。

>参见[JMX][JMX]和[JFR][JFR]。

<a name="ahead_of_time_compilation" />
## AOT编译（ahead-of-time compilation）

一般来说，AOT编译是指在执行代码之前现对全部或部分进行编译。C++编译器在生成二进制可执行文件时就是这样的。

>参见[JIT][JIT]。

<a name="allocation_profiling" />
## 内存分配分析（allocation profiling）

JRockit Management Console的一个特性就是运行用户实时查看应用程序中各个线程的内存分配情况。JFR中划分了多种内存分配分析事件，用户可以查看每个线程中每种事件类型的统计数据。

<a name="atomic_instruction" />
## 原子指令（atomic_instruction）

原子指令在执行时，无论操作对象是什么，指令要么都执行，要么都不执行。根据硬件模型的不同，在执行普通指令时，可能会因弱内存语义而乱序执行，相比之下，原子指令的执行时间通过会比普通指令大几个数量级。大部分CPU架构所支持的[比较并交换][CAS]指令就是一个原子指令。

>参见[比较并交换][CAS]。

<a name="automatic_memory_management" />
## 自动内存管理（automatic_memory_management）

本书中，自动内存管理是指在运行时系统中使用垃圾回收器来管理内存。

<a name="balloon_driver" />
## 膨胀驱动程序（balloon driver）

在虚拟环境中，虚拟机管理程序可以使用名为膨胀驱动程序（其具体形式可能会虚拟设备驱动程序）来隐式的与客户应用程序来协商内存使用情况。通过这种机制，客户应用程序对内存的使用请求就可以跨越虚拟抽象层这道屏障，实现内存使用的动态伸缩。

>参见[虚拟化][virtualization] [客户应用程序][guest]和[虚拟机应用程序][hypervisor]。

<a name="basic_block" />
## 基本块（basic_block）

在编译器的中间表示中，基本块是最小的控制流单元。一般情况下，基本块中会包含0个或多个指令，并且具有"一荣俱荣"的特性，即若是执行了基本块中的某条指令，则肯定会执行该基本块中的所有指令。

>参见[控制流图][control_flow_graph]。

<a name="benchmark_driver" />
## 基准测试驱动（benchmark driver）

基准测试驱动是指在基准测试中通过一台或多台机器来增加负载，然后在衡量基准测试目标操作的实际执行时间时，再将这部分工作时间排除在外的测试方式。

<a name="biased_locking" />
## 偏向锁（biased locking）

>参见[延迟解锁][lazy_unlocking]。

<a name="bytecode" />
## 字节码（bytecode）

字节码是由源代码转化成的、平台无关的二进制表示，就Java来说，字节码由Java源代码编译而成。Java字节码中包含了操作指令（长度为1个字节）和操作数，其结构化程度不如Java源代码，可以任意使用`goto`指令和其他Java源代码中不存在的结构，因此其表现力也远强于Java源代码。

<a name="bytecode_interpertation">
## 字节码解释执行（bytecode interpretation）

字节码解释执行是指，在虚拟执行栈中，以模拟字节码指令、虚拟机状态和本地变量表的形式来运行字节码代码。字节码解释执行的启动速递比编译执行快，但运行性能较低。

<a name="call_profiling" />
## 调用分析（call profiling）

调用分析是指在JIT代码中注入特定代码查看方法的调用频率或调用路径。收集到的调用分析主要用于做代码优化，例如找出应该将哪些方法做内联处理。

>参见[自适应代码生成][adaptive_code_generation]和[JIT][JIT]。

<a name="card" />
## 卡（card）

在本书中， 卡是一中数据结构，用于表示某块堆内存。整个堆内存被划分为多个卡，存储与卡表中。在分代式垃圾回收中，卡表用于判断老年代指定分区是否是脏的（dirty），即该区域中是否有对象包含有指向年轻代中对象的引用。

>参见[写屏障][write_barrier]和[分代式垃圾回收][generational_garbage_collection]。

<a name="card_table" />
## 卡表（card table）

>参见[卡][card]。

<a name="class_block">
## 类块（class block）

类块是JRockit中的名词，指对象头中所指向的、包含了类型信息的数据块。

>参见[对象头][object_header]。

<a name="class_garbage_collection" />
## 类型垃圾回收（class garbage collection）

类型垃圾回收是指JVM对运行时中的类型信息进行清理。如果某个类已经被卸载了，而且没有`java.lang.ClassLoader`实例或其他代码引用该类或其方式时，就可以将其清理掉了。

<a name="client_side_template" />
## 客户端模板（client-side template）

JRockit Mission Control的客户端模板用于控制运行时记录的事件设置。解析改模板文件时，采用的全解析策略，即不支持通配符。模板文件可以带有版本信息。

>参见[事件设置][event_settings]和[服务器端模板][server_side_template]。

<a name="cloud" />
## 云（cloud）

云是指集中大量分布式计算资源（可能是虚拟计算资源），用户可以在其中部署自己的应用程序。

>参见[虚拟化][virtualization]。

<a name="code_generation_queue" />
## 代码生成队列

代码生成队列是JRockit中的一个词儿，为了保证Java应用程序的持续运行，JVM会先将代码生成请求放入到指定队列中，而后代码生成线程会从该队列中获取任务，执行代码生成任务，之后JVM再执行新生成的代码。

>参见[优化队列][optimization_queue]。

<a name="color" />
## 着色（color）

在本书中，着色是指对具有某种特性节点进行标记，常用于寄存器分配算法或引用追踪垃圾回收算法。

在寄存器分配算法中，同时正在使用的变量可以表示为图中的两个相邻节点，于是寄存器分配算法就可以转化为"如何对图中的节点进行着色，使相邻节点具有不同的颜色"，其中可用颜色的数量等于可用寄存器的数量。

此外，着色还可应用于引用追踪垃圾回收算法。通常情况下，标记-清理算法会使用若干种颜色来标记垃圾回收过程已经处理过的若干种对象。

>参见[寄存器分配][register_allocation]和[引用追踪垃圾回收][tracing_garbage_collection]。

<a name="compaction" />
## 内存整理（compaction）

内存整理可用于降低堆的碎片化程度。经过内存整理后，对象会被移动到一起，形成一块大的存活区域，消除内存碎片。对整个堆做内存整理操作，往往需要暂停应用程序线程。

>参见[碎片化][fragmentation]。

<a name="CAS" />
## 比较并交换（compare and swap, CAS）

目前很多CPU架构都支持原子指令，例如x86平台的`cmpxchg`指令和SPARK平台的`cas`指令，这种指令会比较内存和寄存器中的值，若相匹配，则用预设的某个值来覆盖内存中的值。如果覆盖成功，则该指令会设置标志寄存器，做分支处理使用。该指令常用于实现自旋锁。

>参见[原子指令][atomic_instruction]和[自旋锁][spinlock]。

<a name="compressed_reference" />
## 压缩引用（compressed reference）

引用压缩是一种Java对象模型的实现机制，在这种机制下，应用程序中对象的引用会比系统级的指针小。例如，在64位系统上，如果Java堆小于4GB，则记录对象地址只需32位就够了，在运行时中使用64位完全是浪费。载入/解压缩Java对象的指针会有一点开销（不过并不大），但却可以极大的提升系统的运行速度。

>参见[引用压缩][reference_compression]和[引用解压缩][reference_decompression]。

<a name="concurrent_garbage_collection" />
## 并发垃圾回收（concurrent garbage collection）

在本书中，并发垃圾回收是指在垃圾回收周期的大部分时间内，Java应用程序还可以继续执行的垃圾回收算法。

>参见[并行垃圾回收][parallel_garbage_collection]。

<a name="conservative_garbage_collection" />
## 保守式垃圾回收(conservative garbage collection)

保守式垃圾回收会将所有有可能是对象的内容都当作对象来处理，之所以这样是因为它不会记录对象的元信息。这种实现方式会降低垃圾回收的执行效率，因为没有元信息，垃圾回收器不得不做一些额外的检查。例如，数字17不是一个对象指针，因为它不在堆空间内，而数字0x471148则有可能是一个对象指针，但也有可能只是个常量值。如果某个常量碰巧指向了堆中的某个对象，则保守式垃圾回收很有可能会把这个常量也当作对象而保留下来。这些特性决定了保守式垃圾回收在移动对象时会受到很大的限制。

>参见[准确式垃圾回收][exact_garbage_collection] [活动对象图][livemap]和[安全点][safepoint]。

<a name="constant_pool" />
## 常量池（constant pool）

常量池是class文件中的一部分，其中存储了方法所使用到的常量字符串的较大的数字。

<a name="continuous_JRA" />
## 持续型JRA

持续型JRA，表示记录任务会一直持续运行，是早期开发JRA时的概念，后来JRA被JFR所取代。

>参见[JFR][JFR]。

<a name="control_flow_graph" />
## 控制流图（control flow graph，CFG）

控制流图是一种程序表示方式，在其中以图的形式展示了程序可能具有的执行路径（通常会以基本块作为节点）。图中节点之间的边可以表示直接跳转（如`goto`）、条件跳转、转换表（table switch）等，

>参见[偏向锁][biased_locking]。

<a name="cpu_profiling" />
## CPU分析（cpu profiling）

CPU分析是JRockit Management Console中的一项功能，可以显示出每个线程的CPU使用情况。

<a name="critical_section" />
## 临界区（critical section）

临界区是指只能被单线程运行的代码片段。实现的时候，一般会在临界区前后用锁（例如同步块）来控制多线程访问。

<a name="dead_code" />
## 死代码（dead code）

死代码是指应用程序中永远也不会被执行的代码。如果编译器能正确某段代码确实是死代码，则编译器通常会删除这段死代码。

<a name="deadlock" />
## 死锁（deadlock）

死锁是指，两个线程都因等待对方释放自己需要的资源而被阻塞住。相关线程自己是无法解锁的，只能永远等下去。虽然不消耗CPU资源，但死锁依然是很严重的问题

>参见[胖锁][fat lock]和[活锁][livelock]。

<a name="deadlock_detection" />
## 死锁检测（deadlock detection）

死锁检测是JRockit Management Console的一项功能，用于检测系统中是否存在死锁的线程。

>参见[死锁][deadlock]。


[AST]:                              #AST                                "抽象语法树"
[IR]:                               #IR                                 "中间表示"
[access_file]:                      #access_file                        "访问文件"
[password_file]:                    #password_file                      "密码文件"
[JMX]:                              #JMX                                "JMX"
[JIT]:                              #JIT                                "JIT"
[mixed_mode_interpretation]:        #mixed_mode_interpretation          "混合模式解释执行"
[adaptive_code_generation]:         #adaptive_code_generation           "自适应代码生成"
[adaptive_memory_management]:       #adaptive_memory_management         "自适应内存管理"
[agent]:                            #agent                              "代理"
[JFR]:                              #JFR                                "JRockit Flight Recorder"
[allocation_profiling]:             #allocation_profiling               "内存分配分析"
[atomic_instruction]:               #atomic_instruction                 "原子指令"
[CAS]:                              #CAS                                "比较并交换"
[automatic_memory_management]:      #automatic_memory_management        "自动内存管理"
[balloon_driver]:                   #balloon_driver                     "膨胀驱动程序"
[virtualization]:                   #virtualization                     "虚拟化"
[guest]:                            #guest                              "客户应用程序"
[hypervisor]:                       #hypervisor                         "虚拟机管理程序"
[control_flow_graph]:               #control_flow_graph                 "控制流图"
[benchmark_driver]:                 #benchmark_driver                   "基准测试驱动"
[biased_locking]:                   #biased_locking                     "偏向锁"
[lazy_unlocking]:                   #lazy_unlocking                     "延迟解锁"
[bytecode]:                         #bytecode                           "字节码"
[bytecode_interpertation]:          #bytecode_interpertation            "字节码解释执行"
[call_profiling]:                   #call_profiling                     "调用分析"
[card]:                             #card                               "卡"
[write_barrier]:                    #write_barrier                      "写屏障"
[generational_garbage_collection]:  #generational_garbage_collection    "分代式垃圾回收"
[card_table]:                       #card_table                         "卡表"
[class_block]:                      #class_block                        "类块"
[object_header]:                    #object_header                      "对象头"
[class_garbage_collection]:         #class_garbage_collection           "类型垃圾回收"
[client_side_template]:             #client_side_template               "客户端模板"
[server_side_template]:             #server_side_template               "服务器端模板"
[optimization_queue]:               #optimization_queue                 "优化队列"
[code_generation_queue]:            #code_generation_queue              "代码生成队列"
[color]:                            #color                              "着色"
[register_allocation]:              #register_allocation                "寄存器分配"
[tracing_garbage_collection]:       #tracing_garbage_collection         "引用追踪垃圾回收"
[compaction]:                       #compaction                         "内存整理"
[fragmentation]:                    #fragmentation                      "碎片化"
[spinlock]:                         #spinlock                           "自旋锁"
[compressed_reference]:             #compressed_reference               "压缩引用"
[reference_compression]:            #reference_compression              "引用压缩"
[reference_decompression]:          #reference_decompression            "引用解压缩"
[concurrent_garbage_collection]:    #concurrent_garbage_collection      "并发垃圾回收"
[parallel_garbage_collection]:      #parallel_garbage_collection        "并行垃圾回收"
[conservative_garbage_collection]:  #conservative_garbage_collection    "保守式垃圾回收"
[exact_garbage_collection]:         #exact_garbage_collection           "准确式垃圾回收"
[livemap]:                          #livemap                            "活动对象图"
[safepoint]:                        #safepoint                          "安全点"
[constant_pool]:                    #constant_pool                      "常量池"
[continuous_JRA]:                   #continuous_JRA                     "持续型JRA"
[cpu_profiling]:                    #cpu_profiling                      "CPU分析"
[critical_section]:                 #critical_section                   "临界区"
[dead_code]:                        #dead_code                          "死代码"
[deadlock]:                         #deadlock                           "死锁"
[fat_lock]:                         #fat_lock                           "胖锁"
[livelock]:                         #livelock                           "活锁"
[deadlock_detection]:               #deadlock_detection                 "死锁检测"