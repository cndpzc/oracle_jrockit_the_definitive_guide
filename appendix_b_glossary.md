<a name="appendix_b_glossary" />
# 术语汇编

<a name="AST" />
## 抽象语法树（abstract syntax tree, AST）

抽象语法树（Abstract Syntax Tree，AST）是一种代码表述形式，如果源代码结构良好，则编译器前端可以根据源代码来生成AST。AST中的每个节点都表示高级语言中的一种结构，例如循环或赋值。AST本身的节点不能出现循环结构。

Java字节码是非结构化的，其表现力也强于Java源代码，有时候没办法通过Java字节码来生成AST，因此，会使用JRockit IR是以图，而非树，的形式来展现的。

>另见[IR][IR]。

<a name="access_file" />
## 访问文件（access file）

在JMX中，访问文件用于指定不同角色的访问权限。一般情况下，该文件存放于`JROCKIT_HOME/jre/lib/management/jmxremote.access`。

>另见[密码文件][password_file]和[JMX][JMX]

<a name="adaptive_code_generation" />
## 自适应代码生成（adaptive code generation）

自适应代码生成是指在自适应环境中动态生产代码，例如JIT和混合模式解释执行代码。一般情况下，自适应代码生成会根据运行时反馈信息，对代码做多次优化。JVM是一个自适应环境，可以动态生产代码，而静态编译系统则无法办到。

>另见[JIT][JIT]和[混合模式解释执行][mixed_mode_interpretation]。

<a name="adaptive_memory_management" />
## 自适应内存管理（adaptive memory management）

自动内存管理是指应用某种自适应内存管理技术（例如垃圾回收器）来管理内存。本书中所指的自适应内存管理是指为了提升性能而根据运行时反馈信息来调整垃圾回收器的行为。

<a name="agent" />
## 代理（agent）

本书中的代理有两层含义，分别是JMX代理和JFR引擎，具体是哪个需要根据语境来判断。

>另见[JMX][JMX]和[JFR][JFR]。

<a name="ahead_of_time_compilation" />
## AOT编译（ahead-of-time compilation）

一般来说，AOT编译是指在执行代码之前现对全部或部分进行编译。C++编译器在生成二进制可执行文件时就是这样的。

>另见[JIT][JIT]。

<a name="allocation_profiling" />
## 内存分配分析（allocation profiling）

JRockit Management Console的一个特性就是运行用户实时查看应用程序中各个线程的内存分配情况。JFR中划分了多种内存分配分析事件，用户可以查看每个线程中每种事件类型的统计数据。

<a name="atomic_instruction" />
## 原子指令（atomic_instruction）

原子指令在执行时，无论操作对象是什么，指令要么都执行，要么都不执行。根据硬件模型的不同，在执行普通指令时，可能会因弱内存语义而乱序执行，相比之下，原子指令的执行时间通过会比普通指令大几个数量级。大部分CPU架构所支持的[比较并交换][CAS]指令就是一个原子指令。

>另见[比较并交换][CAS]。

<a name="automatic_memory_management" />
## 自动内存管理（automatic_memory_management）

本书中，自动内存管理是指在运行时系统中使用垃圾回收器来管理内存。

<a name="balloon_driver" />
## 膨胀驱动程序（balloon driver）

在虚拟环境中，虚拟机管理程序可以使用名为膨胀驱动程序（其具体形式可能会虚拟设备驱动程序）来隐式的与客户应用程序来协商内存使用情况。通过这种机制，客户应用程序对内存的使用请求就可以跨越虚拟抽象层这道屏障，实现内存使用的动态伸缩。

>另见[虚拟化][virtualization] [客户应用程序][guest]和[虚拟机应用程序][hypervisor]。

<a name="basic_block" />
## 基本块（basic_block）

在编译器的中间表示中，基本块是最小的控制流单元。一般情况下，基本块中会包含0个或多个指令，并且具有"一荣俱荣"的特性，即若是执行了基本块中的某条指令，则肯定会执行该基本块中的所有指令。

