# C8 系统配置说明
> 目录：specs/
> 包含三份JSON配置文件（后续代码阶段生成）
1. game_spec.json 游戏模块配置
2. aigc_spec.json AIGC生成模块配置
3. dashboard_spec.json 数据看板模块配置

## 一、game_spec.json（游戏模块配置）
用途：存放小游戏全局参数、需要上报的埋点事件、关联特产品类ID
关键字段说明：
- game_name：游戏对外展示名称
- max_score：游戏满分
- coupon_enable：是否开启优惠券发放功能 true/false
- event_list：游戏需要上报的埋点事件ID集合
- culture_ids：游戏可供选择的特产品类ID列表

## 二、aigc_spec.json（AIGC生成模块配置）
用途：控制AIGC图片生成相关参数
关键字段说明：
- aigc_model：调用模型标识
- max_generate_times：单个用户最大生成次数
- event_list：AIGC模块埋点事件集合
- prompt_prefix：生成图片提示词统一前缀

## 三、dashboard_spec.json（数据看板配置）
用途：大屏、BI看板全局参数
关键字段说明：
- demo_filter_is_demo：默认筛选demo数据标记值
- chart_type：启用图表类型，漏斗图、指标卡片等
- show_index：看板展示指标清单

## 四、使用规则
1. 程序启动读取三份json配置，不需要修改代码，改配置文件即可调整业务参数
2. 不要在配置文件写密码、数据库密钥等敏感信息
3. 修改配置后需要重启对应模块生效

## C8验收标准
1. 三份json配置字段定义完整清晰
2. 业务参数与代码解耦，改配置即可调整业务行为
3. 配置文件统一存放specs文件夹
