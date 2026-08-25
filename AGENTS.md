# AGENTS.md — Codex 库存仪表盘

## 这是什么
阿欣的可视化小工具：看见、管理、清理 Codex 本地配置（防止 Codex 堆垃圾）。公开仓库 axinjjj/codex-manager（master 分支），群里有老师在用。
开始工作前：读本文件 + docs/HANDOFF.md（当前状态）+ docs/待办.md（待做需求）。

## 内脏地图（功能 -> 位置）

单文件应用：前端页面（HTML/JS）和后端 API 都在 `Codex管理器/零件箱/Codex配置管理器.py` 一个文件里。

- 翻译功能：`do_translate(text, to)` 函数 + `/api/translate` 接口；按原文指纹缓存到被 Git 忽略的 `零件箱/翻译缓存.json`，未命中时依赖本机 127.0.0.1:10100 的 AI 代理
- 文件操作：`/api/save`、`/api/delete`、`/api/restore`、`/api/purge_item`；普通删除和整组清理先进「隔离区」，`purge_item`/清空回收站才会真删
- skill 列表：前端用 `/api/list?path=skills` 渲染；新建走 `/api/new_skill` + `/api/skill_template`；**skill 删除按钮可直接复用 `/api/delete`**
- 一键清理：`/api/clean_group`；md 查重：`/api/dups`；分类逻辑在 `classify(rel)` 和顶部几个常量表
- 库存仪表盘：`Scan-CodexInventory.ps1` 扫描生成，`零件箱/库存仪表盘.html` 是报告模板；`dashboard.bat` 一键出报告

## 怎么验证

1. `python -m py_compile Codex管理器/零件箱/Codex配置管理器.py`（语法检查）
2. `python tests/test_manager.py`（测试在仓库根目录 tests/，不在 Codex管理器/ 里）
3. 重启管理器：先杀掉命令行含 Codex配置管理器 的 python 进程，再运行 `Codex管理器/manager.bat`
4. 访问 http://127.0.0.1:8799/ 确认页面正常，改动点实际点一遍

## 规矩

- 「隔离区」是私人回收站，绝对不入库（.gitignore 已挡，发布前再确认一次）
- 这个文件含大量中文，读写一律显式 UTF-8（PowerShell 5.1 默认会搞坏中文）
- 最小改动；不顺手重构；一次性脚本不入库
- 结构、入口、规矩有变化，顺手更新本文件和 docs/HANDOFF.md