>另见[控制流图][control_flow_graph]。

<a name="benchmark_driver" />
## 基准测试驱动（benchmark driver）

基准测试驱动是指在基准测试中通过一台或多台机器来增加负载，然后在衡量基准测试目标操作的实际执行时间时，再将这部分工作时间排除在外的测试方式。

<a name="biased_locking" />
## 偏向锁（biased locking）

>另见[延迟解锁][lazy_unlocking]。

<a name="bytecode" />
## 字节码（bytecode）

字节码是由源代码转化成的、平台无关的二进制表示，就Java来说，字节码由Java源代码编译而成。Java字节码中包含了操作指令（长度为1个字节）和操作数，其结构化程度不如Java源代码，可以任意使用`goto`指令和其他Java源代码中不存在的结构，因此其表现力也远强于Java源代码。

<a name="bytecode_interpertation">
## 字节码解释执行（bytecode interpretation）

字节码解释执行是指，在虚拟执行栈中，以模拟字节码指令、虚拟机状态和本地变量表的形式来运行字节码代码。字节码解释执行的启动速递比编译执行快，但运行性能较低。

<a name="call_profiling" />
## 调用分析（call profiling）

调用分析是指在JIT代码中注入特定代码查看方法的调用频率或调用路径。收集到的调用分析主要用于做代码优化，例如找出应该将哪些方法做内联处理。

>另见[自适应代码生成][adaptive_code_generation]和[JIT][JIT]。

<a name="card" />
## 卡（card）

在本书中， 卡是一中数据结构，用于表示某块堆内存。整个堆内存被划分为多个卡，存储与卡表中。在分代式垃圾回收中，卡表用于判断老年代指定分区是否是脏的（dirty），即该区域中是否有对象包含有指向新生代中对象的引用。

>另见[写屏障][write_barrier]和[分代式垃圾回收][generational_garbage_collection]。

<a name="card_table" />
## 卡表（card table）

>另见[卡][card]。

<a name="class_block">
## 类块（class block）

类块是JRockit中的名词，指对象头中所指向的、包含了类型信息的数据块。

>另见[对象头][object_header]。

<a name="class_garbage_collection" />
## 类型垃圾回收（class garbage collection）

类型垃圾回收是指JVM对运行时中的类型信息进行清理。如果某个类已经被卸载了，而且没有`java.lang.ClassLoader`实例或其他代码引用该类或其方式时，就可以将其清理掉了。

<a name="client_side_template" />
## 客户端模板（client-side template）

JRockit Mission Control的客户端模板用于控制运行时记录的事件设置。解析改模板文件时，采用的全解析策略，即不支持通配符。模板文件可以带有版本信息。

>另见[事件设置][event_settings]和[服务器端模板][server_side_template]。

<a name="cloud" />
## 云（cloud）

云是指集中大量分布式计算资源（可能是虚拟计算资源），用户可以在其中部署自己的应用程序。

>另见[虚拟化][virtualization]。

<a name="code_generation_queue" />
## 代码生成队列

代码生成队列是JRockit中的一个词儿，为了保证Java应用程序的持续运行，JVM会先将代码生成请求放入到指定队列中，而后代码生成线程会从该队列中获取任务，执行代码生成任务，之后JVM再执行新生成的代码。

>另见[优化队列][optimization_queue]。

<a name="color" />
## 着色（color）

在本书中，着色是指对具有某种特性节点进行标记，常用于寄存器分配算法或引用追踪垃圾回收算法。

在寄存器分配算法中，同时正在使用的变量可以表示为图中的两个相邻节点，于是寄存器分配算法就可以转化为"如何对图中的节点进行着色，使相邻节点具有不同的颜色"，其中可用颜色的数量等于可用寄存器的数量。

此外，着色还可应用于引用追踪垃圾回收算法。通常情况下，标记-清理算法会使用若干种颜色来标记垃圾回收过程已经处理过的若干种对象。

