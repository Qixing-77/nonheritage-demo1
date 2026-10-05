# 肇庆特色农产品数字化参展项目 C1‑C9
## 项目简介
本项目面向展会参展，实现：特产素材管理、用户行为埋点统计、游戏互动、AIGC图片生成、数据看板、断网离线演示包、展台物料、演练校验整套完整方案。

## 📂完整目录结构
nonheritage‑demo
├─ data/                 # C1 特产素材与 json 数据
├─ track_events/         # C2 埋点建表、埋点上报代码
├─ dashboard/            # C3 增长看板、统计 SQL 脚本
├─ demo_data/            # C4 展会模拟 DEMO 埋点数据
├─ offline_package/      # C5 离线大屏 HTML 演示包，断网可用
├─ booth_material/       # C6 展台物料清单、布展应急方案
├─ drill_record/         # C7 展会演练记录、测试用例
├─ specs/                # C8 游戏 / AIGC / 看板三份系统配置
└─ docs/                 # C9 项目总文档 README

## 🧰软件环境依赖
1. MySQL 8.0（存储埋点业务数据）
2. Python 3.8+ （埋点上报脚本，依赖pymysql库）
3. 浏览器（Chrome/Edge，运行C5离线大屏，**不需要服务器**）

## 🚀标准运行顺序
1. C2：执行track_events.sql，创建track_events埋点数据表
2. C4：执行demo_insert.sql导入模拟展会演示数据
3. C2：运行python埋点上报脚本，测试埋点上报功能
4. C3：执行dashboard查询SQL，获取游戏漏斗、AIGC采纳率指标
5. C5：双击index.html打开离线大屏，联网/断网两种场景验证
6. C7：按照演练文档完成全流程模拟演练

## ✅C1‑C9交付总验收
- C1：特产素材归档，提供结构化json数据
- C2：埋点表、埋点上报可运行代码，覆盖全部12事件
- C3：游戏漏斗+AIGC采纳率统计SQL脚本
- C4：完整模拟用户demo数据集
- C5：离线大屏HTML，断网可演示
- C6：展台物料清单，布展+应急方案
- C7：全项目演练测试用例，演练记录模板
- C8：游戏/AIGC/看板三份json业务配置
- C9：项目总README，目录、环境、运行流程说明

## 注意事项
1. demo数据统一标记is_demo=1，和真实业务数据做隔离
2. 离线包全部使用相对路径，不使用D:/这种磁盘绝对路径
3. 所有物料PDF源文件归档booth_material文件夹，方便展会打印

