# dsh-memory-handover

> DeepSeek Harness（DSH）技能：会话记忆与交接。会话结束前一键把进度沉淀到 `Memory_DSH.md`，下个会话无缝接续。

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

## 这是什么

`memory-handover` 是一个 [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness)（DSH）技能（skill）。它把「每个会话结束前手动记交接」这件事标准化成一条固定流程，每次固定记五件事：

1. **什么时候、在做什么任务**
2. **已经完成了什么**
3. **当前卡在哪**
4. **下一步计划**
5. **踩过的坑（绝对不要踩）**

全部写入一份 `Memory_DSH.md`。下一个会话开头说「读一下 Memory_DSH.md 接续」，即可恢复上下文。

## 安装

把整个目录放到 DSH 的全局技能目录（`~/.dsh/skills/`）：

```bash
# 方式一：git clone
git clone https://github.com/OolleyW/dsh-memory-handover.git ~/.dsh/skills/memory-handover

# 方式二：手动复制 SKILL.md
mkdir -p ~/.dsh/skills/memory-handover
cp SKILL.md ~/.dsh/skills/memory-handover/
```

> Windows 下 `~/.dsh/skills` 即 `C:\Users\<你>\.dsh\skills`。DSH 会 watch 该目录，放进去即时生效，无需重启。

## 使用

- **点按钮**：输入框下方「技能」→ 选 `memory-handover`；或直接输入 `/memory-handover`。（前提：已安装 `dsh-skill-manager` 插件，否则 GUI 上没有「技能」按钮）
- **更省事**：会话里直接说「**保存记忆**」「**交接一下**」「**接续一下**」，模型会按 `whenToUse` 自动触发。

## 交接文件放哪

默认写**当前工作区根目录**的 `Memory_DSH.md`。若你一直用某个固定路径（如 `E:\DSH_work\Memory_DSH.md`），技能会沿用该路径，不会另建新文件。

## 五件事

| # | 记什么 | 说明 |
|---|---|---|
| 1 | 什么时候、在做什么 | 任务主线 + 带日期的时间线 |
| 2 | 已完成什么 | 具体产物：文件、命令、结果数字 |
| 3 | 卡在哪 | 硬阻塞 / 未闭环点 / 遗留待办 |
| 4 | 下一步计划 | 按优先级可执行 |
| 5 | 踩过的坑 | 逐条，写清为什么 + 怎么避免 |

## License

[MIT](LICENSE) © 2026 OolleyW