>另见[寄存器分配][register_allocation]和[引用追踪垃圾回收][tracing_garbage_collection]。

<a name="compaction" />
## 内存整理（compaction）

内存整理可用于降低堆的碎片化程度。经过内存整理后，对象会被移动到一起，形成一块大的存活区域，消除内存碎片。对整个堆做内存整理操作，往往需要暂停应用程序线程。

>另见[碎片化][fragmentation]。

<a name="CAS" />
## 比较并交换（compare and swap, CAS）

目前很多CPU架构都支持原子指令，例如x86平台的`cmpxchg`指令和SPARK平台的`cas`指令，这种指令会比较内存和寄存器中的值，若相匹配，则用预设的某个值来覆盖内存中的值。如果覆盖成功，则该指令会设置标志寄存器，做分支处理使用。该指令常用于实现自旋锁。

>另见[原子指令][atomic_instruction]和[自旋锁][spinlock]。

<a name="compressed_reference" />
## 压缩引用（compressed reference）

引用压缩是一种Java对象模型的实现机制，在这种机制下，应用程序中对象的引用会比系统级的指针小。例如，在64位系统上，如果Java堆小于4GB，则记录对象地址只需32位就够了，在运行时中使用64位完全是浪费。载入/解压缩Java对象的指针会有一点开销（不过并不大），但却可以极大的提升系统的运行速度。

>另见[引用压缩][reference_compression]和[引用解压缩][reference_decompression]。

<a name="concurrent_garbage_collection" />
## 并发垃圾回收（concurrent garbage collection）

在本书中，并发垃圾回收是指在垃圾回收周期的大部分时间内，Java应用程序还可以继续执行的垃圾回收算法。

>另见[并行垃圾回收][parallel_garbage_collection]。

<a name="conservative_garbage_collection" />
## 保守式垃圾回收(conservative garbage collection)

保守式垃圾回收会将所有有可能是对象的内容都当作对象来处理，之所以这样是因为它不会记录对象的元信息。这种实现方式会降低垃圾回收的执行效率，因为没有元信息，垃圾回收器不得不做一些额外的检查。例如，数字17不是一个对象指针，因为它不在堆空间内，而数字0x471148则有可能是一个对象指针，但也有可能只是个常量值。如果某个常量碰巧指向了堆中的某个对象，则保守式垃圾回收很有可能会把这个常量也当作对象而保留下来。这些特性决定了保守式垃圾回收在移动对象时会受到很大的限制。

>另见[准确式垃圾回收][exact_garbage_collection] [活动对象图][livemap]和[安全点][safepoint]。

<a name="constant_pool" />
## 常量池（constant pool）

常量池是class文件中的一部分，其中存储了方法所使用到的常量字符串的较大的数字。

<a name="continuous_JRA" />
## 持续型JRA

持续型JRA，表示记录任务会一直持续运行，是早期开发JRA时的概念，后来JRA被JFR所取代。

>另见[JFR][JFR]。

<a name="control_flow_graph" />
## 控制流图（control flow graph，CFG）

控制流图是一种程序表示方式，在其中以图的形式展示了程序可能具有的执行路径（通常会以基本块作为节点）。图中节点之间的边可以表示直接跳转（如`goto`）、条件跳转、转换表（table switch）等，

>另见[偏向锁][biased_locking]。

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

>另见[胖锁][fat lock]和[活锁][livelock]。

<a name="deadlock_detection" />
## 死锁检测（deadlock detection）

死锁检测是JRockit Management Console的一项功能，用于检测系统中是否存在死锁的线程。

>另见[死锁][deadlock]。

<a name="design_mode" />
## 设计模式（design mode）

在运行JFR客户端时，设计模式是禁用的。通过设计模式可以直接访问构建用户界面的各种工具，自定义GUI界面，并将之导出为插件供他人使用。

>另见[运行模式][run_mode]。

