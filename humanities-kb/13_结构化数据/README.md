# 结构化数据层

本目录为 Markdown 知识库的机器可读补充。截至2026-09-25已累计1343个实体、1628条关系；其中1507条为status=verified，覆盖部分已实际阅读章节；不是全书实体迁移或完整知识图谱。历史JSON可能含与Markdown重复的长说明和related字段；121条旧关系未标status，不自动视为verified。旧文件继续保留，新结构按轻量实体和少量有来源关系自然累积。
## 目录

- books / people / concepts / events / movements / artworks / topics：独立 JSON 实体。
- relations/relations.jsonl：一行一条、有来源的关系。

## 约定

- 实体 ID 使用稳定小写英文 snake_case，并与文件名主干对应。
- 未由项目材料确认的字段留空字符串或空数组；不以模型常识补全。
- 每个关系都应包含 source、evidence_type、confidence。
- evidence_type 仅使用 author_explicit、textual_summary、cross_book_interpretation、ai_inference。
- confidence 描述当前项目材料对关系的支持程度，不是真实性评分。
- concepts.definitions 分作者记录，不把不同思想家的概念压成统一定义。
- movements 中的“纽约摄影学派”“西海岸组装艺术”按章节中的批评分类记录；若来源未证明其为正式组织，不推断其有成员制度或共同宣言。
- relations 中关系类型优先使用规范词表：influenced_by、influenced、criticizes、responds_to、develops、inherits、opposes、contemporary_of、related_to、derived_from、contrasts_with、extends、redefines、historically_related_to、causes、contributes_to、emerges_from、accelerates、transforms、influences_art_movement、influences_artist、responds_to_event、uses_concept、challenges、associated_with、supports、compares_with。必要时可使用少量明确的新词，如 created_by、collaborated_with、studied_under、co_founded_with、interprets、represented_in、discusses、author_of、draws_on、commissioned、features、supported_by、signed、joined、names、articulates、marks_formation_of、marks_institutional_acceptance_of。
- 来源优先包含书名、章节作者、章节标题、书内页码、PDF页码和可定位段落/图注。
- Markdown档案仍是主要的人类可读记录；结构化实体与关系不得替代、覆盖或削弱原笔记。

### 2026-09-25：《文化生产：媒体与都市艺术》

- 新增1本书、1位作者和5个概念实体；新增10条有来源关系，复用既有“文化资本”实体。
- 跨书关系标为cross_book_interpretation；不把克兰关于战后美国媒体的分析推广为所有国家和时代的普遍规律。
- JSON/JSONL解析、关系端点和重复三元组已在入库前核验。

### 2026-09-25：《艺术的法则》整本阅读

- 新增1个书籍实体、5个概念实体及10条带来源关系；复用既有文化资本实体。
- 关系包括作者与书、正文概念关系，以及与《历史资本主义》《开放社会科学》《Art Since 1900》的跨书比较；跨书记录标注为解释，不归为布迪厄原话。
- JSON/JSONL解析、关系端点与重复三元组核验通过；整本论证和阅读位置见单书档案。

## 文件状态

已录数据依据下列本地原书页码：
- Yve-Alain Bois, “1959b: Assemblage,” book pp.477–482 / PDF pp.481–486.
- Rosalind Krauss, “1959c: Postwar figuration,” book pp.483–487 / PDF pp.487–491.
- Benjamin H. D. Buchloh, “1959d: New York School photography,” book pp.488–493 / PDF pp.492–497.

relations.jsonl 的每行均独立校验为 JSON；新增关系需避免重复，并保留证据层级。
- Yve-Alain Bois, “1959e: The Manifesto of Neoconcrete Art is published,” book pp.494–501 / PDF pp.498–505.

## 轻量化规则（2026-09-21起）

