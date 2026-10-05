# C3 增长看板文档
> 跨模块看板：游戏模块【游戏参与→完赛→兑券→下单】；AIGC模块【AIGC采纳率】
> 数据来源：track_events埋点表；区分真实数据 / DEMO演示数据(is_demo字段)

## 一、指标口径定义（游戏漏斗）
|指标|计算逻辑|
|---|---|
|游戏参与人数|触发 e01(game_enter) 的独立user_id数量|
|游戏完赛人数|触发 e03(game_finish) 的独立user_id数量|
|完赛率|完赛人数 ÷ 游戏参与人数|
|兑券人数|触发 e04(coupon_get) 的独立user_id数量|
|兑券率|兑券人数 ÷ 游戏完赛人数|
|下单人数|触发 e06(order_submit) 的独立user_id数量|
|下单转化率|下单人数 ÷ 兑券人数|

## 二、AIGC指标
|指标|计算逻辑|
|---|---|
|AIGC生成成功次数|事件 e09(aigc_success) 触发总次数|
|AIGC采纳次数|事件 e10(aigc_adopt) 触发总次数|
|AIGC采纳率|AIGC采纳次数 ÷ AIGC生成成功次数|

## 三、统计SQL脚本
### 3‑1 游戏漏斗（DEMO演示数据 is_demo=1）
```sql
SELECT
  event_id,
  COUNT(DISTINCT user_id) AS user_cnt
FROM track_events
WHERE is_demo = 1 AND event_id IN ('e01','e03','e04','e06')
GROUP BY event_id;

SELECT
  SUM(IF(event_id='e09',1,0)) AS success_cnt,
  SUM(IF(event_id='e10',1,0)) AS adopt_cnt,
  ROUND(SUM(IF(event_id='e10',1,0)) / SUM(IF(event_id='e09',1,0)),4) AS adopt_rate
FROM track_events
WHERE is_demo = 1;