<a name="deterministic_garbage_collection" />
## 确定式垃圾回收（deterministic garbage collection）

在本书中，确定式垃圾回收是指JRockit Real Time所使用的低延迟垃圾回收器。

>另见[延迟][latency]和[软实时][soft_real_time]。

<a name="diagnostic_command" />
## 诊断命令

通过JRCMD、MBean`DiagnosticCommand`或JMAPI可以给JRockit JVM发送指定的诊断命令。

>另见[JRCMD][JRCMD]和[JMAPI][JMAPI]。

<a name="double_checked_locking" />
## 双检查锁（double-checked locking）

在双检查锁中，在获取锁之前会先进行一次检查是否满足条件，以期避免执行开销较大的加锁操作。强烈建议不要使用这种"技巧"，在某些内存模型下，这种"技巧"可能具有不同的行为，甚至是错误的行为。

>另见[Java内存模型][JMM]。

<a name="driver" />
## 驱动程序（driver）

>另见[基准测试驱动][benchmark_driver]。

<a name="editor" />
## 编辑器（editor）

编辑器是富客户端平台（RCP）的基本概念，在GUI中，它通常位于RCP应用程序的中间部分，展示相关数据。

>另见[富客户端平台][RCP]。

<a name="escape_analysis" />
## 逃逸分析（escape_analysis）

逃逸分析是一种代码优化手段，用于判断指定对象的作用域，并在可能情况下移除不必要的对象。如果编译器能证明，对象的作用域之间某个有限范围内，绝对不会"逃逸"出这个范围（例如某个对象是作为参数被传入到方法中），则编译器就可以省去为对象分配内存的操作，直接将对象属性保存到局部变量。逃逸分析与C++中在栈中分配对象有异曲同工之妙。

<a name="event" />
## 事件（event）

在JRA延迟分析工具和JFR中，事件是与某个时间点相关的数据集合。事件可以有持续时间属性和事件类型属性。

>另见[事件类型][event_type]。

<a name="event_attribute" />
## 事件属性（event attribute）

事件包含了一系列属性-值得组合，事件属性也称为事件域。

>另见[事件域][event_field]。

<a name="event_field" />
## 事件域（event field）

>另见[事件属性][event_attribute]。

<a name="event_settings" />
## 事件配置（event settings）

事件配置包括事件类型、阈值和是否记录调用栈等内容。

>另见[客户端模板][client_side_template]和[服务器端模板][server_side_template]。

<a name="event_type" />
## 事件类型（event type）

事件类型用于描述JFR中的事件，包含了与事件域、事件路径、事件名和描述等元信息。事件类型和事件的关系就好像是类和实例的关系。

<a name="exact_garbage_collection" />
## 准确式垃圾回收（exact_garbage_collection）

与保守式垃圾回收相反，准确式垃圾回收要求运行时提供元数据信息，以便明确知道寄存器和栈帧中的哪些位置存储了对象指针，这样就免去了垃圾回收器猜测数据到底是不是对象指针的麻烦。元数据虽然增加了内存消耗，却可以加快垃圾回收的执行速度，并提升回收操作的准确性。

>另见[保守式垃圾回收][conservative_garbage_collection]。

<a name="exact_profiling" />
## 准确分析（exact profiling）

准确分析是指以注入代码的形式来获取准确的分析结果，例如方法执行时间和方式执行次数。这种方式通常都会带来一点性能开销。

>另见[采样分析][sample_based_profiling]。

<a name="extension_point" />
## 扩展点（extension point）

在Eclipse Equinox(OSGi)中，插件可以通过扩展点为应用程序增加新功能。例如，在JRockit Management Console中，第三方插件可以通过扩展点来增加新的标签页。

<a name="fairness" />
## 公平性（fairness）

若是系统的中的线程获得时间片的几率相同，则称之为公平调度。对于具体的应用程序来说，公平调度并不是必需的，因为频繁的上下文切换回带来不小的性能开销，不过需要线程能够均等运行的场景中却是非常重要的，