- Markdown仍是阅读、论证和跨书研究的主体；新增JSON只保存稳定标识、名称和必要的基本属性，不复制长摘要，不继续扩张related_*数组。
- relations.jsonl优先保存少量高价值、带明确文本位置的关系；新关系必须带status。正式入库的记录使用`status: "verified"`；候选关系不进入正式文件，除非另行明确标记为`candidate`并说明待核内容。
- 旧实体和关系保持原样。2026-09-21简短审计时，旧数据为95个实体、121条关系；所有旧关系有source字段，但均无status，其中26条是通用模板式描述。它们是历史数据，不能仅因存在于文件中就视为按新规则verified；不批量改写或迁移。
- 新关系的source尽可能包含book、author、chapter、page及location；confidence只表示当前项目文本支持程度。
- 新关系类型优先复用既有词表。确需细分时可增少量精确词，如organized、launched、negotiates、repositions；不得为同义关系重复造词。

新增章节来源：
- 古本根重建社会科学委员会，《开放社会科学：重建社会科学报告书》，1997年三联书店版；第一至第四章书内pp.1–113 / PDF pp.9–116。新增报告书、委员会主席、欧洲中心主义与学术客观性的轻量实体，并把跨学科重建、普遍主义批判与客观性主张接入现有图谱。
- 《Art in Theory 1900–2000》第二版正文八部及书后书目、版权致谢、索引已全部核读，读至书内p.1258 / PDF p.1286；完整进度见[整本阅读档案](../01_单书档案/Art%20in%20Theory%201900-2000整本阅读档案.md)。本结构化层仍只覆盖实际入库且逐条列明来源的章节，不代表整本书已转换为实体关系图谱。本次累计补录涉及艺术原生性（Art Brut）、媒介特定性、特定物与维护艺术；新增关系仍按下方各条目记录来源和状态。
- Benjamin H. D. Buchloh, “1960a: Nouveau Réalisme,” book pp.504–508 / PDF pp.508–512.
- Rosalind Krauss, “1960b: Greenberg's modernism,” book pp.509–514 / PDF pp.513–518.

- Hal Foster, “1960c: American Pop art,” book pp.515–519 / PDF pp.519–523.

- Yve-Alain Bois, “1961: Oldenburg and happenings,” book pp.520–525 / PDF pp.524–529.

- Benjamin H. D. Buchloh, “1962a: Fluxus,” book pp.526–533 / PDF pp.530–537：新增少量人物、运动、概念和事件身份实体；新增关系均有原文位置、证据类型、confidence及`status: verified`。旧实体与旧关系未迁移或重写。

- Benjamin H. D. Buchloh, “1962b: Viennese Actionism,” book pp.534–539 / PDF pp.538–543：新增少量人物、运动、事件和概念身份实体；六条关系均带来源、证据类型、confidence与`status: verified`。


- Hal Foster, “1962c: Andre, Flavin, and LeWitt,” book pp.540–544 / PDF pp.544–548：新增俄国构成主义与三位艺术家的轻量实体；三条关系均有章节来源和`status: verified`。
- Rosalind Krauss, “1962d: The abstract side of Pop art,” book pp.545–550 / PDF pp.549–554：新增Johns及本章核心概念的轻量身份实体；仅补入两条有章节位置、证据类型、confidence与`status: verified`的高价值关系。旧记录未批量迁移。
- Benjamin H. D. Buchloh, “1963: Baselitz and Schönebeck,” book pp.550–555 / PDF pp.555–559：新增少量人物、事件与概念身份实体；新增关系仅记录宣言合作、章节明示的艺术模式对照、Habermas理论应用及展览事件的章节解释，均带来源与`status: verified`。
- Benjamin H. D. Buchloh, “1964a: Beuys,” book pp.556–561 / PDF pp.560–565：新增Beuys、Duchamp、亚琛事件、核心作品与记忆美学的轻量实体；新增关系聚焦记忆美学、奇观、Fluxus差异、Duchamp回应和作品证据。
- Hal Foster, “1964b: Warhol,” book pp.562–567 / PDF pp.566–571：新增两个轻量概念实体和《Thirteen Most Wanted Men》实体；新增四条聚焦创伤重复、大众主体及作品出处的verified关系。
- Rosalind Krauss, “1965: Judd, Morris, and Minimalism,” book pp.568–571 / PDF pp.572–575：新增Judd、Morris、Fried、极简主义、特定物和Primary Structures展览的轻量身份实体；五条关系记录理论阐述、媒介批评和运动形成，均有来源与`status: verified`。




