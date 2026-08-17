# AGENTS.md — Codex 库存仪表盘

## 这是什么
阿欣的可视化小工具：看见、管理、清理 Codex 本地配置（防止 Codex 堆垃圾）。公开仓库 axinjjj/codex-manager，群里有老师在用。

## 怎么跑
- 管理器：运行 `Codex管理器/manager.bat`，访问 http://127.0.0.1:8799/
- 仪表盘：运行 `Codex管理器/dashboard.bat`（生成并打开报告）
- 测试：`python Codex管理器/tests/test_manager.py`（如目录结构不同先确认路径）

## 规矩
- 「隔离区」是私人回收站，绝对不入库（.gitignore 已挡，发布前再确认一次）
- 改完 `Codex配置管理器.py` 必须：`python -m py_compile` 语法检查 + 重启管理器 + 打开 8799 验证
- 这个文件含大量中文，读写一律显式 UTF-8（PowerShell 5.1 默认会搞坏中文）
- 最小改动；不顺手重构；一次性脚本不入库
