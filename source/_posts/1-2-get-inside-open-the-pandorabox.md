---
title:  2.深入了解：打开潘多拉魔盒
date:  2017-05-01 18:43:20
categories:
- 1 Chapter
tags: 
- 计算机基础
- 硬件
- CPU
- 处理器
- GPU
- 显卡
- 内存
---

&emsp; 啊哈，又见面了。很有趣的标题：潘多拉魔盒。计算机有那么可怕么？当然了！年轻人千万不要碰的就是：吸烟，喝酒，吸毒，编程，单反和HiFi了。（笑cry）

&emsp; 俗话说：单反穷三代，编程毁一生。作为一个喜欢摄影，又热爱编程，还特别喜欢在耳机，解码器，耳放这类HiFi设备上面烧钱的我来说，简直就是感同身受。不过好在我并不是一个纯粹的程序员（不然你们也见不到这个项目了），也不是一个纯粹的摄影家，也不是一个纯粹的音乐制作人，也不是一个纯粹的DJ，也不是一个纯粹的人.......(咳咳，打住，打住！)

&emsp; 所以说，电脑就是一个潘多拉魔盒，打开它就给我们带来无穷无尽的.................快乐！！！谁让它那么好玩的，至于什么近视了，还有辐射了，这都无所谓了（PS：其实这些都是玄学，23333，懂一点科学的人就知道这些是真的还是假的，为了不被喷，我就不明说了，不过颈椎病这个是真的。。。）。

&emsp; 所以，接下来，我们就要打开，不，拆开，这个潘多拉魔盒了！

# 打开潘多拉魔盒

## 乱入的黑箱

&emsp; 在开始之前，我想向大家介绍一下“黑箱”这个概念，为什么要介绍这个乱入的概念呢？因为我们平常使用的电脑（可能有人会发现我计算机和电脑换来换去的，在需要正规用计算机的地方我会用计算机，在闲谈的时候我就看心情。。），手机或者平板，都是黑箱：我们并不知道它们内部长什么样，也不理解它们是怎么运行的，但并不影响我们使用它们，这就是黑箱。

&emsp; 简单说，黑箱就是一种装置或者设备，我们在不了解内部构造，也不理解其内部运行原理的时候，也可以无障碍的控制和使用。

## 上节回顾

&emsp; 上一节，我们从词典的角度，认识了计算机。这是一种纯粹（又TM说纯粹！！！）的计算机 ：以二进制形式，根据程序的指令，存储和处理数据的一种电子设备。这只是对计算机原理的基本功能的描述。这也是计算机最开始被发明的目的：进行**运算**。

&emsp; 那么，计算机是通过什么来进行计算的呢？

## CPU：计算机的运算核心


&emsp; 随着这几年某些国产手机品牌大打“**性能牌**”，大家可能会对处理器，内存这些名词有一些概念，不过我敢保证，你看完本章（不是本节），你就知道这些你们天天跪舔的一些国产机厂商是怎么忽悠你们的了！！（我知道我写这一句话之后，会有很多人喷我，不过无所谓，我就是要写出来。）

&emsp; 提到计算机的计算功能，就不能不提到CPU，（即 Central Processing Unit）中央处理器，也经常被简称成处理器。

&emsp; 什么是处理器呢？

&emsp; 简单来说，处理器是一种黑箱，是一种按照人的意愿进行特定计算的计算机元件。之所以叫元件，因为它并不能独立工作。（实际上计算机中大部分的元件，或者说是硬件，都没办法独立工作，所以在维修硬件问题的时候会搭建“最小系统”这类环境，让一些必须工作的硬件工作，测试系统是否正常。）

&emsp; 为什么处理器不能独立工作呢？这就需要对它的原理有一定了解，首先，因为我们本阶段并不会实际的对CPU进行操作（虽然每一行我们写的代码都需要CPU处理，但是我们并没有真正的去控制CPU，这都是C，编译器，系统帮我们实现的），所以我不会过于深入的介绍CPU的原理。