### 2026-09-22轻量审计

- 审计现状：182个实体、199条关系；95个实体JSON文件超过500字节，部分旧文件保存了较长说明和related_*关系字段，存在与Markdown重复的风险。relations.jsonl中121条旧记录没有status；所有记录仍有source字段且当前可解析，其中早期审计发现26条使用通用模板式描述。缺status的旧记录不视为新规则下的verified。旧文件及旧关系全部保留，不作批量迁移。
- 后续新增采用身份字段为主的轻量JSON，研究叙述留在Markdown；只添加少量能由刚读文本定位的关系，并标注source、evidence_type、confidence及status。
- 本次1966a新增4个身份实体、4条verified关系；未把章节中提到的所有艺术家和概念自动扩成节点。


- Hal Foster，“1966b: Bourgeois, Hesse, and Kusama”，book pp.576–580 / PDF pp.580–584：新增三位艺术家、展览、两件展出作品、策展相关人物和“偏心抽象”概念的身份实体；新增关系限于展览、作品归属及章节核心分类。


- Yve-Alain Bois，“1967a: Smithson and entropy”，book pp.581–584 / PDF pp.585–588：新增熵及三位核心人物和Passaic摄影游记的身份实体；关系聚焦熵、极简主义批评、艺术家回应及作品证据。


- Benjamin H. D. Buchloh，“1967b: Arte Povera”，book pp.585–590 / PDF pp.589–594：新增运动、首展、核心人物、概念及《12 Cavalli》轻量实体；关系记录命名／首展、运动形成、材料概念及具名作品证据。
- Yve-Alain Bois, “1967c: French Conceptualist painting,” book pp.591–596 / PDF pp.595–600：新增BMPT、联合行动、核心人物和指示符轻量实体；新增9条少量、可追溯的verified关系。
- Benjamin H. D. Buchloh, “1968a: The Bechers,” book pp.597–602 / PDF pp.601–606：新增核心摄影家与概念轻量实体；新增9条带来源的verified关系。
- Benjamin H. D. Buchloh, “1968b: Conceptual art,” book pp.603–609 / PDF pp.607–613：新增观念艺术及其核心参与者和概念轻量实体；新增14条可追溯的verified关系。
- Hal Foster, “1969: Postminimalism and Process,” book pp.610–613 / PDF pp.614–617：新增过程艺术核心概念和Serra轻量实体；新增13条有来源的verified关系。
- Rosalind Krauss, “1970: Site-specific art,” book pp.616–620 / PDF pp.620–624：新增场址特定艺术、扩展场域及Pomona项目身份节点；新增14条带章节位置的verified关系。


### 2026-09-22轻量化复核（1971条目后）

- 复核范围：单书档案、人物／事件／概念／专题Markdown、总知识地图、全部实体JSON与relations.jsonl。Markdown继续承担完整论证与证据记录；结构化层仅追加身份节点和少量关系。
- 当前实体255个旧节点 + 6个本次新增节点 = 261；关系287条旧记录 + 8条本次新增 = 295。95个旧JSON文件超过500字节，且都含related_*字段，存在与Markdown重复；未改写或迁移。
- 关系中121条旧记录缺status，保留为未按新规则核验的历史记录；166条旧verified记录与8条新增verified记录共174条有状态关系。所有295条当前均有source；新关系均有来源位置、evidence_type、confidence和status。
- 当前文件无重复三元组、悬空实体引用或JSON/JSONL解析错误。relations.jsonl暂无candidate记录；候选关系不自动入正式图谱。
- 后续继续采用：Markdown做深、实体JSON做轻、relations优先精确与可追溯；旧数据保持原样，逐本自然过渡，不作批量迁移。

新增章节来源：Benjamin H. D. Buchloh，“1971: Early institutional critique”，*Art Since 1900*, 3rd ed., book pp.621–624 / PDF pp.625–628。


### 2026-09-22轻量化复核（1972a条目后）

