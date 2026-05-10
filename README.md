# COPD-Medical-Knowledge-Graph
COPD Medical Knowledge Graph Construction Based on MIMIC-III Electronic Health Records, including full pipeline code for data cleaning, entity extraction, LLM-based knowledge extraction, and graph visualization.
# COPD 医学知识图谱构建项目

本项目基于公开临床数据集 MIMIC-III，从电子病历文本中自动抽取 COPD（慢性阻塞性肺疾病）相关的医学实体与知识关系，最终构建并可视化交互式医学知识图谱，为疾病关联分析与临床决策支持提供结构化知识基础。

---

## 📌 项目背景与目标
随着电子病历数据的快速增长，如何从海量非结构化临床文本中高效提取、整合并呈现医学知识，成为医疗AI领域的重要挑战。本项目旨在通过自然语言处理与知识图谱技术，构建 COPD 疾病的结构化知识网络，直观展示疾病、症状、治疗方案与危险因素之间的关联关系，为后续临床研究与智能辅助提供可解释的知识支撑。

---

## 🛠️ 技术栈
- **编程语言**：Python
- **数据处理**：Pandas, NumPy
- **语义向量化**：Sentence-Transformers (`all-MiniLM-L6-v2`)
- **医学实体识别**：spaCy / ScispaCy
- **知识三元组抽取**：大语言模型 API
- **图谱构建与可视化**：PyVis

---

## 📂 项目文件结构
```
COPD-Medical-Knowledge-Graph/
├── 1_data_clean.ipynb          # 步骤 1：数据清洗与文本预处理
├── 2_entity_extraction.ipynb   # 步骤 2：医学实体识别与筛选
├── 3_llm_extract.ipynb         # 步骤 3：基于大模型的知识三元组抽取
├── 4_build_graph.ipynb         # 步骤 4：知识图谱构建与可视化
├── images/                      # 结果截图（图谱可视化、统计图表）
│   └── ZSTP.png        # 知识图谱示例图
└── README.md                    # 项目说明文档
```

---

## 🚀 运行说明

### 1. 环境配置
安装项目所需依赖库：
```bash
pip install pandas numpy torch tqdm spacy scispacy networkx sentence-transformers pyvis openai
```

### 2. 数据准备
本项目不包含受保护的原始医疗数据，使用前请自行申请 MIMIC-III 数据集，并在本地项目根目录新建 `data/` 文件夹，放入 `NOTEEVENTS.csv.gz` 等相关数据文件。

### 3. 执行流程
可以按照顺序运行 Notebook 文件，完成全流程实验：

1. **1_data_clean.ipynb**：完成数据去重、文本脱敏、噪声过滤与格式标准化
2. **2_entity_extraction.ipynb**：识别并筛选 COPD 相关的病历
3. **3_llm_extract.ipynb**：抽取「疾病 - 症状 - 治疗」等医学知识三元组
4. **4_build_graph.ipynb**：构建知识图谱并生成交互式可视化页面

### 4. 可视化结果
运行完所有代码后，就可以获得与ZSTP.png相似的知识图谱了

---

## 📊 项目成果

### 核心成果
- ✅ 实现了从原始电子病历到结构化医学知识的全流程自动化处理
- ✅ 构建了覆盖 COPD 疾病核心关联的医学知识图谱，包含疾病、症状、治疗方案、危险因素等多类实体与关系
- ✅ 生成了可交互的可视化图谱，支持节点探索、关系查询与路径分析
- ✅ 统计并分析了高频医学实体分布与疾病关联模式，为后续研究提供了数据基础
---

## ⚠️ 注意事项
- **数据合规性**：本项目不包含任何 MIMIC-III 原始数据，使用前需完成官方申请并严格遵守数据使用协议，禁止数据泄露与商业用途。
- **路径配置**：代码中数据路径已设为相对路径 `./data/`，请确保本地数据存放位置与代码路径一致，否则会出现读取错误。
- **模型依赖**：Sentence-Transformers 模型（如 `all-MiniLM-L6-v2`）会在首次运行时自动下载，无需手动配置本地路径；若网络不佳，可提前下载模型并修改代码路径。
- **API 调用**：基于大语言模型的知识抽取步骤依赖 API，请提前配置好相关密钥，避免调用失败。
---

## 📄 声明
本项目仅用于学术研究与学习交流，禁止用于商业用途。
