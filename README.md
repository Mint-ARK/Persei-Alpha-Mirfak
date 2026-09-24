# 天船三 (Persei-α-Mirfak)

<div align="center">

**简体中文** | [English](./README_EN.md)

![Platform](https://img.shields.io/badge/Platform-Windows%2010%2B%20%7C%20Linux%20x64-0078D6?style=flat-square)
![Python Version](https://img.shields.io/badge/Python-3.10%2B%20(asyncio)-3776AB?style=flat-square&logo=python)
![License](https://img.shields.io/badge/License-Non--Commercial%20Research-grey?style=flat-square)

<p align="center">
  <b>Aether Gazer 离线仿真服务端核心源码 (Simulation Runtime Engine)</b>
</p>

</div>

> 📖 **项目杂谈 / 开发者手记**：  
> 想了解本项目立项背后的心路历程、开发故事与作者的碎碎念？欢迎阅读博文：[《关于LocalServer》- MoriaRuRuka](https://moriaruruka.com/2026/09/24/411/)。

---

## 模块定位

`Persei-α-Mirfak`（天船三）是 **Alpha Persei Cluster** 体系中的服务端核心内核仓库。本仓库仅包含服务端的纯 Python 运行时源码与必要配置结构，不包含重型静态资产（立绘、模型、音效）或前端管理面板。

---

## 核心架构概览

服务端由 70 个核心 Python 模块构成，按功能职责划分为 9 大工程子系统：

1. **主装配与生命周期入口 (4 模块)**：`main.py`, `login.py`, `server_daemon.py`, `replay.py`
2. **网络传输与多协议监听层 (6 模块)**：`server_net.py`, `transport.py`, `dns_server.py`, `cdn_proxy.py`, `fetch_manifests.py`, `gen_cert.py`
3. **会话调度与业务管线中枢 (5 模块)**：`core.py`, `middleware.py`, `operations.py`, `event_bus.py`, `protocol_ref.py`
4. **动态 Protobuf 编解码与响应合成体系 (7 模块)**：`codec.py`, `generator.py`, `decode_schema.py`, `hero_codec.py`, `reserve_codec.py`, `daily_fatigue_codec.py`, `schema_default.py`
5. **数据持久化与结构治理 (2 模块)**：`account_db.py`, `normalize_db_transitions.py`
6. **核心业务领域服务集群 (25 模块)**：
   * `hero_service.py` (角色养成)
   * `draw_service.py` (抽卡与保底)
   * `inventory_service.py` (资产出入库与原子变更帧)
   * `achievement_service.py` (成就推进与横幅广播)
   * `fatigue_service.py` (体力 6 分钟自然恢复推算)
   * `equip_service.py` (刻印强化突破与赋能)
   * `servant_service.py` (钥从独立实例与唤醒)
   * `chip_service.py` (管理喵与角色行为芯片)
   * `stage_service.py` (关卡与章节流转)
   * `mail_service.py` (邮件与信件收藏室)
   * `shop_service.py` (商城货架与周期限购)
   * `recharge_service.py` (充值模拟与累充积分)
   * `trust_service.py` (好感度与送礼交互)
   * `oath_service.py` (誓约仪式与专属任务)
   * `backhome_service.py` (游园街/后宅/食堂)
   * `admin_cat_explore_service.py` (猫咪探索挂机)
   * `polyhedron_service.py` (多维变量局内状态机)
   * `weekly_challenge_service.py` (高难周常玩法轮换)
   * `rogueteam_service.py` (虚构推演玩法)
   * `autochess_service.py` (决斗王自走棋)
   * `minigame_service.py` (常驻小游戏)
   * `periodic_gift_service.py` (连续多日周期礼包)
   * `peripheral_service.py` (名片装扮与大厅看板)
   * `archive_service.py` (角色档案与心链故事)
   * `activity_lottery.py` (任务活跃度宝箱附加抽奖)
7. **战斗与交互子系统 (5 模块)**：`battle_server.py`, `battle_payload.py`, `cooperation_skill_server.py`, `team_server.py`, `mythic_affix_cfg.py`
8. **AI 角色交互子系统 (7 模块)**：`ai_bot_service.py`, `ai_bot_config.py`, `ai_context_builder.py`, `ai_history_manager.py`, `ai_calendar.py`, `ai_bot_leaderboard.py`, `ai_translator.py`
9. **运维监控、日志与调度监听 (9 模块)**：`gm_api.py`, `gm_reader.py`, `res_version_manager.py`, `task_listener.py`, `timer_listeners.py`, `lazy_timer.py`, `logger.py`, `log_sifter.py`, `illustrated_listener.py`

---

## 运行方式

1. **安装环境依赖**：
   ```powershell
   pip install -r requirements.txt
   ```
2. **信任本地根证书**（首次运行，需管理员权限）：
   ```powershell
   .\一键安装Windows证书.bat
   ```
3. **启动服务**：
   ```powershell
   python main.py
   ```

---

## 免责声明

本项目仅供软件逆向工程、分布式网络协议编解码等课题的个人研究与学术交流使用。严禁用于任何商业目的。