- 累计266个实体、303条关系；其中121条旧关系缺status，182条关系为带状态的verified记录。新增的1972a关系均提供章节页码／定位、evidence_type、confidence和status。
- 95个早期大于500字节的实体JSON均含related_*字段，继续保留但不当作已核验研究关系；没有进行批量迁移或重写。
- JSON/JSONL后续检查应继续核对解析、关系端点和重复三元组；机器候选关系需与verified分开。

新增章节来源：Benjamin H. D. Buchloh，“1972a: Marcel Broodthaers installs his ‘Musée d’Art Moderne, Département des Aigles, Section des Figures,’ in Düsseldorf, West Germany”，*Art Since 1900*, 3rd ed., book pp.625–629 / PDF pp.629–633。


### 2026-09-22轻量化复核（1972b条目后）

- 累计274个实体、313条关系；121条早期关系仍缺status，192条关系为带状态的verified记录。本篇新增关系带章节位置、evidence_type、confidence及status；为准确表示章节所说“Documenta 5标志欧洲观念艺术制度接受”，关系词表增加`marks_institutional_acceptance_of`这一精确类型。
- 早期95个大于500字节且包含related_*字段的实体JSON均保留；没有批量简化或迁移。Markdown继续承担论证、比较和原文位置。

新增章节来源：Benjamin H. D. Buchloh，“1972b: Documenta 5”，*Art Since 1900*, 3rd ed., book pp.630–635 / PDF pp.634–639。

### 2026-09-22轻量化复核（1972c条目后）

- 累计283个实体、321条关系；121条早期关系缺status，200条关系为有状态的verified记录。1972c新关系均有章节位置及证据字段。
- 新增关系复用既有类型：author_of、articulates、contrasts_with、influences_art_movement、transforms；没有复制长摘要进实体JSON。
- 原有95个较大且含related_*字段的实体JSON继续保留，不作批量迁移。

新增章节来源：Hal Foster，“1972c: Postmodern architecture”，*Art Since 1900*, 3rd ed., book pp.636–643 / PDF pp.640–647。

### 2026-09-22轻量化复核（1973条目后）

- 累计290个实体、328条关系；121条旧关系缺status，带状态verified关系为207条。本篇新增关系采用现有类型，记录章节位置、证据类型、confidence和状态。
- 新增实体仅用于视频艺术、The Kitchen开设空间、关键作品和“即时性／中介”概念；理论分析与跨书比较保留在Markdown。

新增章节来源：Hal Foster，“1973: Early video art”，*Art Since 1900*, 3rd ed., book pp.644–648 / PDF pp.648–652。

### 2026-09-22轻量化复核（1974条目后）

- 累计302个实体、346条关系；121条早期关系仍缺status，225条关系为有状态的verified记录。1974新增关系均带章节页码、evidence_type、confidence和status。
- 新增实体限于身体艺术、三位核心案例艺术家、Ono、五件作品及两个核心概念；详细论证留在Markdown。
- 旧的较大JSON与无status关系继续保留，不作批量迁移；后续只自然追加经文本核实的轻量节点和核心关系。

新增章节来源：Hal Foster，“1974: American Performance art”，*Art Since 1900*, 3rd ed., book pp.649–653 / PDF pp.653–657。

### 2026-09-22轻量化复核（1975a条目后）

- 累计323个实体、377条关系；121条早期关系仍缺status，256条关系为有状态的verified记录。1975a新增关系均带章节页码、evidence_type、confidence和status。
- 新增节点限于女性主义艺术、关键组织事件、核心艺术家、作品和少量概念；理论期刊、完整论证与阶段差异留在Markdown。
- 旧JSON与无status关系继续保留，不作批量迁移。

新增章节来源：Hal Foster，“1975a: Feminist art”，*Art Since 1900*, 3rd ed., book pp.654–659 / PDF pp.658–663。

### 2026-09-22轻量化复核（1975b条目后）

