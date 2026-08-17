# Current Handoff

Last updated: 2026-08-17
Verified against: master 33ff166（本地与 GitHub 一致）

## Current state

- 本地文件夹 `桌面\项目台\Codex库存仪表盘` 已连体 GitHub 公开仓库 axinjjj/codex-manager（master）
- 管理器正常运行的路径：`Codex管理器/manager.bat`，地址 http://127.0.0.1:8799/
- 桌面「Codex 管理器」图标用 8.3 短路径指向新位置，已验证可用

## Recently completed（2026-08-17）

- 本地目录从没有 git 的毛坯接入仓库：克隆官方结构 + 合入本地新改进
- 管理器新增技能标签（havenskill/vpsskill/memoryskill）和路径感知描述
- 补回仓库缺失的 `零件箱/库存仪表盘.html`（没它仪表盘打不开）
- .gitignore 增加：隔离区/、*.lnk

## Active work

无进行中任务。

## Known issues

- `docs/screenshot.png` 和 `零件箱/screenshot.png` 疑似重复，未来清理时确认

## Next safe step

docs/待办.md 里的两个功能：翻译缓存、skill 单独删除按钮。

## Do not lose

- 隔离区永不入库；改代码前先停掉正在运行的管理器；发布前确认没有私人数据
