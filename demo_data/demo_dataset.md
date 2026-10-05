# C4 演示DEMO数据集
> 存放展会现场演示用模拟埋点数据，所有模拟数据标记 is_demo = 1，不和真实业务数据混淆。
> 文件存放目录：demo_data/

## 一、DEMO数据说明
1. 模拟5个演示用户：demo_01 ~ demo_05
2. 每条埋点数据 `is_demo = 1`，用于看板演示筛选
3. 覆盖全部12个事件 e01‑e12，包含游戏流程、AIGC生成、页面访问完整链路
4. 格式支持：SQL插入脚本，可直接导入track_events表

## 二、DEMO模拟数据INSERT脚本
```sql
INSERT INTO track_events (event_id,event_name,user_id,culture_id,event_time,is_demo,ext_info) VALUES
-- demo_01 用户完整游戏+AIGC流程
('e01','game_enter','demo_01','cult001','2026‑09‑10 09:00:00',1,'{"product":"德庆贡柑"}'),
('e02','game_start','demo_01','cult001','2026‑09‑10 09:00:15',1,'{}'),
('e03','game_finish','demo_01','cult001','2026‑09‑10 09:02:30',1,'{"score":85}'),
('e04','coupon_get','demo_01','cult001','2026‑09‑10 09:02:45',1,'{"coupon_id":"cp001"}'),
('e05','order_click','demo_01','cult001','2026‑09‑10 09:03:10',1,'{}'),
('e06','order_submit','demo_01','cult001','2026‑09‑10 09:04:00',1,'{"order_no":"ord_d01"}'),
('e07','aigc_enter','demo_01','cult002','2026‑09‑10 09:10:00',1,'{"product":"西江鲈鱼"}'),
('e08','aigc_create','demo_01','cult002','2026‑09‑10 09:10:20',1,'{"prompt":"生成西江鲈鱼宣传图"}'),
('e09','aigc_success','demo_01','cult002','2026‑09‑10 09:11:10',1,'{}'),
('e10','aigc_adopt','demo_01','cult002','2026‑09‑10 09:11:40',1,'{}'),
('e11','demo_mark','demo_01','', '2026‑09‑10 09:12:00',1,'{"scene":"展会现场演示"}'),
('e12','page_view','demo_01','cult001','2026‑09‑10 09:13:00',1,'{"page":"首页"}'),

-- demo_02 用户：游戏完赛，不使用AIGC
('e01','game_enter','demo_02','cult003','2026‑09‑10 09:15:00',1,'{"product":"广宁笋干"}'),
('e02','game_start','demo_02','cult003','2026‑09‑10 09:15:20',1,'{}'),
('e03','game_finish','demo_02','cult003','2026‑09‑10 09:17:10',1,'{"score":72}'),
('e12','page_view','demo_02','','2026‑09‑10 09:18:00',1,'{"page":"素材列表页"}');