- 累计347个实体、410条关系；121条早期关系仍缺status，289条关系为有状态的verified记录。1975b新增关系均带章节页码、evidence_type、confidence和status。
- 新增节点限于莫斯科概念主义、Sots Art、非官方艺术网络、核心艺术家、作品和少量概念；完整历史背景、比较与不确定性留在Markdown。
- 旧JSON与无status关系继续保留，不作批量迁移。

新增章节来源：David Joselit，“1975b: Moscow Conceptualism”，*Art Since 1900*, 3rd ed., book pp.660–667 / PDF pp.664–671。

### 2026-09-22轻量化复核（1976条目后）

- 累计367个实体、438条关系；121条早期关系仍缺status，317条关系为有状态的verified记录。1976新增关系均带章节页码、evidence_type、confidence和status。
- 新增节点限于替代空间网络、公共资助／展览事件、全球博物馆相关人物和少量制度概念；完整制度论证留在Markdown。
- 旧JSON与无status关系继续保留，不作批量迁移。

新增章节来源：Rosalind Krauss，“1976: The institutional structure of art”，*Art Since 1900*, 3rd ed., book pp.668–671 / PDF pp.672–675。

### 2026-09-22轻量化复核（1977a条目后）

- 累计401个实体、468条关系；121条早期关系仍缺status，347条关系为有状态的verified记录。1977a新增关系均带章节页码、evidence_type、confidence和status。

新增章节来源：Rosalind Krauss，“1977a: The ‘Pictures’ exhibition”，*Art Since 1900*, 3rd ed., book pp.672–675 / PDF pp.676–679。

### 2026-09-22轻量化复核（1977b条目后）

- 累计434个实体、500条关系；121条早期关系仍缺status，379条关系为有状态的verified记录。1977b新增关系均带章节页码、evidence_type、confidence和status。

新增章节来源：David Joselit，“1977b: Queer art”，*Art Since 1900*, 3rd ed., book pp.676–685 / PDF pp.680–689。

### 2026-09-22轻量化复核（1980条目后）

- 累计459个实体、526条关系；121条早期关系仍缺status，405条关系为有状态的verified记录。1980新增关系均带章节页码、evidence_type、confidence和status。

新增章节来源：Hal Foster，“1980: The simulacral image”，*Art Since 1900*, 3rd ed., book pp.688–691 / PDF pp.692–695。

- Benjamin H. D. Buchloh，“1984a: Photoconceptualism”，book pp.692–697 / PDF pp.696–701：新增轻量人物、事件、运动、概念、作品及专题实体；新增关系聚焦摄影的指示性、发行多重物、城市公共空间、政治纪实语境和系列性，均带source、evidence_type、confidence及status=verified。篇章页眉正式标记为1984a；1981年Burgin讲座作为首段时间背景记录。


### 2026-09-22轻量化复核（1984a条目后）

- 累计484个实体、563条关系；442条关系为有状态的verified记录，121条旧关系仍缺status。1984a新增关系均带source、evidence_type、confidence和status=verified；JSON/JSONL解析、关系端点和重复三元组检查通过。

### 2026-09-22轻量化复核（1984b条目后）

- 累计506个实体、597条关系；476条关系为有状态的verified记录，121条旧关系仍缺status。1984b新增关系均带source、evidence_type、confidence和status=verified；JSON/JSONL解析、关系端点和重复三元组检查通过。

### 2026-09-22轻量化复核（1986条目后）

- 累计534个实体、635条关系；514条关系为有状态的verified记录，121条旧关系仍缺status。1986新增关系均带source、evidence_type、confidence和status=verified；JSON/JSONL解析、关系端点和重复三元组检查通过。

- Hal Foster，“1987: Activist art”，*Art Since 1900*, 3rd ed., book pp.707–713 / PDF pp.711–717：新增行动主义艺术、AIDS行动与酷儿美学相关的轻量实体；58条新增关系均带source、evidence_type、confidence及status=verified。

- Benjamin H. D. Buchloh，“1988: Richter and Kiefer”，*Art Since 1900*, 3rd ed., book pp.714–718 / PDF pp.718–722：新增战后德国历史、媒介中介、Richter／Kiefer与Habermas相关的轻量实体；25条新增关系均带source、evidence_type、confidence及status=verified。

