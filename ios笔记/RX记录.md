## RX学习记录

### observable可监听序列

* single用于单个网络请求，返回一个值或error
* completable只用于检测任务是否完成，返回completed或error
* maybe是single和completable的混合
* driver不产生error事件，并会发送最近一次的序列给共享的观察者，适用于文本内容和选择值的绑定（状态序列）
* signal是不会回放上一个元素的driver，适用于点击事件（事件序列）

