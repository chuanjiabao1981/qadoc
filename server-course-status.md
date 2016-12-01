## 状态列表
* rejected: -1, # 被拒绝
* init: 0, # 审核中
* published: 1, # 招生中
* teaching: 2, # 已开课
* completed: 3 # 已结束

## 事件
* 创建
* 审核通过
* 拒绝
* 编辑
* 调课

## 创建
辅导班创建完成以后处于`init`状态

## 审核通过

审核中`init`的辅导班可以审核通过, 审核通过以后辅导班进入`published`状态

如果辅导班第一节课时间小于等于今天, 辅导班从`published`跳到`teaching`并处理辅导班下面的课程

1. 今日之前的课程`missed`
2. 今日课程`ready`
