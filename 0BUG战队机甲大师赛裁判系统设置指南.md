```
文件名：0BUG战队裁判系统设置指南.md  
作者：叶林伟  
版本：V1.0  
创建日期：2020-02-17  
文件描述：本文档基于大疆机甲大师赛2019年版裁判系统，详细描述裁判系统搭建思路  
```
# 0BUG战队裁判系统设置指南  
本文档基于大疆机甲大师赛2019年版裁判系统，详细描述裁判系统搭建思路。  
我期待阅读者拥有基本的计算机网络常识，最好对IP地址、子网掩码、网关等概念有一定的认识。没有也没关系，这不是考试，不懂的名词可以上网查。同时我也会尽我所能用通俗易懂的语言来描述。  

## 裁判系统的工作原理  
裁判系统的核心就三个部分：服务器、客户端、机器人。  
这三部分相互通信，共同组成整个裁判系统。
![Effect](https://github.com/DLUT-0BUG/RM-RefereeSystemConfiguration/blob/master/3BasicParts_for_RefereeSystem.png)  
### 服务器  


## 裁判系统的网络设备拓扑 
裁判系统基本由以下设备组成： 

1. 服务器  
2. 操作手电脑  
3. 机器人上的裁判系统控制模块  
4. 无线路由器
   
虽然不是必要组成部分，有时也包括：  

5. 图传发送端  
6. 图传接收端  
7. 交换机  

其中，设备1服务器和设备2操作手电脑，本质都是运行在Windows系统上的软件，占用系统资源很少。这里我们假定他们分别运行在专门的作为服务器的电脑和操作手的电脑上，并把它们当作真实物理设备来处理。  

大疆提供的裁判系统控制模块只能通过2.4GHz频段的Wi-Fi来与裁判系统服务器通信（准确来说是IEEE 802.11 bgn协议），因此我们需要一个无线路由器作为整个系统的核心来连接各个设备。考虑到届时我方最多会有7个设备（5个车/无人机/导弹）同时在线，为避免Wi-Fi设备过多堵塞信道，造成没有必要的通信延迟，我希望服务器和操作手的电脑通过网线与路由器相连。  
这就引发了另一个小问题问题，市售家用无线路由器的LAN口有限，无法满足所有操作手电脑的通信需求，所以我们引入设备7千兆交换机来扩展接口。  
考虑到一方面交换机转发存在通信延迟（尽管很小），另一方面服务器在整个网络拓扑中需要与所有设备建立通讯，这里我建议服务器的网线和路由器的LAN口相连，操作手电脑与交换机相连，再用一根网线接通路由器LAN口和交换机。  

![Effect](https://github.com/DLUT-0BUG/RM-RefereeSystemConfiguration/blob/master/DeviceTopology_for_RefereeSystem.png)  
