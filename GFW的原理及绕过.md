# GFW的原理及绕过
> maoist2009

GFW，估计是目田起的，全称GreatFireWall，指的是中国的国际联网审查机器，但也成约定俗成的名字了。

## 审查机器
虽然gfw是wall，但是自由派往往称其为审查机器（censor）。

这是因为，反动政府无法完全阻断互联网，其作为第三次产业革命的产物早已深入社会生产的各个部分。这就像封建统治者不能禁止农民阶级拥有锄头一样。

因此，其需要识别流量，这就需要流量本身有特征，如没有加密，大小明显等。与此同时，审查机器所面对的是国际出入口每秒TB级别的出入数据（也就是几千部电影的大小），其必须能快速地处理数据流。这正是反动政府面对人民群众的劣势。反动政府的机器再好，也多不过人民群众手中设备的总和，只不过人民群众还没有团结起来罢了。
## 各级网络协
网络协议大致分为四层，就好像从物理到化学到生物学到社会学一样，每一层都有自己的规律，又为上一层所承载。
1. 为了讲清楚审查的过程，我会重点讲讲过程中泄露了哪些信息。
2. 为了规避审查，我们需要改变包的内容，所以需要知道我们能否有权限对这一层数据进行更改

### 数据链路层
这一层底下就是物理信号。该层搭建了一个局部的网络。

该层常见协议为以太网协议，这个网络中机器的编号叫mac号。

在这个网络中，所有机器可谓互相连接。类比邮件递送过程，这就像地方邮局，记录下了附近邮局和住户的实际地址，比如说某某路多少弄几号。每个数据包[^1]有一个源mac和目标mac。

[^1]: 可以理解成每个快递包裹，但是我们没有全球地图，只能和几个附近直接相连的个体对话。

这一层是一个叫做网卡的硬件负责的，即使是操作系统[^2]也无法自由控制[^3]。但是，特别的，mac号是由操作系统可以控制的。

[^2]: 也指有高权限的应用，所谓高权限权限如windows的admin权限，linux的root权限。

[^3]: 自由控制只能自由构造包裹，这一层来讲，比如说能不写mac号，或者在两个mac号中间插入别的东西，或把mac号放在数据后头等。

每台机器的mac号由网卡决定，每个网卡的默认mac号表示了厂商名，批次名和编号。每台设备默认mac号不一致，所以会被用来标识设备。当然，网卡提供操作修改自己mac号。

### ip层

这一层定义了一个互联的网络最大的ip网络就是全球互联网（公网），因为网络中参与者太多，很多时候这些人在一个小ip网络（局域网）中，共用一个上一级ip网络身份，甚至局域网也可以嵌套。

常见的协议有ipv4协议和ipv6协议。ipv6是因为ipv4地址不够用而提出的。你可以认为ip是一个家庭，共用一个编号（收件地址），如中南海习家。

显然，ip是被泄露了的。因此，审查机器可以阻止向特定的收件人送信。这种封锁手段就叫**ip黑洞**
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4ODgzNTE5MTAsLTYzMjk1MjI1M119
-->