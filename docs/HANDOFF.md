# Current Handoff

Last updated: 2026-09-06
Last verified feature commit: master 25b9d35（功能验证提交，本地与 GitHub 均存在）

## Current state

- 本地文件夹 `桌面\项目台\Codex库存仪表盘` 已连体 GitHub 公开仓库 axinjjj/codex-manager（master）
- 管理器正常运行的路径：`Codex管理器/manager.bat`，地址 http://127.0.0.1:8799/
- 桌面「Codex 管理器」图标用 8.3 短路径指向新位置，已验证可用
- GitHub Actions CI 位于 `.github/workflows/ci.yml`；推送和 PR 会在 Ubuntu + Python 3.14 上运行语法检查及完整契约测试

## Recently completed（2026-09-06）

- 新增只读权限的 GitHub Actions CI，自动执行管理器语法检查和 `tests/test_manager.py`
- CI 使用 Ubuntu 执行完整测试，以覆盖 Windows 无法创建的 `< >` 文件名安全夹具

## Recently completed（2026-08-17）

- 翻译结果按原文 SHA-256 指纹缓存在本地；同原文再次翻译直接命中缓存，原文变化才请求翻译代理
- 「你的 Skills」中每个用户 Skill 都有单独删除按钮；删除整个 Skill 目录进入隔离区，可原位恢复
- 本地目录从没有 git 的毛坯接入仓库：克隆官方结构 + 合入本地新改进
- 管理器新增技能标签（havenskill/vpsskill/memoryskill）和路径感知描述
- 补回仓库缺失的 `零件箱/库存仪表盘.html`（没它仪表盘打不开）
- .gitignore 增加：隔离区/、*.lnk

## Active work

无进行中任务。

## Known issues

- Windows 无法创建文件名含 `< >` 的测试夹具，因此 `test_inventory_encodes_filesystem_names_before_embedding_them` 在 Windows 建夹具时失败；CI 在 Ubuntu 上执行完整测试

## Next safe step

确认 `codex/github-ci` 分支首次 CI 运行通过；如需把 CI 设为合并门禁，再单独配置 GitHub 分支保护规则。

## Do not lose

- 隔离区和翻译缓存永不入库；改代码前先停掉正在运行的管理器；发布前确认没有私人数据