- Hal Foster，“1989: Les Magiciens de la terre”，*Art Since 1900*, 3rd ed., book pp.719–723 / PDF pp.723–727：新增后殖民艺术、杂糅、Dreamtime与制度批判相关的轻量实体；33条新增关系均带source、evidence_type、confidence及status=verified。

- Hal Foster，“1992: The anthropological model”，*Art Since 1900*, 3rd ed., book pp.726–731 / PDF pp.730–735：新增民族志转向、项目艺术、社会学制图和策展角色相关的轻量实体；30条新增关系均带source、evidence_type、confidence及status=verified。

- Rosalind Krauss，“1993a: The critique of visuality”，*Art Since 1900*, 3rd ed., book pp.732–736 / PDF pp.736–740：新增视觉性、凝视、后像和视觉批判相关的轻量实体；31条新增关系均带source、evidence_type、confidence及status=verified。

- Hal Foster，“1993b: Postminimalism revisited”，book pp.737–740 / PDF pp.741–744：新增少量英国女性艺术家、后极简主义、社会身体、负空间铸造及《House》事件实体；新增关系均有章节位置、证据类型、confidence与`status: verified`。
- Hal Foster，“1993c: Politicized black art”，book pp.741–746 / PDF pp.745–750：新增政治化身份、纪实类型学、种族可读性、黑人艺术与代表作品实体；新增关系均有章节位置、证据类型、confidence与`status: verified`。
- Hal Foster，“1994a: Abject art”，book pp.747–751 / PDF pp.751–755：新增卑贱物、创伤、回归、破碎身体及代表作品实体；新增关系均有章节位置、证据类型、confidence与`status: verified`。
- Rosalind Krauss，“1994b: The resurgence of drawing”，book pp.752–755 / PDF pp.756–759：新增矩阵、字形、擦除和技术压力概念，以及LeWitt、Pettibon、Kentridge作品实体；新增关系均有章节位置、证据类型、confidence与`status: verified`。
- David Joselit，“1997: South African photography”，book pp.756–763 / PDF pp.760–767：新增南非摄影、种族隔离视觉性、黑人都市现代性、回望凝视及代表作品／事件实体；新增关系均有章节位置、证据类型、confidence与`status: verified`。

- Rosalind Krauss / Hal Foster，“1998: The projected image”，book pp.764–769 / PDF pp.768–773：新增少量投影艺术、媒介理论人物与作品身份实体；新增关系均有章节位置、证据类型、confidence与`status: verified`。

### 2026-09-22轻量化复核（1998条目后）

- 累计887个实体、1041条关系；121条旧关系仍缺status，920条关系为有状态的verified记录。1998新增39条关系均提供章节页码／定位、evidence_type、confidence和status。
- 本次新增实体保持轻量身份字段；章节的完整论证、概念差异、图版说明与AI推演留在Markdown。旧JSON和旧关系不迁移、不批量重写。
- JSON/JSONL解析、关系端点和重复三元组检查通过；当前无candidate记录。

- Hal Foster，“2001: Pictorial photography”，book pp.773–777 / PDF pp.777–781：新增少量数字摄影人物、概念、作品与事件身份实体；新增关系均有章节位置、证据类型、confidence与`status: verified`。

### 2026-09-22轻量化复核（2001条目后）

- 累计900个实体、1070条关系；121条旧关系仍缺status，949条关系为有状态的verified记录。2001新增29条关系均提供章节页码／定位、evidence_type、confidence和status。
- 本次实体继续采用轻量身份字段；完整论证、图版说明、数字摄影与资本空间的跨书问题留在Markdown。旧JSON与旧关系不迁移、不批量重写。
- JSON/JSONL解析、关系端点和重复三元组检查通过；当前无candidate记录。

- Hal Foster，“2003: Archival aesthetics”，book pp.778–783 / PDF pp.782–787：新增少量档案美学、后生产、协作与互动实践的人物、概念、作品和事件身份实体；新增关系均有章节位置、证据类型、confidence与`status: verified`。

### 2026-09-22轻量化复核（2003条目后）

