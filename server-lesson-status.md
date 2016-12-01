## 状态
* missed: -1, # 已错过
* init: 0, # 初始化/未上课
* ready: 1, # 等待上课
* teaching: 2, # 上课中
* paused: 3, # 暂停中 意外中断可以继续直播
* closed: 4, # 直播结束 可以继续直播
* finished: 5, # 已完成 不可继续直播
* billing: 6, # 结算中
* completed: 7 # 已结算

## 事件
* 创建
* 删除
* 准备
* 错过
* 调课
* 上课
* 心跳
* 暂停
* 结束
* 完成
* 结算

## 辅导班交互
* 课程数量 lessons_count
* 开课数量 started_lessons_count
* 完成数量 finished_lessons_count

## 事件触发 

### 创建/删除
辅导班在可编辑`rejected`, `init`状态下可以创建/删除课程, 课程创建/删除更新`lessons_count`(依赖counter_cache)

### 准备
每天凌晨执行定时任务, 准备今日要上课的课程, `init`进入`ready`状态
辅导班通过审核, 准备今日要上课的课程, `init`进入`ready`状态

### 错过
每天凌晨执行定时任务, 设置前一天没有上课的课程为错过状态, `init`, `ready`进入`missed`状态

### 调课
未上课`init`, `ready`, `missed`的课程可以调课

调课后今日辅导班进入`ready`状态, 非今日辅导班进入`init`状态

### 上课