&emsp; 关于处理器的原理，处理器的英文缩写 CPU 是 Central Processing Unit 的缩写，这里面出现了Unit，实际上CPU就是由很多单元组成的。下图（来源：http://www.webopedia.com/TERM/C/CPU.html）就展示了CPU的基本结构。
![CPU结构](http://www.webopedia.com/imagesvr_ce/4966/cpu-diagram.gif)

&emsp; CPU是一种分层结构，在上层，运算和控制层，分为ALU和CU，分别是逻辑运算单元和控制单元，逻辑运算单元负责一些计算工作，控制单元负责把内存中的指令解码和执行，并且在必要的时候调用ALU，下面是内存单元内存单元包括RAM，ROM和cache，事实上，CPU只包含cache，但是可以通过一些方法控制这三者。RAM和ROM会在后面讲解，cache如果有必要会简单说一下。

&emsp; 看了上面一堆，可能你并不清楚究竟发生了什么，如果还要简单来说的话，那就是CPU主要是从内存读取数据和指令，然后进行运算后再传回内存的一种计算机硬件，看到这里你可能很惊讶，我下载的软件实际上是在硬盘啊，并不是内存啊！这个，等我们了解了硬盘和内存之后就明白了。

&emsp; 虽然了解了CPU的基本原理，可是我们并不知道各种宣传中所谓的GHz这个概念，这个概念很好理解（简单理解），Hz是频率的单位，频率就是1s钟内某种活动完成了多少个周期，比如你跳绳1分钟跳了120个，一秒钟2个，你跳绳的频率就是2 Hz。既然谈到了G，就在这里说一下计算机的计数方法吧。

&emsp; 常见的计算机数量单位从小到大可分为 b(小写) B(大写) KB MB GB TB PB ... 可能有很多朋友看到网络带宽的广告写着可以达到100Mbps（这里的ps是per second的意思就是/s的英文说法）认为一秒钟最快可以下载100MB的数据，然而实际上最快也不过12MB/s多一点，这就是大写B和小写b的区别，大写B是Byte （字节）的缩写，而小写b是 bit（比特，也就是一个二进制位）的缩写，按照规定 8 个bit位表示一个Byte字节，也就是 8 bits = 1 Byte ，所以100Mb = 12.5 MB ，8 秒才能下载100MB的数据，至于KB ，K在英语是kilo的缩写，在汉语中就是千的意思，然而实际上，1 KB = 1024 B ，也就是说，这并不是十进制的千，那这1024怎么出来的呢？（我知道有的人一看到1024就兴奋。。。别那么明显，2333），如果你还记得二进制的内容，那么你可以计算一下 2 的 10 次方，你会发现这正好是1024，所以实际上1 KB = 2 ^ 10 B，同理 1 MB = 2 ^ 10 KB ， 1 GB = 2 ^ 10 MB.....
实际上并不是只有这些单位，根据摩尔定律，存储容量会越来越大。（当然，根据物理学角度，单位存储容量最后会达到一个定值。）

&emsp; 说完了单位换算，我们可以继续回到这个GHz的问题了，现在你知道这个GHz就是CPU在一秒内完成了某个周期多少G次，实际上这个周期就是CPU周期，就是处理器执行一条指令所用的时间，当然这个指令不是指任何指令，而是CPU内部的指令，我们写的程序最终都会被翻译成这样的指令。不同的处理器这种内部指令是不同的，这也造成了手机和电脑处理器的差异，电脑的处理器是通用处理器，很多复杂的运算可以在一个CPU周期内完成，手机的处理器是RISC类处理器，精简了很多内部指令，这样的好处是，处理器的尺寸，功耗都可以大规模减小，弊端就是，电脑处理器一个CPU周期内完成的运算，手机处理器需要调用几种内部指令来进行“等效”，这样性能就被大打折扣，所以，不要幻想着手机处理器吊打电脑处理器了，就算现在的手机处理器发展很快，可是电脑处理器也在不断发展啊。

&emsp; 还有一个问题，就是核心数和线程。先说说核心数：随着激光技术的进步，芯片生产工艺越来越高，这意味着我们可以在与原来同尺寸的处理器里面放入更多的元件，但随着发展的深入，人们发现时钟频率已经发展到了一个水平，进一步的提升需要很高的成本提升却很少，于是乎“多核心”这个概念进入了人们的视野，为什么不在一个处理器的空间中装入“更多的处理器”呢？由此，多核处理器就诞生了。

&emsp; 事实上，在多核处理器出现之前，就已经有在一个主板上安装多个处理器的技术了。多核心处理器实际上与这类似，理论上，多核心处理器的运算性能可以达到单核心的2倍，然而由于程序编写的问题，以及其他硬件的制约，往往只能提升到原来的70%，但是，多核在很大成都上增加了计算机的处理速度，比如说，在以前的单核心处理器上，计算机在一个处理器周期内只能处理一个指令，也就是只能做一种工作，比如，一个处理器只能对音频文件进行解码，而不能做其他操作，你不能同时进行文字处理。不过事实上，在单核处理器流行的时候，人们也可以通过计算机进行多任务操作，可以一般听音乐一边进行文字处理，这是因为计算机的处理速度很快，可以通过在不同的程序之间快速切换来实现多任务。但处理器的速度就那么大，也许做一些简单的工作的时候，没有感觉到性能不足，假设你同时复制两个文件呢，速度会是复制一个文件的两倍么？

&emsp; 但多核处理器可以在与软件良好结合的情况下，处理这些多任务问题，所以更多的核心理论上可以提供更强的运算能力，但实际上能力的发挥不仅仅取决于处理器，还需要软硬件之间的协调。

&emsp; 下面说一说线程，线程实际上是一个复杂的概念，如果以现在所学的知识理解就是一个运行中的程序（不过实际上程序可以有很多线程），运行中的程序也被成为进程，实际上线程就是进程的实际运作单位。

&emsp; 我们在上面知道在任意一个时刻，CPU的一个核心只能运行一个进程，处理器中又有很多的运算单元，这个进程会使用其中一些运算单元进行一些运算工作，这些被使用的，正在工作的运算单元就是线程，如果把处理器看作一个工厂，进程就是工厂的客户，要求工厂做一些工作，工厂里面有很多工人，其中一些去完成这个客户的需求，这些工人就是线程。
所以大多数处理器内核数是等于线程数的，也就是某一时刻处理器最多可以完成的工作数量。

&emsp; 但是从上面不难看出，无论是处理器的运算单元，还是工厂里面的工人，总会有闲着的，万恶的资本家看到心里这个难受啊！！！所以万恶的资本主义科学家（哈哈哈哈，我自己都笑了）发明了超线程技术，就是如果在某一时刻，其他的进程需要的运算单元正好处于空闲状态的时候，可以同时进行运算，这样一个工厂做了两个工作，但是却没有增加内核的数量，利用了空闲的资源。不过实际上，由于程序算法的复杂性，超线程技术并不是很好用。而且市面上支持超线程的处理器比较少，低端的有atom类的处理器，单核心双线程，高端的有i7处理器一般都是四核心八线程，马上，下面要划重点了！！！

&emsp; 有很多电脑城的JS（奸商）用超线程的处理器冒充多核处理器，比如原本四核心的处理器说是八核心的，由于超线程本质是同一个核心，所以在任务管理器的CPU占用率页面，同一核心的资源占用率是相同的，很容易就看出来，曲线都是一样的。所以。。。。当然了，个人觉得买电脑，没必要去实体店。关于选购电脑这个以后再说吧。

## 硬盘：懒惰娇贵又忠诚的史官

&emsp; 本来想先将内存的，但是想了想，还是先聊聊硬盘吧，然后在说说内存和缓存。

&emsp; 硬盘，有一些对计算机有一些浅显了解的人，觉得硬盘就是外存或者ROM，觉得外存和ROM就是硬盘，然而事实上并不是这样，尤其是一些手机上面宣传的ROM就更说不过去了。

&emsp; 按照惯例，我吐槽完就该说点干货了，那么，什么是硬盘呢？为什么我给它这么一个绕嘴的拟人呢？因为这很符合它啊～且听我慢慢道来。

&emsp; 上节在介绍二进制的时候我说过，硬盘是通过磁性物质的磁极排列来存储数据的，但是这只是硬盘主要功能的一个抽象。实际上，硬盘是我们大多数数据的“家”，我们想要保留的数据最终都被存到了以硬盘为首的“外存”设备中了。

&emsp; 先说说为啥我说它“懒”，其实我也挺惭愧的，怎么能有比我懒的人，更何况这是一个机器！这个懒是相对说的，相对于我们么？当然不是，目前的常见的硬盘（SATA3 标准 7200转速的硬盘）一分钟记录的内容，不知道我们要记多久呢。所以这个“懒”是相对与计算机的某个硬件来说的，是什么呢？当然是我们唯一学习的一个硬件CPU了～ 我们知道处理器的执行速率已经到达了GHZ的程度，实际上这个速度在多年前，单核心处理器的时候就已经达到了，何况现在都是多核心处理器。（当然了，就算CPU满载每秒钟处理几G条处理器指令，也不意味着这些指令都来自硬盘，就是说，他们不是一一对应的关系，就好比，让一个人计算12的阶乘，题目很简单，但是需要很多次运算（执行很多指令），题目很短（程序很小），因为阶乘的方法（就好比处理器的计算单元）已经在人的脑中。）然而目前主流的SATA 3.0标准最大传输速度也不过600MB/s，也就是说如果处理器在运算的时候突然要从硬盘查点数据，按照处理器的急性子，它都要急死了，所以它很懒，正因为如此，为了解决CPU和硬盘之间巨大的速度落差，人们增加了“内存”这个中间介质，来缓冲。

&emsp; 然后再说说为啥它娇贵。因为硬盘是园的（实际上只是盘片是园的，这个下节再说），这不由得让人想到唱机。

![唱机](http://img.guitarchina.com/img2016/0129ty/45.jpg)
（图自http://img.guitarchina.com/img2016/0129ty/45.jpg）

&emsp; 硬盘实际上也是类似的原理，只不过磁头和盘片是不接触的，盘片在高速的旋转，常见的有每分钟5400 转每秒，或者7200 有的甚至可以达到1万以上，所以在硬盘运行的过程中，晃动 震动或者抖动都会导致磁头和盘片接触，然后就，噗次卡嚓，稀里哗啦....额，你们脑补一下车祸现场吧.......然后硬盘就挂掉了，所以它很娇贵。

&emsp; 至于忠诚嘛。虽然硬盘这么娇贵，然而实际上，硬盘是最可靠且安全的存储媒介，你们肯定不知道，其实你们手机里面的数据长时间不通电使用，数据是会慢慢消失的，而且超不过十年！同时大多数存储设备，比如SD卡（包括不仅限于MicroSD SDHC SDXC），可擦写的光盘，u盘（也有叫闪存盘的）都是有读写次数寿命的，一般几千次到几百万次不等。但是硬盘却可以在正常家用的情况下使用十余年不出现损坏的情况（大多数），而且数据也不会丢失，所以它绝对够忠诚！

&emsp; 至于史官嘛，硬盘记录了你很多的信息，如果进行数据挖掘，你用了多久电脑都可以看出来，暂且不说这些，你平常下载到电脑的视频图像，音频文档，都是保存在硬盘的。所以这个官分给再在合适不过了。

&emsp; 这就是硬盘的简单描述，其实说了这么多啥也没讲，连个硬盘的图都没有，我写的时候也考虑过这个问题，这节就是给大家简单的建立一个电脑各硬件的概念，至于深入的研究，我们在下节课探讨。

## 内存：勤劳的坏脑子

&emsp; 说到内存，我感觉我就和它一样，勤劳！哦，不是，我和它一样记性不好........

&emsp; 内存，上面说过是为了解决CPU和硬盘之间巨大的速度（也可以说成是性能）落差而安装到电脑上的中间介质，这也就意味着它有两个显而易见的特性：

 - 速度快.
 - 实际不具有存储数据的功能.
 
 &emsp; 内存实际上是很多设备的统称，实际上内存是内部存储器的说法，但是在应用中，为了方便表述我们的内存就是解决CPU和硬盘之间巨大的速度落差的硬件，也就是常说的内存条，也是常说的RAM。
 
&emsp; 似乎又到了英语课的时间，上课之前闲扯一会吧～ 英语，我觉得计算机科学中最重要的知识，涉足这个领域，可能你最开始对数学了解不多，可能未接触过线性代数，但是，一定不能让英语成为你的短板，学会了英语就掌握了获取新的信息和知识的钥匙，就算数学类学科限制了你的研究，你也可以很快在一些渠道找到学习的资料，这些资料往往是英文的。你可能会说，我可以找中文版啊。这的确是个方便的方法，但，你如何保证翻译的准确性和正确性呢？同时，有一点我不得不说的，虽然，我在开头介绍计算机的时候，根据字典的意思，翻译过来，介绍计算机，但是我并不建议把所有的计算机术语都翻译成中文，因为实际上很多术语就是来自于生活中的英文单词，幽默风趣又浪漫的外国科学家给他们的新理论，新功能赋予了一个和它们相似的生活中的词语，然而我们翻译要讲究信达雅，有时候甚至歪曲了本意，造成很多国内的资料看起来晦涩难懂。之所以我用了翻译的方法介绍计算机，只不过是一个引子的作用，而且在以后的内容中，我也只会解释一些有清晰意思的英文术语。

 &emsp; RAM : Random-Access Memory 是随机访问存储器的缩写，之所以是随机的，是在程序进行请求的时候的内存地址是随机的，这个在讲解指针的内容会具体说明，我们简单的说说内存吧！

&emsp; 前面说过，指令是存在内存里面的，所以，实际上，当你运行一个程序的时候，程序被从硬盘读出，复制到内存中（这个过程就是传说中的加载，也是英文给枪装弹的load的意思），然后处理器从内存中读取指令和所需的数据，这里不得不提到大名鼎鼎的 冯 诺依曼 体系 了，在前面的内容中，我总是说，内存里面包含指令和数据，你可能在想（很可能你根本没注意到）指令和数据是不是互相分离的，并且有专门的办法区分，当然有办法区分，不然我为什么说是指令和数据，但是只是对于人来说，就算程序可以区分指令和数据，那也是人编程的结果，实际上，对于计算机，指令和数据是没有区别的，都只是一堆二进制位罢了，这就是冯诺依曼体系，对于计算机，数据和指令是没有区别的，处理器通过特殊的寄存器（一种特殊的存储数据的结构），来确定要执行指令的在内存中的位置。这个体系造就了计算机，同时这个体系也给计算机造成了无穷无尽的灾难--漏洞，就是因为数据和指令的无区别性，可以通过一些特殊方法让恶意构造的数据被当作指令执行，从而在系统中打开后门。

&emsp; 不过，你可能很好奇，我下载的十多个甚至几十GB的游戏，运行的时候也没有装满我几个G的内存啊！当然不会装满，首先，你运行的游戏程序并不是很大，加载的只是这个主程序和一些必要的资源文件。其次，这类程序通常有很高级的内存管理机制，可以动态的使用和释放内存，而不是一次性都加载到内存中。所以几个G的内存并不会完全被很大的程序占满。

&emsp; 之前我们说过，内存是为了解决硬盘和处理器之间巨大的性能落差而增设的。那么，内存的速度够和处理器平起平坐了么？当然不够！不然，为什么还有一个我还没有提及的缓存的存在？所以，缓存是什么？可能有一些机智的读者已经猜到了。对，它就是解决处理器和内存之间的性能落差的。缓存通常很小，但速度很快，被封装在内存中用于存储一些急需访问的数据。这个以后有机会再详细的说一说吧～

## 显卡 ：热爱三角形和并行运算的计算狂魔

&emsp; 很多人都知道GPU或者显卡，并且知道这个东西是计算机或者手机平板之类设备游戏性能的主要贡献者。但是却不知道它究竟是何物。下面我们就来揭开显卡神秘的面纱吧～

&emsp; 显卡(Graphics card) 准确来说应该是 图形显示卡，是一直安装在计算机主板（稍后会提到）上的一种显示信息转换从而驱动显示器显示信息的设备。这也是显卡最开始被发明的目的：在终端命令行界面发展到一定程度之后，出现了图形化的界面，然而CPU的处理能力不足以支持可视化界面的渲染，所以科学家发明了最早的显卡--“图形加速卡”，后来随着芯片的制作工艺的发展，显卡的发展空间也越来越大，由此出现了“3D加速卡” 等更大处理能力的显卡。

&emsp; 所以，你可能要问：显卡是不是可以取代CPU？目前来讲不太可能（只是目前来讲，谁知道未来会发展成什么鬼样子）这就得说说GPU了，就是显卡的“CPU”（当然这种说法不正确，只是一种比喻），GPU （graphics processing unit） 图形处理器，GPU使显卡减少了对CPU的依赖，并分担了部分原本是由CPU所担当的工作，尤其是在进行3D图形运算的时候。GPU就是显卡的运算核心，至少从1999年8月NVIDIA公司发布Geforce 256之后到今天已经一段时间之内是这样，简单来说目前的显卡就是GPU和显存（显卡专用的内存，性能往往比同时期的内存高很多）还有风扇之类的散热器还有一些负责图像输出之类的芯片和电路组成的。

&emsp; 正因如此，显卡不仅仅以“卡”的形式存在，比如现在的超级本或者手机平板，都有很强的图像处理能力，然而这些设备的尺寸都不足以容纳一张显卡。因为这些设备的“显卡”或者说图形运算设备，都是集成的，或者常说的板载的，也有说是集显（实际上这只是针对超级本或者一些笔记本，平板和手机并不是这样的），这些设备的GPU被集成到了主板上，集成
的好处就是，可以大幅度的减小设备的尺寸，但是目前，因为我们还没能实现让某一事物尽善尽美，所以这样做也是有很大代价的，就是GPU的性能被缩水，而且由于没有足够的空间放置显存（当然我这是比较委婉的说法，大多数的真实情况是为了节约成本），通常GPU的显存由系统的内存共享，就是分出一部分的内存给显卡当作显存，这样不仅仅制约了GPU性能的发挥（实际上这个制约不是很大，因为集成的GPU本身的性能就不是很强），同时由于需要共享内存，使得系统实际的内存被减少，同时集成以为着永久固定在电路板上，除非更换整块主板，不然没有办法升级显示核心。

&emsp; 当然还有一种新的GPU存在形式，就是把GPU和CPU做在一起，现在很多的低端电脑都是采用这种方案。手机平板几乎都是采用这种方案，这种封装方式的显卡被称为“核显”。

&emsp;  回到刚才的问题：为什么目前GPU没办法替代CPU，因为GPU也是一种RISC，并不是为通用计算设计的。所以目前GPU，并不能完全做CPU的工作，但是GPU不同于CPU，具有数百或者数千个处理单元（内核），可以并行运算大量计算。

&emsp; GPU因为在游戏中的3D渲染而出名，这里就简单说一下游戏的渲染，其实，显卡的3D渲染就是在快速的生成大量的三角形，密密麻麻的三角形，组成了我们看到的各种各样的具有立体感的画面，同时GPU在数据分析，深度学习，机器学习也有得天独厚的优势，GPU允许某些计算比传统CPU上运行相同的计算速度快10倍至100倍.

## 声卡：电子“金嗓子”

&emsp; 啊！我知道，我的小标题起的越来越老土了，甚至还有打广告的嫌疑（竟然被发现了，咳咳....）不过我的确暂时想不到更好的简述了。

&emsp; 言归正传，声卡，一个经常被人们忽视的设备，我，作为一个HiFi发烧友，对声卡的依赖性就像猫奴吸猫一样，一日不吸，整天都没有好状态。除了睡觉之外的任何工作我都离不开音乐，虽然在焊接这类危险工作的时候要尽量保证安静，但我还是在动次打次.....

&emsp; 声卡之所以被人忽视是因为，就像耳机一样，声卡的价格可以从十几元的白菜价到几百，几千，几万甚至几十万的天价。如果只是听个响，大部分设备，诸如电脑，手机，平板都有板载的集成声卡，大部分计算机主板都集成了AC97兼容声卡，所以，很多人似乎认为拥有音频的输入输出是计算机本来就有的功能。

&emsp; 然而事实并非如此，就和显卡一样，标准的声卡也是一种插在主板上的板卡，声卡主要负责对音频的处理，简单来说，声卡是一种封装了ADC和DAC的板卡，当然了这个ADC和联盟这些类Dota游戏里面的ADC可不是一个东西，这里的ADC是analog digital convert 模拟-数字 转换也就是传说中的模数转换，模拟信号就是生活中的信号，比如声音，声音的变化可以连续的被记录在电流中，也就是用电流模拟声音的变化。但是数字信号是非线性的，只有1和0两个状态，所以，需要进行转换，这就是ADC，通常ADC负责录音。至于DAC，就是数模转换了，简单来说就是把音频文件中的数字信号转换
成驱动音响的模拟信号（电信号），通过音响内部的信号放大电路处理之后，你就可以听到声音了。

&emsp; 实际上，早期的声卡集成了游戏控制器的接口，也就是接驳手柄一类设备的接口。综上，就是声卡的全部了，当然这也是一个抽象的声卡。（笑）

## 网卡:和声卡一样的幕后英雄

&emsp; 网卡，就和声卡一样，很多人都觉得是计算机本来就提供的功能，因为它和声卡一样，早就被板载了，很少有人再去购买独立网卡了，网卡，很容易猜到它的意思，就是提供计算机联网功能的设备，网卡其实也是有很大学问的，网卡的接口决定了网速，或者无线网卡的一些协议都会影响网络速度。因为目前广泛被集成的有线网卡都是千兆速率的（也是小b），所以就不细说了~

## 主板:热情的东北人

&emsp; 啊！我感觉很多人觉得我在开地图炮了，当然，如果你这么觉得，请在当前浏览器按下ctrl + w 然后别再来这个网站了。如果你觉得我是在引用一个巧妙的比喻（可能并不巧妙），那么让我们继续聊天吧～

&emsp; 终于到了我们晦涩难懂又枯燥无味的抽象介绍的最后一位了，当然，我说的是这些设备，并不是我，哈哈。

&emsp; 那么，主板到底是什么呢？根据我上面的描述，似乎所有东西都插或者接驳在主板上。事实正是如此，差不多所有的计算机硬件设备都要与主板连接，主板在英文中写作MotherBoard，所以你也可以叫它母版，不过无所谓了，主板在计算机中责任重大，不仅板载集成了好多设备，还包含 南桥 和 北桥芯片 来沟通处理器和内存以及各种板卡设备，同时拥有很多的接口，各种电源接口（用来给主板供电，同时也提供了为各种设备，如硬盘，显卡这类设备供电的接口），各种按键接口（比如开机键，重启键），各种设备接口，比如硬盘接口（IDE SATA SCSI等）或者各种板卡接口（显卡接口PCI-E,声卡接口PCI 都是常用接口，并不是绝对的）。总得来说，计算机的设备通过与主板连接，主板提供了不同设备数据交换的通道，同时给大部分设备供能，也可以通过主板的一些设置调节系统的一些参数。


