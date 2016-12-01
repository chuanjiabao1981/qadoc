## 状态
* missed: -1, # 已错过
* init: 0, # 初始化
* ready: 1, # 等待上课
* teaching: 2, # 上课中
* paused: 3, # 暂停中 意外中断可以继续直播
* closed: 4, # 直播结束 可以继续直播
* finished: 5, # 已完成 不可继续直播
* billing: 6, # 结算中
* completed: 7 # 已结算

## 事件