<a name="fat_lock" />
## 胖锁（fat lock）

相对于瘦锁，胖锁更加智能，实现也更加复杂。当线程在等待获取锁的时候，胖锁会将线程置于休眠状态，并为等待线程维护一个优先级队列。胖锁可以降低对CPU资源的消耗，因而更适用于那些竞争激烈或持有时间很长的锁

>另见[瘦锁][thin_lock]。

<a name="fragmentation" />
## 碎片化（fragmentation）

碎片化是内存分配行为和可分配内存的恶化，其成因是对象被垃圾回收器回收后在内存空间中留下无法再被使用的空洞。如果堆中的空洞非常多，而又非常小，此时即便空闲内存不少，但却有可能无法再为新对象分配内存了。碎片化是现代垃圾回收器天敌之一，不少垃圾回收器通过内存整理来解决碎片化问题。

>另见[内存整理][compaction]。

<a name="free_list" />
## 空闲列表（free list）

空闲列表是运行时用来记录堆中可用空间的数据结构。通常情况下，空闲列表会指向堆中那些可以容纳新对象的空洞，其具体结构可能是针对固定大小区域块的优先级队列。在为对象分配内存时，会在对应大小的空闲列表中查找合适的空闲块。

>另见[碎片化][fragmentation]。

<a name="full_virtualization" />
## 全虚拟化（full virtualization）

全虚拟化是指客户应用程序无需任何修改就可以直接运行在虚拟机中，就像运行在物理硬件上一样。

>另见[虚拟化][virtualization]和[客户应用程序][guest]。

<a name="GC_heuristic" />
## 启发式GC（GC heuristic）

启发式GC是指一组规则，例如吞吐量和暂停时间，用于确定如何对垃圾回收器进行配置。

>另见[GC策略][GC_strategy]。

<a name="GC_pause_ratio" />
## GC暂停时间比例（GC pause ratio）

GC暂停时间比例是JRockit Mission Control中的一个概念，是指运行应用程序代码和暂停应用程序运行垃圾回收代码的时间比例。需要注意的是，应用程序运行时间指的是总体运行时间，可能会包含将数据写入到硬盘的延迟时间。

<a name="GC_strategy" />
## GC策略（GC strategy）

在JRockit垃圾回收器中，尤其是R27版本之前的垃圾回收器中，GC策略通常是指符合某种启发式GC规则的垃圾回收器行为。在JMAPI中，GC策略包含以下三种定义：

* 新生代行为（开/关）
* 标记阶段行为（并行/并发）
* 清理阶段行为（并行/并发）

>另见[启发式GC][GC_heuristic] [并行垃圾回收][parallel_garbage_collection]和[并发垃圾回收][concurrent_garbage_collection]。

<a name="generation" />
## 代（generation）

代是堆的一部分，通常情况下，对象会按其年龄（所经历的垃圾回收次数）存放到指定的代中。

>另见[堆][heap]和[分代式垃圾回收][generational_garbage_collection]。

<a name="generational_garbage_collection" />
## 分代式垃圾回收（generational garbage collection）

分代式垃圾回收是指将堆划分为多个区域，或称"代"。新生代（即young generation或nursery）通常比较小，执行垃圾回收的频率较高，相比于老年代来说，垃圾回收的执行速度也较快。当系统中大部分对象的生命周期都很短时，分代式垃圾回收就很适用。不过，分代式垃圾回收也会带来一些执行开销，垃圾回收器需要记录下老年代中哪些对象包含有指向新生代对象的引用。

>另见[新生代][young_space] [老年代][old_space]和[写屏障][write_barrier]。

<a name="graph_coloring" />
## 图着色（graph coloring）

