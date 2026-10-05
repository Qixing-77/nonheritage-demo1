# C2 埋点系统 track_events
## 12个埋点事件定义
|事件ID|事件英文名|归属模块|含义|
|---|---|---|---|
|e01|game_enter|游戏|用户进入非遗游戏页面|
|e02|game_start|游戏|用户开始游戏|
|e03|game_finish|游戏|用户游戏完赛|
|e04|coupon_get|游戏|用户领取优惠券|
|e05|order_click|游戏|用户点击下单|
|e06|order_submit|游戏|用户提交下单|
|e07|aigc_enter|AIGC|用户进入AIGC生成页面|
|e08|aigc_create|AIGC|用户发起AIGC生成请求|
|e09|aigc_success|AIGC|AIGC生成图片成功|
|e10|aigc_adopt|AIGC|用户采纳AIGC生成结果（计算采纳率）|
|e11|demo_mark|公共|DEMO演示标记事件|
|e12|page_view|公共|页面访问|

## track_events MySQL建表SQL
```sql
CREATE TABLE track_events (
  id BIGINT AUTO_INCREMENT PRIMARY KEY COMMENT '自增主键',
  event_id VARCHAR(64) NOT NULL COMMENT '事件ID e01~e12',
  event_name VARCHAR(128) NOT NULL COMMENT '事件英文名称',
  user_id VARCHAR(128) NOT NULL COMMENT '用户ID',
  culture_id VARCHAR(64) COMMENT '非遗/特产品类ID，关联素材',
  event_time DATETIME NOT NULL COMMENT '事件发生时间',
  is_demo TINYINT DEFAULT 0 COMMENT '是否DEMO数据：1=DEMO，0=真实数据',
  ext_info JSON COMMENT '扩展字段，存放额外参数',
  INDEX idx_userid (user_id),
  INDEX idx_eventtime (event_time),
  INDEX idx_eventid (event_id)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COMMENT='用户行为埋点表';
