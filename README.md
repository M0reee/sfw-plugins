# sfw-plugins

SFW 官方插件市场 `sfw-official`。格式和 Codex 官方插件目录（openai/plugins）一样：

- 市场清单：`.agents/plugins/marketplace.json`
- 每个插件一个目录：`plugins/<名字>/.codex-plugin/plugin.json`，技能放在 `skills/<技能名>/SKILL.md`
- `plugin.json` 里的 `sfwSurface.rightPanel` 是 SFW 自己的字段：装了以后右侧栏出现对应标签页（引擎会忽略它）

## 改插件

1. 改完把 `plugin.json` 的 `version` 调高（SFW 按版本号判断要不要给用户重装）。
2. 在 SFW 仓库里校验：`./.venv/bin/python tools/check_sfw_official.py /path/to/sfw-plugins`
3. 提交、推送。

SFW 从 `SFW_OFFICIAL_MARKET_GIT` 环境变量或设置项 `plugins.official_git` 指定的地址拉取；拉不到时用安装包里自带的快照。
SFW 仓库里的 `src/sfw/plugins/sfw-official/` 是安装包自带的那份，发版前要和这里保持一致。