在寄存器分配算法中，图着色算法用于计算寄存器赋值问题。同时使用的变量被抽象为图中相邻的两个节点，寄存器分配器的工作就是，在相邻节点不能同色的前提下，用尽量少的颜色画满途中所有的节点。如果最后计算出所需颜色的数量大于可用寄存器的数量，则需要使用Spilling技术来处理。作为一个NP-hard问题，虽说图着色问题可以求出近似解，但仍是代码生成过程中计算量最大的生产步骤之一。

>另见[着色][color] [寄存器分配][register_allocation] [图融合][graph_fusion]和[Spilling][spilling]

<a name="graph_fusion" />
## 图融合（graph fusion）

图融合是对图着色的扩展。通过某些启发式算法（通常情况下是根据代码块的热度），将IR分拆为几个子区域，然后分别对每个子区域进行着色，再做融合操作。这个过程需要在相邻子区域之间的边上生成一些额外代码来记录关联关系。如果作为划分标准的热度的尺度足够高，处理代码时可以直接从最热的部分开始，那这个算法就非常有用了，可以少生成一些额外的代码了。

>另见[着色][color] [寄存器分配][register_allocation] [图着色][graph_coloring]和[Spilling][spilling]。

<a name="green_thread" />
## 绿色线程（green thread）

绿色线程是指用一个底层线程实例（例如一个操作系统线程）来表示多个高层线程实例（例如`java.lang.Thread`对象）。对于没什么复杂性的应用程序来说，这个实现方式简单有效，但却有很有弊端，最大问题就是多线程处理。在本地代码中，无法对线程施加控制，没法得知线程正在等待IO，因此可能会出现死锁的情况。如果将绿色线程置于休眠状态，通常会将其底层的操作系统线程也一起休眠了，导致该操作系统线程所代理的其他绿色线程都无法运行了。

>另见[多对多线程模型][NxM_thread]。

<a name="guard_page" />
## 保护页（guard page）

保护页是内存管理中的一个特殊页，带有操作系统级页保护标志位。因此，对该页做解引用操作时，会抛出异常。这个特性非常有用，将保护页置于栈结构的底部时，可用于检查是否发生栈溢出。此外，还可以用保护页实现安全点，对指定安全点解引用所涉及的页面加以保护即可。这样，当下一次到达安全点时，运行时就会抛出一个异常，终止控制流。

>另见[活动对象图][livemap]和[安全点][safepoint]。

<a name="guest" />
## 客户应用程序（guest）

运行在虚拟机管理程序上的自包含的系统，例如操作系统，被称为客户应用程序。多个客户应用程序可以运行在同一个虚拟机管理程序中，只不过在全虚拟化下，客户应用程序会认为自己是直接运行在物理机器上，并不会意识到有其他客户应用程序存在。

>另见[虚拟化][virtualization]和[虚拟机管理程序][hypervisor]。

<a name="hard_real_time" />
## 硬实时（hard real-time）

硬实时是指运行环境对实时性的要求很高，需要精确控制延迟时间。对于Java服务器端应用程序来说，通常来说这没必要，软实时就够了，即控制延迟等级水平即可，无需精确控制延迟时间。

>另见[软实时][soft_real_time]。

<a name="hardware_prefetching" />
## 硬件预抓取（hardware prefetching）

硬件预抓取是一种基于硬件的预抓取实现，通常情况下，是指CPU无需与应用程序交互，通过启发式算法，在访问数据之前，预先将目标数据抓取到缓存中。

>另见[预抓取][prefetching]和[软件预抓取][software_prefetching]。

<a name="heap" />
## 堆（heap）

在本书中，堆是指JVM中预留的、专用于存储Java对象的内存空间。

>另见[本地堆][native_memory]。

<a name="HIR" />
## 高级中间表示（HIR，high level intermediate representation）

HIR是JRockit中将字节码转换为本地代码过程中的首份产出。JRockit HR是一个以基本块作为节点的有向控制流图，每个基本块都包含0个或多个操作。JRockit HIR是平台无关的。

>另见[MIR][MIR] [LIR][LIR] [IR][IR] [寄存器分配][register_allocation]和[本地代码][native_code]。

