## schedule

当天请求的数据总会有from previous和until next这两天，开始时间分别为0和8640，所有数据都按开始时间已经排序好，只管显示就行



## sensor

修改传感器下sensor工作场景时是否要约束，一个场景下至少有一个sensor在工作



## 界面适配

全机型的界面适配是否在组件中进行

* VSConst里有界面适配的方法

* 约束的左右统一用leading和traling 防止阿拉伯语言环境下左右颠倒
* storyboard可以用于看不同设备界面和安全区尺寸，也可以编辑storyborad后vc根据storyboard id去读入storyboard中样式，storyboard中控件也可以拖拽访问绑定vc中方法（但是实际开发中不使用，因为storyboard操作不够精细 快捷） 
* make.edge可以同时约束上下左右，不用一个个布局



## 代码格式

* vc中代码自上而下顺序是生命周期、代理和方法、布局方法、lazy var变量，view中也类似