- 累计924个实体、1106条关系；121条旧关系仍缺status，985条关系为有状态的verified记录。2003新增36条关系均提供章节页码／定位、evidence_type、confidence和status。
- 本次实体只保留身份字段；档案美学、互动美学的完整论证与作者对“开放形式=民主共同体”类比的警惕留在Markdown。旧JSON和旧关系不迁移、不批量重写。
- JSON/JSONL解析、关系端点和重复三元组检查通过；当前无candidate记录。

- Rosalind Krauss，“2007a: Marclay, Calle, Coleman, and Kentridge”，book pp.785–789 / PDF pp.789–793：新增少量后媒介状态、技术支撑、白立方与代表作品身份实体；新增关系均有章节位置、证据类型、confidence与`status: verified`。

### 2026-09-22轻量化复核（2007a条目后）

- 累计939个实体、1139条关系；121条旧关系仍缺status，1018条关系为有状态的verified记录。2007a新增33条关系均提供章节页码／定位、evidence_type、confidence和status。
- 本次实体继续采用轻量身份字段；后媒介状态、技术支撑、白立方专栏及Kentridge的历史语境留在Markdown。旧JSON和旧关系不迁移、不批量重写。
- JSON/JSONL解析、关系端点和重复三元组检查通过；当前无candidate记录。

- Benjamin H. D. Buchloh，“2007b: New sculpture”，book pp.790–797 / PDF pp.794–801：新增少量新雕塑、商品雕塑、物件积累人物、概念、作品和事件身份实体；新增关系均有章节位置、证据类型、confidence与`status: verified`。

### 2026-09-22轻量化复核（2007b条目后）

- 累计959个实体、1170条关系；121条旧关系仍缺status，1049条关系为有状态的verified记录。2007b新增31条关系均提供章节页码／定位、evidence_type、confidence和status。
- 本次实体保持轻量身份字段；商品雕塑、对象积累、消费与毁灭的完整论证留在Markdown。旧JSON和旧关系不迁移、不批量重写。
- JSON/JSONL解析、关系端点和重复三元组检查通过；当前无candidate记录。


## 最近审计

- 2007c“Art and the market”（Hal Foster，书内pp.798–803 / PDF pp.802–807）新增19个轻量实体和28条verified关系；关系来源均指向章节页码或Further reading。
- 旧的121条无status关系继续保留，未被自动提升为正式研究关系。

- 2009a“The art of social relations”（David Joselit，书内pp.804–809 / PDF pp.808–813）新增25条verified关系，来源均可回溯到章节页码。

- 2009b“Painting's social networks”（David Joselit，书内pp.810–817 / PDF pp.814–821）新增26条verified关系，来源指向章节页码和图注。

- 2009c“Media, new technologies, and images of war”（David Joselit，书内pp.818–823 / PDF pp.822–827）新增27条verified关系，来源指向章节页码和图注。

- 2010a“Chinese contemporary art”（David Joselit，书内pp.824–829 / PDF pp.828–833）新增28条verified关系，来源指向章节页码和图注。

- 2010b“The avatar as artistic strategy”（David Joselit，书内pp.830–835 / PDF pp.834–839）新增26条verified关系，来源指向章节页码和图注。

- Hal Foster, “2015: The new museums of art,” book pp.836–841 / PDF pp.840–845：新增来源限定人物、作品、事件与概念；仅纳入有明确章节页码的关系。历史旧关系保持原样。

- Krauss, Bois, Buchloh, Foster; Joselit added thoughts, “The predicament of contemporary art / Roundtable,” book pp.843–854 / PDF pp.847–858. Discussion originally December 2003; Joselit addition September 2010.

- *Art Since 1900* Glossary, book pp.857–865 / PDF pp.861–869: 76 headwords read; concise retrieval index added.

### 2026-09-23：当代艺术摄影与符号学前言

