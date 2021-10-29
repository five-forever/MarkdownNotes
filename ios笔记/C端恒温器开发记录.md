## ScheduleList页

* 点击添加跳转至Edit页，初始化一个带isedit属性为false的editVM

* 点击schedule的cell跳转至edit页，需要传递data信息如下

  ```JSON
  "payload": {
    "method": "adjustTsSchedule",
    "data": {
      "scheduleId": 12,
      "dayOfWeeks": 2,
      "startTimeSec": 16,
      "routineId": 11
    },
    "source": "APP"
  }
  ```

其中dayOfWeeks为当前选中schedule的所在天（传当前选中的titie信息即可）值范围是2 4 8等对应周一到周日？（或者周日到周一？）



* 获取当前day schedulelist的回复信息如下

  ```json
  {
   ``"code"``: 0,
   ``"traceId"``: ``"1627974237147"``,
   ``"result"``: {
    ``"total"``: 4,
    ``"scheduleList"``: [
     ``{
      ``"scheduleId"``: 12,
      ``"fromPreviousDay"``: ``true``,
      ``"startTimeSec"``: 100,
      ``"routineName"``: ``"111_thermostat"``,
      ``"routineType"``: 2,
      ``"heatToTemp"``: 52.00,
      ``"coolToTemp"``: 68.00
     ``},
     ``{
      ``"scheduleId"``: 111,
      ``"fromPreviousDay"``: ``false``,
      ``"startTimeSec"``: 800,
      ``"routineName"``: ``"thermostat"``,
      ``"routineType"``: 4,
      ``"heatToTemp"``: 52.00,
      ``"coolToTemp"``: 78.00
     ``},
     ``{
      ``"scheduleId"``: 112,
      ``"fromPreviousDay"``: ``false``,
      ``"startTimeSec"``: 890,
      ``"routineName"``: ``"111_thermostat"``,
      ``"routineType"``: 2,
      ``"heatToTemp"``: 52.00,
      ``"coolToTemp"``: 68.00
     ``},
     ``{
      ``"scheduleId"``: 11,
      ``"fromPreviousDay"``: ``false``,
      ``"startTimeSec"``: 8640,
      ``"routineName"``: ``"111_thermostat"``,
      ``"routineType"``: 2,
      ``"heatToTemp"``: 52.00,
      ``"coolToTemp"``: 68.00
     ``}
    ``]
   ``}
  }
  ```

如此一来展示schedule时就不用再去查找routine列表了，也可以不请求routine列表？



* schedulelist思路：内容部分为左右滑动的collectionview，有横向排列的7个cell对应7天，每个cell包含1个tableview，tableview中的每个cell是一条schedule信息 先从每条的schedule信息写起
* 点击schedule编辑事件思路：page的collectionview层可以确定selectedDay 点击时需要传一个索引？ 在初始化数据源时可以给cell加一个属性？
* 可以给每个schedule cell初始化时增加一个model？总的model二维数组在schedule主页的vm中请求获取，通过handyjson转化

## ScheduleEdit页

* 进入ScheduleEdit页时请求routine列表



