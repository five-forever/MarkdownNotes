# 中心模式蓝牙库封装思路

### BluetoothConStructor

​	一个基本的蓝牙管理的构造器，单例形式，自定义了线程安全池，用于同时处理几个CBCentralManagerDelegate，规定了读写操作的形式



### Network

​	负责指令的发送，超时筛查等，只关心指令发送的状态（队列）



### Command

​	蓝牙指令的序列（Network直接接收），包括指令的数据和一系列指令状态信息，如指令类型（通道、授权）、指令创建时间、指令返回的信息等



### 总结

控制底层蓝牙连接的工具，在这之上还有一层设备层，VeSyncBluetoothProducts，
