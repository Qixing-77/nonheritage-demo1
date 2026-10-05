# C5 离线演示包 + 大屏展示方案
> 目录位置：offline_package/
> 作用：展会现场断网也可以演示大屏、非遗素材，不需要连接外网数据库。

## 一、离线包组成清单
1. 静态大屏页面（HTML，无需后端，浏览器直接打开）
2. 离线DEMO数据JSON文件（不再依赖MySQL数据库）
3. 非遗特产图片素材（从C1素材提取）
4. 使用说明 readme.txt
5. 打包脚本：一键压缩为zip离线包，用于拷贝到现场展台电脑

## 二、大屏页面内容模块
1. 标题区域：肇庆特色农产品数字化参展大屏
2. 游戏漏斗图表模块：游戏参与‑完赛‑兑券‑下单（读取本地离线JSON数据）
3. AIGC采纳率指标卡片
4. 特产素材轮播：德庆贡柑、西江鲈鱼等特产图文轮播展示
5. 页面底部：展会演示标识【离线演示模式，is_demo=1】

## 三、离线数据JSON示例 offline_demo.json
```json
{
  "is_offline": true,
  "demo_list": [
    {
      "user_id":"demo_01",
      "game_enter":1,
      "game_finish":1,
      "coupon_get":1,
      "order_submit":1,
      "aigc_success":2,
      "aigc_adopt":1
    },
    {
      "user_id":"demo_02",
      "game_enter":1,
      "game_finish":1,
      "coupon_get":0,
      "order_submit":0,
      "aigc_success":0,
      "aigc_adopt":0
    }
  ],
  "product_list":[
    {"id":"cult001","name":"德庆贡柑"},
    {"id":"cult002","name":"西江鲈鱼"}
  ]
}