- 用户上传《当代艺术摄影与符号学》前言PDF pp.1–16已逐页视觉核读；作者和完整书目信息未在片段中确认。
- 新增轻量实体：`topic_contemporary_art_photography_semiotics`、`concept_anti_semiotics_image_as_subject`。
- 新增3条verified关系，只记录本片段明确支持的“当代艺术摄影—符号学”“当代艺术摄影—反符号学”及Galton复合肖像案例；更大的类型学／政治史解释留在Markdown并标为待核。

### 2026-09-23：当代艺术摄影与符号学05–06（叶尔姆斯列夫）

- 用户上传05（43页）与06（35页）已逐页视觉核读；课程以Hjelmslev为核心，但未提供完整原著出处，故结构化关系标记为课件来源限定。
- 新增轻量实体：Louis Hjelmslev、Mohamed Bourouissa、Taryn Simon，表达／内容平面、形式／实体／质料、过程／系统、依从关系，Hjelmslev专题，以及《R.I.P》《Shoplifters》《Paperwork, and the Will of Capital》《Blind Spot》等作品节点。
- 新增17条verified关系，优先记录理论概念、作品归属及课程实际用于分析的案例关系；未把艺术家与Hjelmslev之间写成影响关系。

### 2026-09-24：《20世纪60年代西方文化运动》

- 整本101页扫描PDF已逐页视觉核读；新增1个book、4个人物、4个事件、2个movement与1个topic轻量实体，共12个实体。
- 新增15条verified关系，主要记录“本书讨论哪些事件／人物／运动”及少量来源明确的关系；不把通俗叙事中的强因果或遇刺阴谋说法写入图谱。
- Markdown保留详细论证、书内页码／PDF页码、跨书互读和证据边界。

### 2026-09-24：《科学革命的结构》（第四版）整本
- 全文核读Thomas S. Kuhn《科学革命的结构》（第四版）253页PDF；正文、1969后记、Ian Hacking导读和译后记分层记录。
- 新增8个轻量实体：1本书、1位人物、6个核心概念。
- 新增10条verified关系，聚焦作者身份、范式／常规科学／反常危机革命／不可通约性／学科基质／科学进步及其内部关系；每条均包含书名、章节、书内／PDF页码、evidence_type、confidence与status。
- 不把艺术史中的任何风格变化直接结构化为“范式转换”；跨领域关系仅保留在Markdown的解释层，待有直接材料再入图谱。

### 2026-09-24：《六十年代》整本完成
- 用户补充264页完整扫描后，从书内p.142 / PDF p.151续读至书内p.254 / PDF p.263，并核对封底；全书现可标记为完整阅读。
- 原partial_scan书籍实体已替换为 `book_sixties_wang_fengzhen_2000`；原10条关系同步迁移到完整书籍ID，菲尔兹《法国的毛主义》来源范围更新为pp.113–162。
- 新增8个轻量实体：4位续读作者与4个核心概念；新增10条verified关系，覆盖弗里斯、艾普特、杜伯曼、吉尔伯特及摇滚记忆政治、跨代延续、60年代记忆历史化、文本之外的阅读等。
- 当前结构化层合计1244个实体、1485条关系，其中1364条verified，121条历史旧关系仍无status；relations.jsonl解析通过。
- 详细论证仍保留在Markdown；多作者选集各篇观点分开归属，不把全书压成统一政治立场。

### 2026-09-25：《开放社会科学》整本完成

- 新增4个轻量实体：1本1997年中文版集体报告、委员会主席Immanuel Wallerstein、欧洲中心主义与社会科学、社会科学客观性。
- 新增4条带明确章节／页码、evidence_type、confidence与`status: verified`的关系，分别连接报告与跨学科性、欧洲中心主义、学术客观性及委员会主席身份。
- 完整报告正文范围为书内pp.1–113 / PDF pp.9–116；扫描PDF pp.117–118为出版社书目广告，p.119为空白（OCR重复识别了广告）。原始PDF及OCR Word转换稿不入库。

### 《历史资本主义》（2026-09-25）

新增轻量书目实体与4个来源限定概念实体；5条关系带章节、页码、证据类型、confidence和status。覆盖积累、半无产阶级家庭、核心—边缘与地缘文化；其他论证仍以中文Markdown档案为主。英语段与中译本的扫描边界分别登记。
