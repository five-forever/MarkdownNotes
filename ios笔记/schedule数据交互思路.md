### schedule主页

* 重点是模型的建立，和主页数据加载和展示的逻辑，是全部获取展示还是部分获取展示
* Schedule不再进行合并。 仅在创建和修改Schedule时，判断前后一小时内是否存在别的Schedule。如果存在，则不可创建，且提示用户冲突。
* 暂定进入时GCD多线程一次请求7天数据，之后点击和滑动请求所在天的数据，在界面停留时，每15s轮询请求一次当天的数据？
* ⭐️⭐️⭐️先把本地的假数据源读取整好了再写请求，整明白handyjson
* 初次请求全部schedule数据结束后，后续滚动界面的请求都不显示网络转圈加载，加载失败就保持原样并开启另一个定时器（比正常的轮询定时器更快，成功一次后就关闭）？
* selectedday变化时判断一下是否相同，若相同则不执行任何操作，点击按钮时同理？
* getAll的请求完成后回主线程reload数据源



### schedule编辑页

* 两个入口，传入不同的信息，不传值的默认状态下为create，传入当前schedule model的情况下再切换成edit页，初始化默认选择的时间，隐藏repeat，显示delete按钮（有时不可删除，再说吧）

* 添加和编辑时都会返回一个scheduleID，添加时示例

* ```json
  "payload"``: {
    `` ``"method"``: ``"addTsSchedule"``,
    `` ``"data"``: {
    ``  ``"routineId"``: 11,
    ``  ``"dayOfWeeks"``: 2,
    ``  ``"startTimeSec"``: 16`` ``
  				},
  `` ``"source"``: ``"APP"``
  }
  ```

  编辑时示例

  ```json
  "payload"``: {
   ``"method"``: ``"adjustTsSchedule"``,
   ``"data"``: {
    ``"scheduleId"``: 12,
    ``"dayOfWeeks"``: 2,
    ``"startTimeSec"``: 16,
    ``"routineId"``: 11
   ``},
   ``"source"``: ``"APP"
  }
  ```

* 接下来要做的事
  1. 处理edit和add页两种情况的判断
  2. 编辑时直接隐藏weekly repeat的cell
  3. 编辑时传入当前时间，timepicker设为当前值 OK
  4. 编辑时传入当前routine信息，routine设为默认选中（routine未合并）