<a name="hosted_hypervisor" />
## 托管型虚拟机管理程序（hosted hypervisor）

托管型虚拟机管理程序是指，在当前操作系统中，作为一种用户应用程序来运行的虚拟机管理程序。

>另见[虚拟机管理程序][hypervisor]。

<a name="hypervisor" />
## 虚拟机管理程序（hypervisor）

虚拟机管理程序是一种允许多个操作系统（也称为客户应用程序）同时运行在一台物理机器上的应用软件，可以为客户应用程序提供硬件抽象。

>另见[虚拟化][virtualization] [客户应用程序][guest] [本地型虚拟机管理程序][native_hypervisor]和[托管型虚拟机管理程序][hosted_hypervisor]。


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
[design_mode]:                      #design_mode                        "设计模式"
[run_mode]:                         #run_mode                           "运行模式"
[deterministic_garbage_collection]: #deterministic_garbage_collection   "确定式垃圾回收"
[latency]:                          #latency                            "延迟"
[soft_real_time]:                   #soft_real_time                     "软实时"
[diagnostic_command]:               #diagnostic_command                 "诊断命令"
[JRCMD]:                            #JRCMD                              "JRCMD"
[JMAPI]:                            #JMAPI                              "JMAPI"
[JMM]:                              #JMM                                "Java内存模型"
[double_checked_locking]:           #double_checked_locking             "双检查锁"
[driver]:                           #driver                             "驱动程序"
[editor]:                           #editor                             "编辑器"
[RCP]:                              #RCP                                "富客户端平台"
[escape_analysis]:                  #escape_analysis                    "逃逸分析"
[event]:                            #event                              "事件"
[event_type]:                       #event_type                         "事件类型"
[event_attribute]:                  #event_attribute                    "事件属性"
[event_field]:                      #event_field                        "事件域"
[event_settings]:                   #event_settings                     "事件配置"
[exact_profiling]:                  #exact_profiling                    "准确分析"
[sample_based_profiling]:           #sample_based_profiling             "采样分析"
[extension_point]:                  #extension_point                    "扩展点"
[fairness]:                         #fairness                           "公平性"
[thin_lock]:                        #thin_lock                          "瘦锁"
[free_list]:                        #free_list                          "空闲列表"
[GC_strategy]:                      #GC_strategy                        "GC策略"
[GC_heuristic]:                     #GC_heuristic                       "启发式GC"
[GC_pause_ratio]:                   #GC_pause_ratio                     "GC暂停时间比例"
[generation]:                       #generation                         "代"
[heap]:                             #heap                               "堆"
[young_space]:                      #young_space                        "年轻代"
[old_space]:                        #old_space                          "老年代"
[graph_coloring]:                   #graph_coloring                     "图着色"
[spilling]:                         #spilling                           "Spilling"
[graph_fusion]:                     #graph_fusion                       "图融合"
[green_thread]:                     #green_thread                       "绿色线程"
[NxM_thread]:                       #NxM_thread                         "多对多线程模型"
[guard_page]:                       #guard_page                         "保护页"
[hard_real_time]:                   #hard_real_time                     "硬实时"
[soft_real_time]:                   #soft_real_time                     "软实时"
[hardware_prefetching]:             #hardware_prefetching               "硬件预抓取"
[prefetching]:                      #prefetching                        "预抓取"
[software_prefetching]:             #software_prefetching               "软件预抓取"
[native_memory]:                    #native_memory                      "本地堆"
[MIR]:                              #MIR                                "中级中间表示"
[HIR]:                              #HIR                                "高级中间表示"
[LIR]:                              #LIR                                "低级中间表示"
[native_code]:                      #native_code                        "本地代码"
[hosted_hypervisor]:                #hosted_hypervisor                  "托管型虚拟机管理程序"
[native_hypervisor]：               #native_hypervisor                  "本地型虚拟机管理程序"