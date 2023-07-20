# GameNetworkingSockets

GameNetworkingSockets是游戏的基本传输层。其特点是:

* 面向连接的API(如TCP)
* …但是是面向消息的(如UDP)，而不是面向流的。
* 支持可靠和不可靠消息类型
* 消息可以大于底层MTU。该协议对可靠的消息进行分片、重组和重传。
* 可靠性层比基本的tcp风格的滑动窗口复杂得多。
* 数据加密
* 在同一连接上的多个消息流(“通道”)的行首阻塞控制和带宽共享。
* 支持IPv6
* 点对点网路
* 跨平台。该库已在主机，手机平台和非steam商店上发布，并已用于促进跨平台连接。

github: [https://github.com/ValveSoftware/GameNetworkingSockets](https://github.com/ValveSoftware/GameNetworkingSockets)