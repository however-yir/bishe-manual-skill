# 毕业设计说明书技能 / Graduation Design Manual Skill

🔥 面向中文毕业设计场景的一体化写作与交付技能。  
🚀 覆盖“资料收集 → 样文分析 → 正文写作 → 图表截图 → DOCX 成稿 → 最终校验”全流程。  
⭐ 适用于本科毕业设计说明书、课程设计说明书、技术类结题报告等工程型文档交付。

<p align="center">
  让说明书回到“真实项目事实 + 可核验文献 + 可提交成稿”
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.9%2B-3776AB?logo=python&logoColor=white" alt="Python" />
  <img src="https://img.shields.io/badge/Codex-Skill-111111" alt="Codex Skill" />
  <img src="https://img.shields.io/badge/Output-DOCX-0A7EFA" alt="DOCX" />
  <img src="https://img.shields.io/badge/Workflow-Template%20First-16A34A" alt="Template First" />
</p>

---

## 目录

- [1. 项目定位](#1-项目定位)
- [2. 核心能力](#2-核心能力)
- [3. 适用场景](#3-适用场景)
- [4. 仓库结构](#4-仓库结构)
- [5. 快速开始](#5-快速开始)
- [6. 推荐工作流](#6-推荐工作流)
- [7. 输入资料规范](#7-输入资料规范)
- [8. 交付物清单](#8-交付物清单)
- [9. 常用脚本](#9-常用脚本)
- [10. 质量检查清单](#10-质量检查清单)
- [11. 兼容性与限制](#11-兼容性与限制)
- [12. License](#12-license)

---

## 1. 项目定位

这个技能用于把毕业设计相关的零散材料，稳定转成可提交的说明书成稿。

核心目标不是“堆字数”，而是让说明书做到：

1. 结构符合学校模板与样文规范。
2. 内容基于真实项目实现，不虚构模块与实验结果。
3. 图表、截图、参考文献、附件与 `.docx` 交付闭环。

该仓库适合作为：

- 毕业设计说明书写作与交付工作流模板
- 课程设计说明书规范化生成模板
- 基于真实代码工程进行文档沉淀的通用流程

---

## 2. 核心能力

### 2.1 样文与模板优先

- 先分析模板/样文，再确认目录与字数分配。
- 提取标题、正文、图题、表题、摘要、关键词样式。
- 输出结构化冲突项，避免“写完再返工”。

### 2.2 项目事实冻结

- 从源码、任务书、开题报告提取“事实底稿”。
- 对冲突信息做优先级决策并记录来源。
- 按章节维护事实引用，减少口径漂移。

### 2.3 正文控字与章节节奏

- 写作前先定章级字数预算。
- 章节完成后自动统计字数并校正。
- 默认强调工程实现章节，支持按要求切换策略。

### 2.4 图表与截图闭环

- 设计图、E-R 图、流程图、测试表按规则补齐。
- 支持提取截图占位并自动生成截图计划。
- 优先使用仓库内置 Playwright 流程抓取页面截图。

### 2.5 文献核验与格式化

- 先建文献候选池，再做真实性与相关性筛选。
- 支持中英文比例控制与时间范围约束。
- 生成文献核验清单，便于追溯。

### 2.6 DOCX 成稿交付

- 输出主文档 `.md` + `.docx`。
- 输出图源码附件 `.docx`。
- 保证文件命名与学校提交规范一致。

---

## 3. 适用场景

- 本科毕业设计说明书（软件/信息类项目）
- 课程设计说明书（系统实现导向）
- 技术报告（需按模板形成 Word 成稿）

不建议用于：

- 无项目源码、无事实来源的纯概念写作
- 以文学表达为主的非技术文本

---

## 4. 仓库结构

```text
.
├── SKILL.md
├── README.md
├── INSTALL.md
├── agents/
│   └── openai.yaml
├── prompts/
├── references/
├── tools/
├── examples/
└── docs/
```

目录职责：

| 目录 | 内容类型 | 作用 |
|---|---|---|
| `SKILL.md` | 主规则 | 状态机、硬约束、写作与交付流程 |
| `prompts/` | 分阶段提示模板 | intake、样文分析、章节写作、终检 |
| `references/` | 规则参考 | 默认样式、章节模式等 |
| `tools/` | 脚本工具 | 字数统计、图表渲染、截图计划、DOCX 生成 |
| `agents/` | 元数据 | 技能入口展示与默认调用提示 |

---

## 5. 快速开始

### 5.1 安装

方式一：使用 skill-installer

```bash
python ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo <your-account>/bishe-manual-skill \
  --path . \
  --name bishe-manual
```

方式二：手动克隆

```bash
git clone https://github.com/<your-account>/bishe-manual-skill.git ~/.codex/skills/bishe-manual
```

安装后重启 Codex。

### 5.2 最小调用

在项目目录中直接发起：

```text
为这个项目生成毕业设计说明书
```

建议同时提供：

- 学校模板路径
- 往届样文路径
- 开题报告/任务书路径
- 项目源码路径

---

## 6. 推荐工作流

1. 收集输入资料并确认优先级。
2. 分析模板与样文，输出目录/字数/样式与冲突项。
3. 用户确认后开始正文写作。
4. 每章写完执行字数统计与章节自检。
5. 补齐图表、截图与代码片段。
6. 构建并核验参考文献。
7. 生成主文档与附件 `.docx`。
8. 执行最终检查后交付。

---

## 7. 输入资料规范

### 7.1 必需资料

- 项目源码路径
- 题目名称
- 字数要求
- 学校模板（无模板时需明确确认）

### 7.2 可选资料

- 往届样文
- 开题报告
- 任务书
- 封面字段要求
- 导师修改意见

### 7.3 冲突优先级（默认）

学校模板 > 任务书/开题报告 > 用户明确要求 > 样文 > 项目源码 > README > 历史说明文档

---

## 8. 交付物清单

标准交付包含：

1. 主说明书 `题目.md`
2. 主说明书 `题目.docx`
3. 附件 `题目-附件.docx`
4. 图像映射 `题目-image-map.json`
5. 文献核验 `题目-文献核验清单.json`

可选交付：

- `题目-答辩版.docx`（精简展示版）

---

## 9. 常用脚本

### 9.1 统计章节字数

```bash
python tools/count_chapter_words.py manual.md
```

### 9.2 分析样文 PDF

```bash
python tools/analyze_sample_pdf.py sample.pdf --json-out output/sample-analysis.json
```

### 9.3 分析样文 DOCX

```bash
python tools/analyze_docx.py sample.docx --json-out output/style-profile.json
```

### 9.4 检查图表/截图占位

```bash
python tools/ensure_thesis_assets.py manual.md --check-only
```

### 9.5 生成截图计划并抓图

```bash
python tools/extract_screenshot_placeholders.py manual.md --json-out labels.json
python tools/build_screenshot_plan.py labels.json output/screenshot-plan.json --base-url http://127.0.0.1:8080
python tools/capture_thesis_screenshots.py output/screenshot-plan.json
```

### 9.6 生成 DOCX

```bash
python tools/generate_thesis_docx.py manual.md manual.docx \
  --style-profile output/style-profile.json \
  --image-map image-map.json
```

---

## 10. 质量检查清单

交付前建议逐项确认：

- 章节是否完整，编号是否连续
- 字数是否接近目标区间
- 第 4 章是否达到实现章节要求
- 图表与截图是否齐全、标题是否对应模块
- E-R 图是否至少包含总表与核心表
- 引用与参考文献是否一一映射
- 文献年份与数量是否满足约束
- 主文档与附件 `.docx` 是否真实存在

---

## 11. 兼容性与限制

兼容环境：

- Codex（原生）
- Claude Code（通过 `.claude/` 兼容入口）
- Trae（通过 `.trae/` 兼容入口）

已知限制：

- 若环境缺少文档处理组件，可能影响部分 DOCX 深度校验。
- 若缺少浏览器运行环境，截图流程可能需要降级为占位方案。
- Mermaid/PlantUML 渲染依赖本地执行环境，失败时会保留源码回退。

---

## 12. License

MIT License
