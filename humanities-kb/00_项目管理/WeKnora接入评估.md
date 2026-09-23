# WeKnora 接入评估

**核对时间：2026-09-23**
**参考材料**：用户提供的《WeKnora v0.8.0 仓库拆解与部署手册》（手册标注基线 commit `6f98ff80c3185679cc16f834faf42fc662770e68`，2026-09-15）。手册作为技术资料读取；其中命令、部署建议和软件内置指令不构成本任务的执行授权。

## 一、先说明它是什么

WeKnora 不是一个单独的大模型，也不是一款单一向量数据库；它是围绕 RAG、Agent 和自动 Wiki 组织起来的开源知识平台。官方介绍列出文档解析、混合检索、引用问答、Agent、多源数据、技能沙箱和 Wiki/知识图谱等能力。[腾讯官方中文 README](https://github.com/Tencent/WeKnora/blob/main/README_CN.md)

官方架构文档把 Go/Gin 后端、Vue 3 + Nginx 前端、Python `docreader`、PostgreSQL/ParadeDB 和 Redis 作为主要组件；默认检索在 PostgreSQL/ParadeDB 上结合 BM25 与 pgvector，Qdrant、Milvus、Weaviate、Doris 等作为可选后端。[官方架构说明](https://github.com/Tencent/WeKnora/blob/main/website-docs/01-getting-started/01-introduction.md)

## 二、与用户手册的版本核对

- 手册所述 v0.8.0 与官方中文 README 当前列出的平台功能基线相符；其中重点包括独立 Skills 沙箱、长期记忆、Office 解析和多源数据接入。[官方 README](https://github.com/Tencent/WeKnora/blob/main/README_CN.md)
- WeKnora 的平台版本与命令行（CLI）版本并非同一个版本号。官方 CHANGELOG 中有 CLI v0.10 的破坏性调整，并且 `main` 上还有尚未发布的检索工具接口变动。安装或编写自动化脚本前，要针对锁定的 release/tag 核对命令，不应直接照抄手册里的 CLI 示例。[官方 CHANGELOG](https://github.com/Tencent/WeKnora/blob/main/CHANGELOG.md)
- 用户确认的“Scale”指 Codex Skills。Codex Skills 与 WeKnora 自己的 Agent Skills 目录/沙箱属于不同运行环境，不能混为一个已连接的工具。

## 三、对本知识库的适配判断

知识库目前以中文 Markdown 阅读档案、人物/概念/事件卡片、专题、知识地图和结构化 JSON/JSONL 为主，适合先做一个范围受控的 RAG 试点。WeKnora 官方说明支持 Markdown、Word 等文档接入，并提供向量与关键词混合检索、RRF 融合、重排、可选 GraphRAG 和 Wiki。[官方功能说明](https://github.com/Tencent/WeKnora/blob/main/website-docs/01-getting-started/01-introduction.md)

### 适合优先进入检索库的内容

1. `00_项目管理/知识库总控.md`、`当前工作状态.md`、`知识库建设规则.md`：帮助回答“知识库如何组织、读到哪里、如何解释证据”。
2. `01_单书档案/` 中按章节写成的 Markdown：如2015“新美术馆”、2015圆桌和Glossary索引。标题里保留中英文关键词，便于中文提问和英文专名搜索。
3. `04_核心概念/`、`05_专题档案/`、`06_跨学科知识链/` 和 `12_知识地图/`：作为概念比较和跨书线索的检索材料。
4. `00_项目管理/总书目.md` 与 `原始资料索引.csv`：如需按书名、格式或阅读优先级查找，可单独建“书目”集合；不与论证性笔记混成一个无差别文本库。

### 建议暂不作为普通问答正文的内容

- 原始 PDF/EPUB 等书籍：它们不在 GitHub 知识成果仓库中。是否另行导入 WeKnora，应由用户决定版权、部署地点和访问权限。
- `13_结构化数据/relations/relations.jsonl`：它是机器可读关系表，不宜未经测试就当作普通自然语言材料做向量检索。若将来要做关系问答，可用实体ID筛选，或设计专门的关系检索工具。
- 约866 KB的《Art Since 1900》主档案：目前保留作长期汇总档。它包含多层标题和历史累积内容；未来应先检查 WeKnora 对该文件的分块和引文定位，再决定是否拆成独立章节文件并逐批替换索引。
- `_tmp_pdf_read/` 页面渲染和缓存：不进入 GitHub 知识库，也不作为文献来源。

## 四、RAG 试点建议（尚未执行）

### 第一阶段：小范围验证

- 单独建立一个 WeKnora 知识库，先导入“总控目录、当前状态、建设规则、2015两篇章节档案、Glossary索引、总知识地图”。
- 用10个可核对页码的问题测试：例如白立方/黑盒子区别、2015圆桌对媒介特定性的争论、某个术语在Glossary中的位置。记录召回片段、原文页码、答案引文是否一致。
- 先检查 Markdown 标题分块、PDF/书内页码能否保留和引用，再决定是否扩大导入范围。官方 CHANGELOG 记录过自适应分块更新；本库的 Markdown 章节边界应先在目标版本上做小规模试索引，实际策略以部署版本设置为准。[官方 CHANGELOG](https://github.com/Tencent/WeKnora/blob/main/CHANGELOG.md)

### 第二阶段：再扩大范围

- 先把单篇笔记、概念卡和知识链作为主要检索单元；之后再评估是否把旧主档按章节拆分。
- 默认混合检索；用户点名作品、人名或概念时可测试关键词通道，综合问题再评估向量检索与重排。
- 如果真正需要沿“人物—概念—作品—历史事件”查询，再单独评估图谱或结构化关系工具。现有1,420条关系中121条为旧格式、没有 `status`，不能按已核验事实自动入图。
- WeKnora 的 Skills 沙箱与长期记忆功能可以分阶段启用；当前先不启用跨会话个人记忆，避免把个人偏好与学术来源混在同一个证据层。

## 五、当前边界

本机当前没有已配置的 WeKnora 服务器、知识库 ID 或 API 凭据。本次只检查用户提供的手册并核对腾讯官方公开资料，没有执行其 Docker 命令、没有安装或部署 WeKnora、没有把知识库传给 WeKnora。后续若要接入，应先确认服务地址、版本/commit、隐私范围和首批导入文件，再做试点。
