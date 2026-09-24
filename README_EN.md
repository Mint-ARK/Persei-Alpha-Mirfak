# Persei-α-Mirfak

<div align="center">

[简体中文](./README.md) | **English**

![Platform](https://img.shields.io/badge/Platform-Windows%2010%2B%20%7C%20Linux%20x64-0078D6?style=flat-square)
![Python Version](https://img.shields.io/badge/Python-3.10%2B%20(asyncio)-3776AB?style=flat-square&logo=python)
![License](https://img.shields.io/badge/License-Non--Commercial%20Research-grey?style=flat-square)

<p align="center">
  <b>Aether Gazer Offline Simulation Server Core Engine (Python 3.10+)</b>
</p>

</div>

---

## Module Scope

`Persei-α-Mirfak` (Alpha Persei / Mirfak) serves as the core backend simulation runtime repository within the **Alpha Persei Cluster** ecosystem.

This repository contains the pure Python server runtime source code and required metadata configuration schemas. It strictly excludes heavy binary assets (character illustrations, 3D models, audio files) and web management dashboards.

---

## Architecture Overview

The backend comprises 70 core Python modules organized into 9 distinct subsystems:

1. **Assembly & Lifecycle Entrypoints (4 modules)**: `main.py`, `login.py`, `server_daemon.py`, `replay.py`
2. **Network Transport & Protocol Listeners (6 modules)**: `server_net.py`, `transport.py`, `dns_server.py`, `cdn_proxy.py`, `fetch_manifests.py`, `gen_cert.py`
3. **Session Scheduling & Pipeline Dispatch (5 modules)**: `core.py`, `middleware.py`, `operations.py`, `event_bus.py`, `protocol_ref.py`
4. **Dynamic Protobuf Codec & Response Assembly (7 modules)**: `codec.py`, `generator.py`, `decode_schema.py`, `hero_codec.py`, `reserve_codec.py`, `daily_fatigue_codec.py`, `schema_default.py`
5. **Data Persistence & Schema Migration (2 modules)**: `account_db.py`, `normalize_db_transitions.py`
6. **Core Business Domain Services (25 modules)**:
   * `hero_service.py` (Character progression)
   * `draw_service.py` (Gacha and pity mechanics)
   * `inventory_service.py` (Asset mutations & delta frames)
   * `achievement_service.py` (Achievement progression & banners)
   * `fatigue_service.py` (6-minute natural stamina recovery)
   * `equip_service.py` (Sigil enhancement & breakthroughs)
   * `servant_service.py` (Unique functor instances & awakening)
   * `chip_service.py` (Admin Cat & character AI chips)
   * `stage_service.py` (Stage progression & 3-star conditions)
   * `mail_service.py` (Mailbox & Special Letters archive)
   * `shop_service.py` (Shop shelves & periodic stock resets)
   * `recharge_service.py` (Payment simulation & tier rewards)
   * `trust_service.py` (Affection levels & gifting)
   * `oath_service.py` (Oath ceremonies & hero assignments)
   * `backhome_service.py` (Dormitory, canteen & commissions)
   * `admin_cat_explore_service.py` (Idle cat exploration dispatches)
   * `polyhedron_service.py` (Dimensional Variable rogue-like engine)
   * `weekly_challenge_service.py` (Weekly challenge periodic rotation)
   * `rogueteam_service.py` (Challenge Rogue Team / Fictional Deduction)
   * `autochess_service.py` (Dojo AutoChess simulation)
   * `minigame_service.py` (Resident minigame progressions)
   * `periodic_gift_service.py` (Multi-day recurring supply packs)
   * `peripheral_service.py` (Profiles, lobby scenes & assistants)
   * `archive_service.py` (Character profiles & Heart-Link stories)
   * `activity_lottery.py` (Activity chest drop lottery)
7. **Combat & Battle Subsystems (5 modules)**: `battle_server.py`, `battle_payload.py`, `cooperation_skill_server.py`, `team_server.py`, `mythic_affix_cfg.py`
8. **AI Character Dialogue Subsystem (7 modules)**: `ai_bot_service.py`, `ai_bot_config.py`, `ai_context_builder.py`, `ai_history_manager.py`, `ai_calendar.py`, `ai_bot_leaderboard.py`, `ai_translator.py`
9. **Operations, Monitoring & Event Listeners (9 modules)**: `gm_api.py`, `gm_reader.py`, `res_version_manager.py`, `task_listener.py`, `timer_listeners.py`, `lazy_timer.py`, `logger.py`, `log_sifter.py`, `illustrated_listener.py`

---

## Quick Start

1. **Install Dependencies**:
   ```powershell
   pip install -r requirements.txt
   ```
2. **Install Local Root Certificate** (Administrator privileges required):
   ```powershell
   .\一键安装Windows证书.bat
   ```
3. **Launch Server**:
   ```powershell
   python main.py
   ```

---

## Disclaimer

This project is intended strictly for personal research and educational study in distributed network protocol engineering and software reverse engineering. Commercial use is strictly prohibited.
