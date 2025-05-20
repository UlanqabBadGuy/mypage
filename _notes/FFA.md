---
layout: note
title: "FFA"
date: 2025-05-09
categories: [介绍]
tags: [考试]
---
# FFA 中文版

* Table of Contents
{:toc}


## 第一章

### 01 财务欺诈分析 (Financial Fraud Analytics) 简介

#### 什么是“欺诈” (Fraud)?

- **英文词典定义**: 指通过欺骗他人获取金钱的犯罪行为。(PPT第6页)
- **法律词典定义**: 指有意使用欺骗、诡计或不诚实手段剥夺他人财产的行为。(PPT第6页)

### 02 数据分析 (Data Analytics)

#### 数据分析策略 (Strategies for Fraud Detection)

- PPT中提到了数据分析策略，但具体内容在当前提供的片段中没有详细展开。(PPT第2页、第4页)

### 03 探索性数据分析 (Exploratory Data Analysis, EDA)

#### EDA概述 (EDA Overview)

- 目的
  - 在正式建模或假设检验之前，发现数据中的模式 (patterns)、识别异常值 (outliers) 和检验假设 (test hypotheses)。 (PPT第69页)
  - 通过直观地总结数据的主要特征，通常使用可视化方法。 (PPT第69页)
  - 提供对数据的初步理解，发现有趣的趋势或异常情况。 (PPT第69页)
  - 为后续的建模任务提供指导。 (PPT第69页)
- 为什么重要
  - 帮助分析师理解手头的数据集。 (PPT第69页)
  - 识别数据中的异常值。 (PPT第69页)
  - 提供更好的特征工程 (feature engineering) 机会，以创建更有效的特征 (features)。 (PPT第69页)
  - 对模型选择 (model selection) 有帮助。 (PPT第69页)
  - 有助于节省时间，因为它可以更快地确定预测因素 (predictors)。 (PPT第69页)

#### EDA – 步骤1：缺失值分析 (Missing Value Analysis)

- 目的

  - 了解缺失数据的模式。 (PPT第70页)
  - 了解缺失值的百分比。 (PPT第70页)
  - 分析缺失数据是否随机 (random)。 (PPT第70页)
  - 对缺失值进行插补 (impute)。 (PPT第70页)

- 插补方法 (Imputation Methods)

  - 删除 (Deletion)

    - 删除具有缺失值的行或列。
    - **行删除 (Listwise Deletion)**: 如果某行包含任何缺失值，则删除整行。当数据集中缺失值较少时适用，否则会导致信息丢失。
    - **成对删除 (Pairwise Deletion)**: 仅在计算特定统计量时删除包含缺失值的观测值。比如计算相关系数时，只删除计算这两个变量时缺失的行。

  - 均值/众数/中位数插补 (Mean/Mode/Median Imputation)

    - 使用非缺失值的均值、众数或中位数填充缺失值。
    - **均值插补 (Mean Imputation)**: 适用于数值型变量，用该变量的均值填充。
    - **众数插补 (Mode Imputation)**: 适用于分类变量，用该变量的众数填充。
    - **中位数插补 (Median Imputation)**: 适用于数值型变量，对异常值更鲁棒。

  - 最近邻插补 (K-Nearest Neighbors, KNN Imputation)

    - 根据与缺失值最相似的K个邻居的特征来填充缺失值。
    - 通过距离函数（如欧几里得距离）找到“最近”的K个数据点。
    - 使用这K个邻居的平均值（数值型）或众数（分类型）来填充缺失值。

  - 回归插补 (Regression Imputation)

    :

    - 利用现有数据建立回归模型，预测缺失值。
    - 将有缺失值的变量作为因变量，其他变量作为自变量，训练回归模型来预测缺失值。

- **来源**: "Missing value analysis (Source: Wikipedia)" (PPT第70页)

#### EDA – 步骤2：单变量分析 (Univariate Analysis)

- 探索内容
  - 每个属性 (attribute) 的数据类型 (data type)。 (PPT第70页)
  - 每个属性中数据的分布 (distribution) 和分散度 (dispersion)。 (PPT第70页)
  - 异常值 (outliers)。 (PPT第70页)
- 技术 (Techniques)
  - 可视化工具 (Visualization tools)
    - 直方图 (histogram): 展示数值型数据的分布。
    - 箱线图 (boxplot): 展示数值型数据的分布、中位数、四分位数和异常值。
    - 计数图 (count-plot): 展示分类变量中每个类别的计数。
    - 密度图 (density plot): 展示数据的概率密度函数估计。
  - 描述性统计 (Descriptive statistics)
    - 均值 (mean)、中位数 (median)、众数 (mode)。
    - 标准差 (standard deviation)、方差 (variance)。
    - 偏度 (skewness)、峰度 (kurtosis)。 (PPT第70页)

#### EDA – 步骤3：双变量/多变量分析 (Bi-/Multi-variate Analysis)

- 目的
  - 理解属性之间的关系 (relations among the attributes)。 (PPT第71页)
  - 识别属性值之间的不兼容性 (incompatibilities among attribute values)。 (PPT第71页)
  - 生成最优的特征组合 (optimal feature combinations)。 (PPT第71页)
- 探索内容
  - **双变量分析 (Bivariate analysis)**: 仅分析两个属性之间的关联。 (PPT第71页)
  - **多变量分析 (Multivariate analysis)**: 分析两个以上属性之间的关联。 (PPT第71页)
- 技术 (Techniques)
  - 可视化工具 (Visualization tools)
    - 直方图 (histogram): 可用于比较两个变量的分布。
    - 箱线图 (boxplot): 可用于比较不同类别下数值变量的分布。
    - 散点图 (scatter-plot): 展示两个数值变量之间的关系。
    - 热力图 (heatmap): 展示多个变量之间的相关性矩阵。
  - **相关性分析 (Correlation analysis)**: 例如皮尔逊相关系数 (Pearson correlation)。 (PPT第71页)
  - **执行顺序**: 在进行多变量分析之前执行双变量分析。通过双变量分析，可以清楚地了解属性对的兼容性。然后，可以结合更多属性对进行进一步分析。 (PPT第71页)

#### 相关性分析 (Correlation Analysis)

- **定义**: 帮助理解不同变量之间关系的一种强大技术，即变量是正相关还是负相关。 (PPT第71页)
- **最常用方法**: 皮尔逊相关系数 (Pearson correlation)。 (PPT第71页)
- **计算方法**: 两个变量的协方差 (covariance) 除以它们标准差 (standard deviations) 的乘积。 (PPT第71页)
- 系数解读
  - 如果系数在 ±0.5 到 ±1.0 之间，则高度相关 (highly correlated)。 (PPT第71页)
  - 如果系数低于 ±0.29，则相关性低 (low correlation)。 (PPT第71页)
- **来源**: "Correlation Analysis (Source: Wikipedia)" (PPT第71页)
- **例子**: 在相关性热力图 (heatmap of correlation) 中，许多变量之间以及与类别变量 (Class variable) 之间没有显著相关性。 (PPT第72页)

## 第二章

#### EDA的定义与局限性 (PPT Page 4)
* **定义**: 探究性数据分析 (EDA) 是一个利用快速、简单的方法对小型数据集进行可视化和检查的过程。常见的传统EDA工具包括箱线图 (boxplots)、直方图 (histograms) 等。该概念由Tukey在1977年提出。
* **局限性**: 随着当前数据集规模的不断增长（涉及大数据的5个V特性，即Volume, Velocity, Variety, Veracity, Value），仅使用传统的EDA方法分析数据已不再可行。

#### EDA的目的 (PPT Page 5)

* 在构建欺诈检测模型之前，更好地理解数据。
* 检测数据中存在的问题。

#### 进行EDA时需要注意的事项 (PPT Page 5)
* 本次欺诈分析的目的是什么？
* 可以从欺诈中获得哪些洞察或深入知识？
* EDA的目标是否与当前面临的问题一致？

#### EDA的步骤 (Data Pre-processing) (PPT Page 6)
* **第一步：加载数据 (Load Data)**: 导入需要分析的数据集。

#### EDA的步骤 (数据准备) (PPT Page 7)
* **第二步：数据清理 (Data Cleaning)**:
    * **处理缺失值 (Missing Values)**: 检查数据中是否存在缺失值，并决定如何处理它们（例如，填充、删除）。
    * **处理异常值 (Outliers)**: 识别并处理数据中的异常值，这些值可能对分析结果产生较大影响。
    * **处理不一致的数据 (Inconsistent Data)**: 查找并纠正数据中的不一致性，例如不同格式的日期或拼写错误。
    * **处理重复的数据 (Duplicated Data)**: 识别并删除数据中的重复记录。

#### EDA的步骤 (数据转换) (PPT Page 8)
* **第三步：数据转换 (Data Transformation)**:
    * **特征选择 (Feature Selection)**: 从原始数据中选择最相关、最有预测能力的特征。
    * **特征工程 (Feature Engineering)**: 创建新的特征，通过组合或转换现有特征来提高模型性能。
    * **数据标准化/归一化 (Data Standardization/Normalization)**: 将数据缩放到特定范围或使其服从特定分布，以避免某些特征对模型产生过大影响。
    * **降维 (Dimensionality Reduction)**: 减少数据的维度，例如使用主成分分析 (Principal Component Analysis, PCA)，以简化模型并减少过拟合的风险。

#### EDA的步骤 (数据探索) (PPT Page 9)
* **第四步：数据探索 (Data Exploration)**:
    * **描述性统计 (Descriptive Statistics)**: 计算数据的基本统计量，如均值、中位数、标准差等，以了解数据的集中趋势和离散程度。
    * **可视化 (Visualization)**:
        * **单变量分析 (Univariate Analysis)**: 分析单个变量的分布，例如使用直方图、箱线图。
        * **多变量分析 (Multivariate Analysis)**: 分析多个变量之间的关系，例如使用散点图 (scatter plots)、热力图 (heatmaps)。

#### EDA的步骤 (总结和报告) (PPT Page 10)
* **第五步：总结和报告 (Summarization and Reporting)**:
    * **见解和发现 (Insights and Findings)**: 总结通过EDA获得的关键见解和发现。
    * **未来工作 (Future Work)**: 基于EDA的结果，提出进一步分析或模型构建的建议。

#### 示例：信用卡欺诈数据集 (PPT Page 11-12)
* **数据集来源**: Kaggle 平台上的信用卡欺诈检测数据集。
* **数据集特性**: 包含欧洲持卡人在2013年9月两天内发生的交易数据。
* **特点**:
    * **高度不平衡 (Highly Imbalanced)**: 欺诈交易（正类）在所有交易中占比非常小，仅占0.172%。
    * **匿名化特征 (Anonymized Features)**: 除了时间和金额特征外，所有特征都经过PCA转换，以保护用户隐私。这些特征的名称为V1到V28。
    * **时间和金额 (Time and Amount)**: 原始的交易时间和交易金额特征没有经过PCA转换。
* **目标**: 基于给定特征检测异常交易。

#### EDA案例分析：时间特征 (PPT Page 13)
* **观察**: 欺诈交易主要集中在特定时间段内，而正常交易在全天都有分布。
* **建议**: 在欺诈检测模型中考虑“时间”特征。

#### EDA案例分析：交易金额特征 (PPT Page 14)
* **观察**: 欺诈交易的金额通常低于正常交易的金额，且集中在较小金额范围。这可能是因为欺诈者倾向于进行小额交易以避免被发现。
* **建议**: 交易金额可以作为欺诈检测的有效特征。

#### EDA案例分析：PCA特征 (PPT Page 15)
* **观察**: 通过PCA转换的特征（V1到V28），不同特征对于区分欺诈和非欺诈交易的重要性不同。例如，V17、V14、V12和V10对于欺诈交易的值明显低于非欺诈交易。
* **建议**: 这些PCA特征对于欺诈检测模型至关重要。

### 财务报表欺诈方案 (Financial Statement Fraud Scheme)

#### 财务报表欺诈的概述 (PPT Page 18)
* **定义**: 财务报表欺诈通常是指在财务报表中的故意虚假陈述或遗漏，旨在欺骗用户。
* **动机**: 常见动机包括满足分析师预期、掩盖运营失败、粉饰管理层表现以及影响股票价格。
* **复杂性**: 识别财务报表欺诈非常复杂，因为欺诈者通常会采取措施隐藏其不当行为。
* **检测**: 审计师、监管机构和内部控制系统是检测财务报表欺诈的关键。
* **影响**: 财务报表欺诈可能对投资者、公司和市场信心产生重大负面影响。

#### 财务报表欺诈的类型 (PPT Page 19)
* **虚假收入 (Fictitious Revenues)**: 虚构收入，例如通过虚假销售或提前确认收入。
* **过早确认收入 (Premature Revenue Recognition)**: 在销售完成或服务提供之前确认收入。
* **隐藏负债或费用 (Concealed Liabilities and Expenses)**: 未报告债务、担保或其他负债，或隐瞒费用以虚增利润。
* **不当资产估值 (Improper Asset Valuation)**: 虚增资产价值（如存货、应收账款），或未充分计提折旧/摊销。
* **披露不当 (Improper Disclosures)**: 未能充分披露重要信息，如重大的关联方交易、或有负债等。

#### 收入操纵的例子 (PPT Page 20)
* **虚假销售 (Fictitious Sales)**: 记录不存在的销售。
* **“开箱”和“填充渠道” (Channel Stuffing)**: 在会计期末向分销商大量销售产品，即使知道这些产品无法立即销售，以提高当期收入。

#### 收入操纵的检测方法 (PPT Page 21)
* **分析销售退回和折让 (Sales Returns and Allowances)**: 如果销售退回和折让在报告期末突然大幅增加，可能表明存在“渠道填充”。
* **分析大额和不寻常的期末销售 (Large and Unusual Year-end Sales)**: 检查在会计期末突然出现的大额或异常销售交易。
* **评估客户信誉 (Customer Creditworthiness)**: 审查客户的信用状况，如果客户的信用评级很差却有大量销售，可能存在问题。
* **销售收入与应收账款的比率 (Sales Revenue to Accounts Receivable Ratio)**: 如果应收账款增长速度快于销售收入，可能表明收入被虚增。
* **销售收入与现金流入的比率 (Sales Revenue to Cash Inflow Ratio)**: 如果销售收入增长快于经营活动现金流入，可能存在虚假销售。

#### 隐藏负债或费用 (PPT Page 22)
* **类型**:
    * **未报告的负债 (Unreported Liabilities)**: 未能在财务报表中披露所有债务或义务。
    * **未记录的费用 (Unrecorded Expenses)**: 未能在损益表中记录所有费用。
    * **资本化费用 (Capitalized Expenses)**: 将应作为费用处理的项目不当地资本化为资产，从而虚增当期利润。

#### 隐藏负债或费用的检测方法 (PPT Page 23)
* **分析未记录的费用 (Unrecorded Expenses)**:
    * **分析供应商发票 (Supplier Invoices)**: 审查报告期末和期初的供应商发票，以识别是否存在未记录的费用。
    * **审查银行对账单 (Bank Reconciliation)**: 核对银行对账单和公司账簿，查找任何未记录的支出。
* **分析已资本化的费用 (Capitalized Expenses)**:
    * **费用与资产比率 (Expense to Asset Ratio)**: 检查费用与资产比率是否异常，如果费用被不当地资本化，该比率可能会下降。
    * **比较与行业平均水平 (Industry Averages)**: 将公司的费用资本化政策与行业平均水平进行比较，以识别异常情况。

#### 不当资产估值 (PPT Page 24)
* **类型**:
    * **夸大资产价值 (Overstating Asset Value)**: 例如，虚增存货 (inventory)、应收账款 (accounts receivable) 或固定资产 (fixed assets) 的价值。
    * **未能充分减记资产 (Failing to Impair Assets)**: 未能及时对价值已降低的资产进行减值处理。

#### 不当资产估值的检测方法 (PPT Page 25)
* **分析存货 (Inventory)**:
    * **存货周转率 (Inventory Turnover Ratio)**: 如果存货周转率异常低，可能表明存货被夸大。
    * **存货与销售额比率 (Inventory to Sales Ratio)**: 如果存货增长速度快于销售额，可能表明存货被夸大。
* **分析应收账款 (Accounts Receivable)**:
    * **应收账款周转率 (Accounts Receivable Turnover Ratio)**: 如果应收账款周转率异常低，可能表明应收账款被夸大或坏账准备不足。
    * **应收账款与销售额比率 (Accounts Receivable to Sales Ratio)**: 如果应收账款增长速度快于销售额，可能表明收入被虚增。

#### 披露不当 (PPT Page 26)
* **类型**:
    * **未能充分披露重要信息 (Failure to Disclose Material Information)**: 例如，重要的关联方交易、或有负债、重大法律诉讼等。
    * **模糊或误导性披露 (Vague or Misleading Disclosures)**: 在财务报表附注中提供不清晰或具有误导性的信息。
    * **遗漏重要信息 (Omission of Key Information)**: 故意省略对投资者决策至关重要的信息。

#### 披露不当的检测方法 (PPT Page 27)
* **阅读财务报表附注 (Read Financial Statement Footnotes)**: 仔细阅读所有附注，寻找任何异常或遗漏的信息。
* **分析关联方交易 (Related Party Transactions)**: 检查关联方交易的性质、条款和披露是否充分。
* **审查管理层讨论与分析 (Management Discussion and Analysis, MD&A)**: 将MD&A中的信息与财务报表中的信息进行核对，寻找不一致之处。
* **比较与行业最佳实践 (Industry Best Practices)**: 将公司的披露实践与行业内的最佳实践和监管要求进行比较。

#### 欺诈三角 (Fraud Triangle) (PPT Page 28)
* **构成要素**: 欺诈三角由三个要素构成：
    * **压力 (Pressure)**: 导致个人实施欺诈的激励或需求（例如财务困难、绩效压力）。
    * **机会 (Opportunity)**: 允许个人实施欺诈的环境或情况（例如内部控制薄弱、缺乏监督）。
    * **合理化 (Rationalization)**: 个人为自己的欺诈行为寻找理由或借口（例如认为自己只是“借用”）。
* **应用**: 欺诈三角被广泛用于理解和预防欺诈行为。

#### 欺诈信号 (Red Flags) (PPT Page 29)
* **定义**: “欺诈信号”或“危险信号”是指可能预示存在欺诈活动的警告性指标或不寻常情况。
* **例子**:
    * **不寻常的交易模式 (Unusual Transaction Patterns)**: 例如，在非工作时间进行大量交易。
    * **财务比率的突然变化 (Sudden Changes in Financial Ratios)**: 例如，应收账款周转率突然下降。
    * **关键人员的突然离职 (Sudden Departure of Key Personnel)**: 特别是那些负责财务或审计的员工。
    * **内部控制薄弱 (Weak Internal Controls)**: 例如，缺乏职责分离或监督。
* **重要性**: 识别欺诈信号有助于早期发现和预防欺诈。

#### Benford定律 (Benford's Law) (PPT Page 30)
* **定义**: Benford定律，也称第一位数字定律，指出在许多真实数据集（如财务数据、人口统计数据）中，首位数字的出现频率并非均匀分布，而是呈偏斜分布。数字1出现的概率最大（约30.1%），其次是2（约17.6%），以此类推，9出现的概率最小（约4.6%）。
* **应用**: 在欺诈检测中，如果数据集的首位数字分布与Benford定律显著偏离，可能表明数据被人为操纵。
* **限制**: Benford定律并非适用于所有数据集，例如那些没有自然增长或存在人为限制的数据。

#### 收入和利润率分析 (Revenue and Margin Analysis) (PPT Page 31)
* **概述**: 对公司的收入和利润率趋势进行分析，以识别潜在的欺诈行为。
* **常见欺诈模式**:
    * **虚增收入 (Inflated Revenues)**: 报告虚假销售或提前确认收入。
    * **利润率异常波动 (Unusual Fluctuations in Margins)**: 利润率突然大幅波动，没有合理解释。
    * **虚增利润 (Inflated Profits)**: 通过隐藏费用或不当估值资产来虚增利润。
* **检测方法**: 比较不同时期或与行业平均水平的收入和利润率，寻找异常趋势。

#### 应收账款和存货分析 (Accounts Receivable and Inventory Analysis) (PPT Page 32)
* **概述**: 分析应收账款和存货余额及周转率，以识别潜在的欺诈行为。
* **常见欺诈模式**:
    * **夸大应收账款 (Overstated Accounts Receivable)**: 虚增应收账款以夸大收入。
    * **夸大存货 (Overstated Inventory)**: 虚增存货以夸大资产。
* **检测方法**:
    * **应收账款周转率 (Accounts Receivable Turnover Ratio)**: 检测是否收账缓慢或虚增。
    * **存货周转率 (Inventory Turnover Ratio)**: 检测是否存货积压或虚增。
    * **销售退回和折让 (Sales Returns and Allowances)**: 如果销售退回和折让比例异常高，可能存在渠道填充。

#### 管理层讨论与分析 (MD&A) 分析 (PPT Page 33)
* **概述**: MD&A是财务报表中的重要部分，管理层在此讨论公司的经营状况、财务业绩和未来展望。分析MD&A可以发现与财务数据不一致的信息或潜在的欺诈信号。
* **检测方法**:
    * **关键词分析 (Keyword Analysis)**: 识别MD&A中是否存在过度乐观、回避责任或模糊的词语。
    * **情绪分析 (Sentiment Analysis)**: 评估MD&A的整体语气和情绪，以发现潜在的问题。
    * **与财务数据的交叉核对 (Cross-referencing with Financials)**: 将MD&A中的陈述与财务报表中的实际数据进行比较。

#### 董事会会议纪要分析 (Board Meeting Minutes Analysis) (PPT Page 34)
* **概述**: 董事会会议纪要记录了公司高层管理人员的决策和讨论。分析这些纪要可以揭示潜在的治理问题、内部冲突或可能导致欺诈的压力。
* **检测方法**:
    * **决策审查 (Review of Decisions)**: 审查关键决策，特别是那些与财务报告、重大交易或内部控制相关的决策。
    * **讨论内容 (Discussion Content)**: 寻找关于会计政策、内部控制缺陷或异常交易的讨论。
    * **利益冲突 (Conflicts of Interest)**: 识别可能存在的利益冲突。

#### 新闻稿和分析师报告分析 (Press Release and Analyst Report Analysis) (PPT Page 35)
* **概述**: 分析公司发布的新闻稿和分析师报告，可以评估公司对外沟通的一致性，并寻找可能与财务报表信息不符的信号。
* **检测方法**:
    * **一致性检查 (Consistency Check)**: 比较新闻稿、分析师报告和财务报表中的信息是否一致。
    * **情绪分析 (Sentiment Analysis)**: 评估新闻稿和分析师报告的整体情绪。
    * **盈利预测 (Earnings Forecasts)**: 关注分析师对公司盈利的预测以及公司对这些预测的回应。

#### 异常检测 (Anomaly Detection) (PPT Page 36)
* **定义**: 异常检测是指识别与大多数数据模式显著不同的数据点、事件或观测值。这些异常点通常被称为异常值 (outliers)。
* **应用**: 在财务欺诈检测中，异常检测可以识别出与正常交易模式不符的欺诈交易或账户行为。
* **常用算法**:
    * **基于统计的方法 (Statistical Methods)**: 例如Z-score、四分位距 (IQR)。
    * **基于聚类的方法 (Clustering-based Methods)**: 例如DBSCAN、K-Means。
    * **基于密度的方法 (Density-based Methods)**: 例如局部异常因子 (Local Outlier Factor, LOF)。
    * **机器学习方法 (Machine Learning Methods)**: 例如孤立森林 (Isolation Forest)、One-Class SVM。

#### 欺诈分析中的异常检测挑战 (PPT Page 37)
* **定义异常的困难 (Difficulty in Defining Anomaly)**: 欺诈模式不断演变，导致难以准确定义“异常”。
* **数据稀疏性 (Data Sparsity)**: 欺诈交易通常非常罕见，导致数据集中欺诈样本量过少。
* **高维度数据 (High Dimensionality Data)**: 财务数据通常具有大量特征，增加了异常检测的复杂性。
* **数据噪声 (Data Noise)**: 数据中的噪声可能被误识别为异常。
* **非静态行为 (Non-stationary Behavior)**: 正常和欺诈行为的模式可能随时间变化。
* **模型可解释性 (Model Interpretability)**: 许多先进的异常检测模型（尤其是基于深度学习的）难以解释其检测结果。

#### 异常检测的类型 (PPT Page 38)
* **点异常 (Point Anomalies)**: 单个数据点与其余数据显著不同。例如，一笔金额异常大的交易。
* **上下文异常 (Contextual Anomalies)**: 数据点在特定背景下是异常的，但在其他背景下可能是正常的。例如，在非工作时间进行的大笔交易。
* **集体异常 (Collective Anomalies)**: 一组数据点作为一个整体是异常的，但单个数据点可能不是。例如，一系列小额但频繁的交易，累积起来构成异常模式。

#### 异常检测方法的分类 (PPT Page 39)
* **监督学习 (Supervised Learning)**: 当有足够的标记（Labeled）欺诈和非欺诈样本时，可以使用分类算法（如SVM、决策树、神经网络）。
* **半监督学习 (Semi-supervised Learning)**: 当只有大量正常样本和少量或没有异常样本的标记时。通常通过学习正常数据的模式，将偏离该模式的数据视为异常。
* **无监督学习 (Unsupervised Learning)**: 当数据中没有标记样本时。算法通过识别数据中的模式或聚类，将不符合主要模式的数据点视为异常。

#### 基于监督学习的异常检测 (PPT Page 40)
* **应用场景**: 当数据集中有足够数量的标记为“正常”和“异常”的数据时。
* **方法**: 可以将异常检测视为一个分类问题。
* **算法**: 支持向量机 (Support Vector Machine, SVM)、逻辑回归 (Logistic Regression)、决策树 (Decision Trees)、随机森林 (Random Forest)、神经网络 (Neural Networks) 等。
* **挑战**:
    * **数据不平衡 (Imbalanced Data)**: 异常样本（欺诈）通常非常稀有，导致模型在预测少数类时性能不佳。
    * **新颖攻击 (Novel Attacks)**: 欺诈模式不断变化，模型可能无法识别从未见过的新型欺诈。

#### 基于无监督学习的异常检测 (PPT Page 41)
* **应用场景**: 当数据集中没有标记样本时，或者只有少数标记异常样本时。
* **方法**: 算法通过发现数据中不常见的模式或与其他数据点行为差异显著的数据点来识别异常。
* **算法**:
    * **K-Means 聚类 (K-Means Clustering)**: 将数据点聚类，远离聚类中心或属于小而稀疏聚类的数据点可能是异常。
    * **孤立森林 (Isolation Forest)**: 通过随机选择特征并随机划分数据点来隔离异常点。
    * **局部异常因子 (Local Outlier Factor, LOF)**: 基于数据点与其邻居密度的比较来评估异常程度。
* **优势**: 不需要标记数据，适用于发现新的或未知的异常模式。
* **挑战**: 难以解释为何某个点被认为是异常，对噪声敏感。

#### 基于半监督学习的异常检测 (PPT Page 42)
* **应用场景**: 当只有大量正常（未标记）数据和少量或没有异常数据可用时。
* **方法**: 通常通过学习正常数据的模式来构建模型，将偏离该正常模式的数据点视为异常。
* **算法**:
    * **One-Class SVM (One-Class Support Vector Machine)**: 训练模型来学习正常数据点的边界，将位于该边界之外的点视为异常。
    * **自编码器 (Autoencoders)**: 学习数据的压缩表示，然后尝试重建数据。重建误差大的数据点可能是异常。
* **优势**: 适用于只有少量异常样本的情况。
* **挑战**: 模型的性能依赖于正常数据的准确表示。

#### 异常检测方法的选择 (PPT Page 43)
* **数据可用性 (Data Availability)**:
    * 如果已标记欺诈和非欺诈数据且数量充足，可使用监督学习。
    * 如果只有正常数据且无欺诈数据，可使用无监督学习。
    * 如果只有少量欺诈数据，可使用半监督学习。
* **可解释性 (Interpretability)**: 有些方法比其他方法更容易解释其检测结果。
* **计算复杂性 (Computational Complexity)**: 大规模数据集可能需要更高效的算法。

### 不平衡数据处理 (Imbalance Data Handling)

#### 什么是类不平衡 (What is Class Imbalance)? (PPT Page 45)
* **定义**: 在分类问题中，当不同类别的样本数量分布不均匀时，就存在类不平衡问题。其中一个或多个类别的样本数量远远少于其他类别。
* **常见场景**:
    * **欺诈检测 (Fraud Detection)**: 欺诈交易远少于正常交易。
    * **疾病诊断 (Disease Diagnosis)**: 患病样本远少于健康样本。
    * **垃圾邮件检测 (Spam Detection)**: 垃圾邮件远少于正常邮件。
* **挑战**: 传统的分类算法通常会倾向于多数类 (Majority Class)，导致对少数类 (Minority Class) 的识别性能较差。

#### 类不平衡数据的影响 (Impact of Class Imbalance Data) (PPT Page 46)
* **模型偏向 (Model Bias)**: 分类模型倾向于预测多数类，即使少数类是关注的重点（如欺诈）。
* **评估指标误导 (Misleading Evaluation Metrics)**: 准确率 (Accuracy) 等指标可能很高，但实际上模型在少数类上的表现很差。
* **少数类召回率低 (Low Minority Class Recall)**: 模型很难正确识别少数类样本，导致重要的欺诈或疾病案例被漏报。
* **泛化能力差 (Poor Generalization)**: 模型对少数类数据的学习不足，在新的、未见过的数据上表现不佳。

#### 解决类不平衡数据的方法 (Methods to Handle Class Imbalance Data) (PPT Page 47)
* **数据层面方法 (Data-level Methods)**:
    * **欠采样 (Undersampling)**: 减少多数类样本的数量。
    * **过采样 (Oversampling)**: 增加少数类样本的数量。
    * **混合采样 (Hybrid Sampling)**: 结合欠采样和过采样。
* **算法层面方法 (Algorithm-level Methods)**:
    * **代价敏感学习 (Cost-Sensitive Learning)**: 为不同类别的误分类赋予不同的代价。
    * **集成学习 (Ensemble Learning)**: 结合多个模型来提高性能，例如Bagging和Boosting。
* **评估指标选择 (Evaluation Metric Selection)**: 选择更适合不平衡数据的评估指标，如精确率 (Precision)、召回率 (Recall)、F1分数 (F1-score)、AUC-ROC曲线 (Area Under the Receiver Operating Characteristic Curve)。

#### 欠采样方法 (Undersampling Methods) (PPT Page 48)
* **随机欠采样 (Random Undersampling)**:
    * **方法**: 随机删除多数类样本，直到多数类和少数类的样本数量达到平衡或接近平衡。
    * **优点**: 简单易行，可以减少训练时间和内存需求。
    * **缺点**: 可能丢失多数类中的重要信息，导致模型性能下降。
* **多数类欠采样 (Undersampling Majority Class)**:
    * **方法**: 与随机欠采样类似，但目标是减少多数类样本的数量。
    * **优点**: 可以平衡数据集。
    * **缺点**: 同样存在信息丢失的风险。
* **基于聚类的欠采样 (Clustering Based Undersampling)**:
    * **方法**: 对多数类进行聚类，然后从每个聚类中选择代表性样本进行欠采样。
    * **优点**: 可以保留多数类中的重要信息。
    * **缺点**: 增加了复杂性。
* **Tomek Links**:
    * **方法**: 识别Tomek Links（即一对属于不同类别的最近邻样本，且它们彼此之间是最近邻），然后删除多数类中的样本。
    * **优点**: 可以清理类边界，使分类器更容易区分两类。
    * **缺点**: 只能删除那些与少数类样本紧密相邻的多数类样本。

#### 过采样方法 (Oversampling Methods) (PPT Page 49)
* **随机过采样 (Random Oversampling)**:
    * **方法**: 简单地复制少数类样本，直到达到所需的比例。
    * **优点**: 简单易行。
    * **缺点**: 可能导致模型过拟合 (Overfitting)，因为重复的样本没有增加新的信息。
* **SMOTE (Synthetic Minority Over-sampling Technique)**:
    * **方法**: 通过在少数类样本及其K近邻之间创建合成样本来增加少数类样本。它不是简单复制，而是通过插值生成新样本。
    * **优点**: 减少了过拟合的风险，并生成了更多样化的少数类样本。
    * **缺点**: 可能在少数类边界附近生成噪声样本，如果少数类样本本身存在噪声，SMOTE可能会加剧问题。
* **Borderline-SMOTE**:
    * **方法**: 仅对位于决策边界附近的少数类样本进行过采样，而不是所有少数类样本。这有助于解决少数类样本内部噪音的问题。
    * **优点**: 专注于改善决策边界附近的学习。
    * **缺点**: 仍然可能受到噪音影响。
* **ADASYN (Adaptive Synthetic Sampling)**:
    * **方法**: 专注于生成更难以学习的少数类样本，即那些周围有更多多数类样本的少数类样本。
    * **优点**: 根据学习难度自适应地生成样本。
    * **缺点**: 实现相对复杂。

#### SMOTE的详细说明 (PPT Page 50-51)
* **基本原理**:
    * 对于每个少数类样本 (x)，找到其K个最近邻 (k-nearest neighbors)。
    * 随机选择其中一个邻居 (xn)。
    * 在样本 (x) 和选定的邻居 (xn) 之间生成一个合成样本。合成样本的特征是 (x) 和 (xn) 之间特征的线性组合。
* **计算公式**: $x_{new} = x + rand(0, 1) \times (x_n - x)$，其中 $x_{new}$ 是新生成的合成样本，$x$ 是原始少数类样本，$x_n$ 是其一个随机选定的K近邻，$\text{rand}(0, 1)$ 是一个0到1之间的随机数。

#### SMOTE的应用示例 (PPT Page 52)
* **步骤**:
    1.  从少数类样本中随机选择一个点 $X_i$。
    2.  找到 $X_i$ 的K个最近邻。
    3.  从K个最近邻中随机选择一个 $X_j$。
    4.  沿着从 $X_i$ 到 $X_j$ 的线段，随机生成一个新样本 $X_{new}$。
* **优点**: 增加了少数类样本的数量，减少了类不平衡对模型训练的影响。

#### 结合采样方法 (Hybrid Sampling Methods) (PPT Page 53)
* **SMOTE + Tomek Links**:
    * **方法**: 先使用SMOTE生成合成少数类样本，然后使用Tomek Links删除多数类中的噪声样本，进一步清理决策边界。
    * **优点**: 结合了过采样和欠采样的优势，既增加了少数类样本，又清理了模糊的边界。
* **SMOTE + ENN (Edited Nearest Neighbours)**:
    * **方法**: 先使用SMOTE生成合成少数类样本，然后使用ENN来删除那些被其K近邻误分类的样本（通常是噪声或位于边界处的多数类样本）。
    * **优点**: 类似SMOTE + Tomek Links，可以更有效地处理不平衡数据和噪声。

#### 算法层面方法 (Algorithm-Level Methods) (PPT Page 54)
* **代价敏感学习 (Cost-Sensitive Learning)**:
    * **方法**: 在训练分类器时，为不同类别的错误分类赋予不同的代价。例如，将少数类（如欺诈）的误分类（假阴性，False Negative）惩罚得更重。
    * **优点**: 模型会更关注正确识别少数类。
    * **缺点**: 需要预先定义误分类的代价，这通常很困难。
* **集成学习 (Ensemble Learning)**:
    * **方法**: 结合多个弱分类器来构建一个更强大的分类器。对于不平衡数据，可以通过集成多个在欠采样或过采样数据集上训练的基分类器。
    * **例子**:
        * **Bagging (Bootstrap Aggregating)**: 例如随机森林 (Random Forest)，可以对原始数据集进行多次欠采样，然后在每个子集上训练一个基分类器。
        * **Boosting**: 例如AdaBoost、XGBoost，它们可以为误分类的少数类样本赋予更高的权重，使其在后续迭代中得到更多关注。
    * **优点**: 通常能提高模型的鲁棒性和性能。

#### 评估指标 (Evaluation Metrics) (PPT Page 55)
* **混淆矩阵 (Confusion Matrix)**:
    * **真阳性 (True Positives, TP)**: 实际为正类且被正确预测为正类。
    * **真阴性 (True Negatives, TN)**: 实际为负类且被正确预测为负类。
    * **假阳性 (False Positives, FP)**: 实际为负类但被错误预测为正类（Type I Error）。
    * **假阴性 (False Negatives, FN)**: 实际为正类但被错误预测为负类（Type II Error）。
* **准确率 (Accuracy)**: $(TP + TN) / (TP + TN + FP + FN)$。当数据不平衡时，准确率会产生误导。
* **精确率 (Precision)**: $TP / (TP + FP)$。被预测为正类中，有多少是真正的正类。
* **召回率 (Recall / Sensitivity)**: $TP / (TP + FN)$。实际为正类中，有多少被正确识别出来。在欺诈检测中，召回率非常重要，因为我们不希望漏掉欺诈。
* **F1 分数 (F1-score)**: 精确率和召回率的调和平均值，$2 \times (Precision \times Recall) / (Precision + Recall)$。综合考虑了精确率和召回率。
* **G-mean (Geometric Mean)**: $\sqrt{Sensitivity \times Specificity}$，其中 $Specificity = TN / (TN + FP)$。它平衡了多数类和少数类的分类性能。
* **AUC-ROC 曲线 (Area Under the Receiver Operating Characteristic Curve)**:
    * ROC曲线描绘了在不同分类阈值下，真阳性率 (True Positive Rate, TPR) 与假阳性率 (False Positive Rate, FPR) 之间的关系。
    * AUC值表示模型区分正负类的能力。AUC值越高，模型性能越好。
    * 在不平衡数据集中，AUC是一个更可靠的评估指标，因为它不依赖于特定的分类阈值，且对类不平衡不敏感。

#### 如何选择最佳方法 (PPT Page 56)
* **没有一刀切的方法 (No One-Size-Fits-All Approach)**: 没有一种方法可以适用于所有不平衡数据集。
* **实验与评估 (Experimentation and Evaluation)**: 需要在具体数据集上尝试不同的方法，并使用合适的评估指标（如F1分数、AUC）来比较它们的性能。
* **领域知识 (Domain Knowledge)**: 结合领域专家知识可以帮助选择更合适的方法。例如，在欺诈检测中，召回率可能比精确率更重要，因为漏报欺诈的代价通常很高。

#### 不平衡数据的例子 (PPT Page 57)
* 以信用卡欺诈数据集为例，正常交易（0）和欺诈交易（1）的比例严重不平衡。

#### 信用卡欺诈检测：不同方法的性能比较 (PPT Page 58)
* 在信用卡欺诈数据集上，使用原始数据集、欠采样、随机过采样和SMOTE后，不同分类器（决策树、Logistic回归）的性能比较。
* **观察**:
    * 在原始数据集上，决策树和Logistic回归的F1分数都非常低，表明对少数类识别效果不佳。
    * 欠采样可能导致信息丢失，F1分数可能没有显著提高。
    * 过采样和SMOTE通常能显著提高F1分数，因为它们增加了少数类样本，使模型能够更好地学习少数类的特征。
* **结论**: 处理类不平衡数据对于提高欺诈检测模型的性能至关重要。

#### SMOTE的进一步解释 (PPT Page 96)
* **原理**: SMOTE通过测量所有少数类实例的K个最近邻，然后计算少数类和多数类实例的类别比率来创建新样本。
* **示例**:
    * 计算所有少数类数据点的“不纯度比率 (Impurity ratio)”。
    * 比率越高，生成的合成数据点越多。
    * 例如，观察值3的不纯度比率为0.8，观察值2为0.2，那么观察值3生成的合成数据点将是观察值2的4倍。
* **不纯度比率计算 (Impurity Ratio Calculation)**: 欺诈类邻居数量 / 非欺诈类邻居数量。
    * 观察1: 欺诈类邻居3个，非欺诈类邻居2个，不纯度比率 = 3/2 = 0.4 (此处示例计算与表中数据有出入，以表中数据为准，表中的0.4可能是3/(3+2)或根据其他加权方式计算)。

**重要提示**: PPT Page 96中的“Impurity Ratio”计算方式与传统SMOTE的最近邻选择和合成样本生成逻辑略有不同，它更像是根据邻域内的多数/少数类比例来决定生成多少新样本，以解决“不纯”的邻域问题。传统的SMOTE是根据K个最近邻中随机选择一个来进行插值，而这里可能暗示了一种基于邻域不纯度（即多数类样本占比）来决定过采样程度的变体。

## 第三章

### 什么是法务会计 (Forensic Accounting)（来源：Slide 6–8）

- **定义**：法务会计是一门研究和应用财务事实与法律问题之间关系的学科，用于在法庭审理中提供证据支持（Slide 6）。
- **功能**：协助调查贿赂、欺诈、洗钱等白领犯罪，并以专家证人的身份出庭作证（Slide 7–8）。
- **角色**：财务与欺诈调查员（Financial and Fraud Investigator）、问题识别者、信息收集者、文档分析师、人员行为分析师以及专家证人（Slide 8）。

### 法务会计师的主要工作内容 (What do Forensic Accountants Do)（来源：Slide 9–10）

1. 欺诈预防与检测 (Fraud Prevention and Detection)
2. 法务与欺诈调查 (Forensic and Fraud Investigation)
3. 合规与内部控制评审 (Regulatory Compliance and Internal Control Review)
4. 资产追踪与回收 (Asset Tracing and Recovery)
5. 反洗钱调查与审查 (Anti-Money Laundering Investigation and Review)
6. 诉讼支持 (Litigation Support)

- 在婚姻纠纷 (Matrimonial Dispute)、股东纠纷 (Shareholder Dispute) 和上市公司调查 (Listed Company Investigation) 中担任专家证人（Slide 10）。

### 审计与法务会计的区别 (Audit vs Forensic Accounting)（来源：Slide 11）

| 特性       | 审计 (Audit)                             | 法务会计 (Forensic Accounting)                             |
| ---------- | ---------------------------------------- | ---------------------------------------------------------- |
| 目标       | 确保财务报表公允呈现 (Fair presentation) | 识别欺诈或不当行为 (Fraud identification)                  |
| 方法与范围 | 有限的测试 (Limited testing)             | 详细审查与高度怀疑 (Detailed review & heightened scrutiny) |
| 标准       | 国际财务报告准则 (IFRS)                  | 法律与监管标准 (Legal and regulatory)                      |
| 培训       | 审计培训 (Audit training)                | 法务会计培训 (Forensic accounting training)                |



### 欺诈的定义与要素 (Fraud)（来源：Slide 12–13）

- **定义**： “欺诈指管理层、治理人员、员工或第三方中的一个或多个人，通过使用欺骗手段获得不正当或非法利益的故意行为。”（香港会计师公会审计准则240，Slide 13）
- **欺诈三要素**：机会 (Opportunity)、动机 (Motive)、合理化 (Rationalization)（Slide 13）。

### 人性的三态 (People’s Dishonesty Spectrum)（来源：Slide 14）

- 20% 天生不诚实 (Inherently dishonest)
- 20% 天生诚实 (Inherently honest)
- 60% 在不当环境下可能不诚实 (Could be dishonest in the wrong situation)

### 全球腐败认知指数 (Corruption Perceptions Index)（来源：Slide 16）

- 由透明国际 (Transparency International) 发布，衡量公共部门腐败程度的认知。
- 香港排名17，中国排名76，美国排名28（Slide 16）。

### 欺诈预防的环境与控制 (Fraud Prevention)（来源：Slide 25–28）

- **系统控制措施**（Slide 26）：
  - 完备的文件和记录 (Adequate documents and records)
  - 职责分离 (Segregation of duties)
  - 授权程序 (Proper authorization procedures)
  - 强制休假 (Mandatory vacation)
  - 新员工背景调查 (New employee vetting)
  - 匿名投诉渠道 (Anonymous complaint hotline)
  - 监督与控制 (Supervision and control)
  - 内部审计 (Internal audit)
- **企业文化与政策**（Slide 27–28）：
  - 行为守则 (Code of conduct)
  - 反欺诈政策 (Anti-fraud policy)
  - 管理层以身作则 (Management example)
  - 对欺诈事件的统一处理 (Consistent incident handling)

### 欺诈红旗 (Red Flags of Fraud)（来源：Slide 30–32）

- **内部控制薄弱信号**（Slide 31）：
  - 控制不严 (Loose internal controls)
  - 弱密码与文件访问控制 (Poor file access/password controls)
  - 不切实际的业绩目标 (Unrealistic targets)
  - 管理层越权 (Management override)
  - 重大客户或供应商异常变动 (Significant changes)
  - 关联交易问题 (Related-party transactions)
- **其他红旗**（Slide 32）：
  - 年底复杂交易 (Complex year-end transactions)
  - 离岸账户无业务理由 (Unjustified offshore accounts)
  - 缺乏文件或批准 (Lack of documentation/approval)
  - 异常快速增长或盈利 (Rapid growth/profitability)
  - 现金流不足 (Cash-flow problems)
  - 财务状况恶化 (Poor financial position)

### 欺诈实施者与特征 (Who Commits Fraud)（来源：Slide 33–37）

- **主体**（Slide 33）：高管、员工、竞争对手、客户与供应商、董事与管理者。
- **行为类型**（Slide 34）：Rum、Racecars、Romancers（三大“R”类型）。
- **常见特征**（Slide 35–37）：贪婪 (Greed)、自尊压力 (Ego/peer pressure)、赌博或毒品问题、超出财力的生活方式、不满情绪、把欺骗当智力挑战、异常单独接触或处理请求、与供应商走得太近等。

### 欺诈风险管理 (Fraud Risk Management)（来源：Slide 38–40）

- **团队构成**：内部团队 (Internal team) 与外部团队 (External team) 的职责与独立性（Slide 38–39）。
- **关键考虑**（Slide 40）：证据收集与保存 (Evidence preservation)、证人管理 (Witness management)、损失评估 (Damage assessment)、冻结令 (Freezing orders)、通知保险及监管机构、与警方合作 (Working with police)。

### 欺诈调查流程 (Fraud Investigation)（来源：Slide 41–46）

1. 访谈管理层及相关人员 (Interview management and staff)
2. 调查可疑交易 (Investigate suspicious transactions)
3. 审核会计记录与合同 (Review records and contracts)
4. 量化损失 (Quantify loss)
5. 收集庭审证据 (Collect evidence for trial)

- **技术与方法**（Slide 44–45）：文档审核、证词、观察、数据分析、计算机取证、物理证据等。
- **执法调查**（Slide 46）：申请与执行法院搜查令，发展证据供起诉使用。

### 新冠疫情下的反欺诈挑战 (COVID-19 Challenges)（来源：Slide 47–50）

- 欺诈案件增多 (Increase in fraud during COVID-19)（Slide 48）。
- **主要类型**：网络欺诈 (Cyberfraud，如商业邮件欺诈、黑客、勒索软件)、支付欺诈 (Payment fraud，如信用卡和移动支付欺诈)（Slide 49–50）。

### 专家证人 (Expert Witness)（来源：Slide 50–54）

- **定义与资格**（Slide 51–52）：具备相关知识、技能、培训或经验，须保持客观性、独立性和诚信。
- **高院规则**（Order 38 Appendix D，Slide 53）：报告需说明资格、事实与假设、意见理由、引用文献及测试细节。
- **不当角色**（Slide 54）：不可成为偏见的“枪手”或事后诸葛亮。

### 专家可提供的服务与流程 (Services & Process)（来源：Slide 55–56）

1. 文档审查 (Document review)
2. 关键问题预定位 (Early issue highlighting)
3. 取证问题与出庭 (Discovery questions & trial attendance)
4. 家产净值评估 (Family net property assessment)
5. 收入/利润损失测算 (Income/loss determination)
6. 现金流/折现预测 (Cash-flow forecasts/DCF)
7. 股权估值 (Share valuations)
8. 调解支持 (Settlement assistance)
9. 专家会议 (Experts’ meetings)
10. 出庭作证 (Trial appearance)

- **流程要点**：及早评估需求并聘请专家，理解其方法与报告，并充分准备（Slide 56）。

### 必须坚持的事项 (Insist Your Expert)（来源：Slide 57）

- 亲自审核文件 (Touch the paper)
- 了解行业与市场 (Know the industry/market)
- 测试关键假设 (Test the assumptions)
- 避免重复计数 (Don’t double count)
- 理解所有报告 (Make sure you understand the reports)

### 示证证据 (Demonstrative Evidence)（来源：Slide 58）

- “一图胜千言”——示证证据是法庭上展示复杂事实的高效工具。

### 真实案例分享 (Real-Life Cases)（来源：Slide 60–70）

1. 上海子公司虚增收益及行贿案（Slide 60–62）：吹哨人举报、审计收入与费用、访谈、发现虚假交易及贿赂，最终巨额罚款。
2. 金属回收公司圈钱案（Slide 63–66）：关联交易循环资金流夸大利润，法院认定“规模巨大”。
3. 2亿港元票据贷款追踪（Slide 67）：循环开票骗贷，资金流追踪，专家作证。
4. 离婚股东资金挪用（Project Seafood，Slide 68–69）：账目追踪与调整，出庭作证。
5. 德企并购合规尽调（Slide 70）：反贿赂与合规审查，访谈与测试。

## 第四章

### 一、概述与基本概念 (Slides 7–9)

**1. 洗钱的定义（Slide 7）**
 “洗钱”是指将非法获得的资金通过各种方法掩盖其来源，使其看似合法所得，包括三个阶段：投放（Placement）、分层（Layering）、整合（Integration） 。

**2. 洗钱三个阶段（Slide 8）**

- **投放（Placement）**：向金融体系注入犯罪所得现金。
- **分层（Layering）**：通过多层复杂交易切断资金与原始犯罪的关联。
- **整合（Integration）**：将“清洗”后的资金以合法形式投入经济活动。 

**3. 恐怖融资定义（Slide 9）**
 恐怖融资是以任何形式支持或资助恐怖活动，不论其资金来源是否合法，都须纳入监管范围。 

------

### 二、国际标准：FATF及其建议 (Slides 10–15)

**1. FATF简介（Slide 10）**
 金融行动特别工作组（FATF）成立于1989年，旨在制定并推动实施国际反洗钱和反恐融资标准 。

**2. 核心建议（Slides 11–12）**

- **Recommendation 10**：客户尽职调查（CDD）
- **Recommendation 11**：记录保存
- **Recommendation 12**：政治公众人物（PEP）
- **Recommendation 19**：高风险国家
- **Recommendation 20**：可疑交易报告
- **Recommendation 21**：妨碍调查禁止（Tipping-off） 

**3. DNFBPs扩展（Slide 13）**
 Recommendation 22、23将CDD与记录保存要求同样适用于指定非金融业务与职业（如赌场、中介、律师、会计师等） 。

**4. “灰名单”与“观察名单”（Slide 14–15）**

- **Call for Action**：朝鲜、伊朗、缅甸需采取最严对抗措施。
- **Increased Monitoring**：如保加利亚、肯尼亚、越南等需在时限内整改，否则升级制裁 。

------

### 三、香港本地法令与监管指引 (Slides 21–26)

**1. 主要法例（Slides 21–22）**

- **DTROP (Cap. 405)**：未及时披露毒贩收益属刑事罪，最高可判14年监禁及HK$5 M罚款。
- **OSCO (Cap. 455)**：涵盖多种严重罪行所得，未披露或处理相关财产亦构罪。
- **UNATMO (Cap. 575)**：资助恐怖活动即属犯罪，可冻结没收资金。
- **AMLO (Cap. 615)**：对金融机构及DNFBPs强制实施CDD、记录保存和报告义务。 

**2. 监管机构与指引（Slide 22）**

- 证监会（SFC）、金管局（HKMA）、保险业监管局（IA）、海关、公司注册处等。
- **SFC AML/CTF 指引**：虽非强制，但在诉讼中具备法律证据地位，覆盖RBA、CDD、持续监测、STR、记录保存、培训等。 

**3. AMLO详细规定（Slides 23–26）**

- **适用主体**：包括持牌公司、认可机构、保险商、汇兑商、放贷人及DNFBPs。
- **指定交易**：房地产业务、客户资产管理、账户管理、公司成立与管理、信托服务等。
- **处罚**：违反CDD/记录条文，FI最高可被罚HK$1 M并判处2年监禁；员工另设刑事及民事责任。 

------

### 四、关键要求与最佳实务 (Slides 6, 30–34, 49)

**1. 风险为本方法（RBA）（Slide 6 & 30–31）**
 要素包含国家风险、客户风险、产品/服务风险及渠道风险。根据不同风险调整DD深度、监测频率与控制措施 。

**2. 客户尽职调查（CDD）（Slides 32–34）**
 必须在开户、单笔≥HK$120 K、汇款≥HK$8 K、出现可疑情形或信息失真时执行，内容包括：

- 验证客户及实益拥有人身份
- 获取业务关系目的与预期性质
- 验证代理人身份与授权
- 法人需收集注册证书、章程、董事名录和股权结构等 。

**3. 持续监测（Ongoing Monitoring）（Slide 49）**

- 对所有业务关系（尤其高风险客户）定期（至少年审）更新资料。
- 审查交易是否与客户背景、风险和资金来源相符，深入调查复杂或异常交易 。

**4. 记录保存（Record Keeping）（Slide 6）**

- 客户识别记录及支持文件保存5年。
- 交易记录及其支持文件同样保存5年 。

**5. 可疑交易报告（STR）（Slide 6）**

- **内部报告**：员工向MLRO提交，保留流程与结论记录。
- **外部报告**：MLRO向JFIU提交，获法律免责；禁止“打招呼” 。

**6. 员工培训（Staff Training）（Slide 49）**

- 根据岗位定制化，每年至少复训一次；
- 培训记录保存不少于3年 。

------

### 五、互评报告与最新动态 (Slides 51–52, 58)

**1. 2019年互评报告（Slides 51–52）**

- 优先行动：深化外来犯罪风险认知、加强执法、完善DPMS监管、填补PEP与TF评估漏洞、资产跨境追踪等。
- 技术合规缺陷：未充分覆盖中国内地PEP的EDD需求。 

**2. AMLO 2022修订（Slide 58）**

- VASP牌照与DPMS注册制度；
- 扩展PEP定义（包括前任PEP）；
- 允许认可电子身份证明用于非面对面CDD。 

**3. 虚拟资产监管（Slides 62–65）**

- VA风险：匿名性、跨境便捷、非面对面关系、监管不一等。
- 自2023 年6 月起，VA平台须向SFC申请牌照并符合CDD、记录保存、客户资产安全等要求。 

------

### 六、执法案例 (Slides 72–75)

- **XIFHK (9 Oct 2024)**：无任何CSS尽调、监测自成交交易失败，被罚HK$9 M，高管停职9 月。 
- **CSC 期货 (Oct 2024)**：类似违规，被罚HK$4.95 M。
- **金瑞期货 (Feb 2023)**：未识别PEP、监管不足，被罚HK$4.8 M，高管停职。
- **Rifa 期货 (Jul 2022)**：未实施2FA、监测不足，被罚HK$9 M。
- **BMI & Sino-Rich (2020–2021)**：CDD失效、可疑交易未报、TPDs监测失败，多名高管被罚及停职 。

## 第五章

### HKMA纪律行动（Slide 5–20）

- **中国中信银行国际有限公司被处罚**：2024 年12 月6 日，中信因交易监控系统规则实施不当，未能在2015 年11 月至201...7 月期间对可疑交易生成警报，且未审查部分客户交易背景与目的，被罚款4 百万港元（Slide 5–6）。
- **富邦银行（香港）有限公司被处罚**：2024 年11 月8 日，富邦自报交易监控系统失效，2019 年4 月至2022 年7 月期间未持续监测客户关系、未及时更新客户尽职调查，又未跟进交易警报大幅减少，被罚款4 百万港元（Slide 6–7）。
- **微信支付香港有限公司被处罚**：2024 年8 月30 日，因未对触发事件进行客户尽职调查及风险缓释措施不足，被罚款875 千港元（Slide 7–8）。
- **星展银行（香港）有限公司被处罚**：2024 年7 月5 日，因未持续监测高风险客户及保留部分客户记录等系统控制缺陷，被罚款10 百万港元（Slide 8–9）。
- **TNG（亚洲）有限公司被处罚**：2023 年12 月18 日，因治理及风险管理框架不健全，内部控制系统缺陷，被罚款1 ,575 千港元（Slide 9–10）。
- **EFG银行香港分行被处罚**：2023 年8 月15 日，因未对跨行转客户进行尽职调查及持续尽调不到位，被罚款16 百万港元（Slide 10–11）。
- **西太平洋银行香港分行被处罚**：2023 年1 月31 日，周期审查延迟及程序缺陷，被罚款4 百万港元（Slide 11–12）。
- **国泰世华银行香港分行被处罚**：2022 年8 月26 日，因未对高风险情形进行加强尽调及持续尽调缺失，被罚款11 百万港元（Slide 12–13）。
- **德国商业银行香港分行被处罚**：2022 年8 月26 日，未按规定对部分客户执行尽职调查、未终止长期不合规关系、PEP识别及程序不完善，被罚款6 百万港元（Slide 13）。

### 香港AML/CFT最新重点（Slide 26–28）

- **数据驱动监管**：2023 年上半年银行接获637宗欺诈投诉，超2022全年555宗，HKMA推动大数据与技术应用于风险画像与监测（Slide 26–27）。
- **信息共享平台FINEST**：与业界及警方合作推出银行间共享情报平台，以打击欺诈及“骡子账户”网络（Slide 27）。
- **宏观分析试点**：对8家银行的金融犯罪数据进行跨机构分析，以定位薄弱环节与潜在威胁（Slide 28）。

### 证券及期货事务监察委员会(Regtech采纳情况)（Slide 33–36）

- **客户识别与开户**：使用“智方便”数字身份体系，通过API与开户系统集成，提高CDD效率（Slide 33）。
- **姓名筛查**：机器人流程自动化（RPA）提取并比对客户信息，减少手动审查量，自然语言处理用于不良媒体监测（Slide 33–34）。
- **交易监测**：定制化场景生成警报，AI评分引擎根据历史评估学习优先级，优化资源分配（Slide 34）。
- **第三方存款尽调**：API每0.5 小时自动拉取存款来源信息，仅匹配通过名称比对方可放行（Slide 35）。
- **合规治理**：制定有效监管框架与AI模型审查机制，确保数据保护与网络安全，SFC对生成式AI的采用提出指导（Slide 36）。

### 贸易洗钱（TBML）概念与发展（Slide 41–44）

- **定义**：利用贸易交易掩饰犯罪所得并转移价值，以使资金合法化，重点在于资金移动而非商品运输（Slide 42）。
- **报告与风险指标**：2020 年FATF报告及2021 年Egmont Group报告提供案例与风险指示器，帮助识别可疑贸易模式（Slide 43）。
- **贸易融资形式**：“开账交易”占约80%，被洗钱者利用因金融机构介入较少，涵盖贸易贷款、发票贴现、信用证等工具（Slide 44–45）。

### TBML风险与易受影响的产业（Slide 46–47）

- **高价值低批量与低价值高批量货物**：贵金属、二手纺织品等均易被利用；特点包括定价幅度大、长贸易周期及难以检查（Slide 46）。
- **具体易受影响产品**：黄金及贵金属、二手/豪华汽车、农产品、服装及二手纺织品、便携式电子产品（Slide 47）。

### 常见TBML手法（Slide 48–49）

- **价格与数量虚报**：发票金额或数量与实际不符。
- **虚构交易（幻影出货）**：无实际货物，仅伪造文件。
- **重复开票**：同一批货物多次索取支付。
- **空壳公司使用**：无实质资产或业务。
- **黑市比索交易**：国内资金为外贸付款提供渠道（Slide 48–49）。

### TBML利用贸易融资工具（Slide 51）

- **功能**：资金流动渠道、降低成本负担、通过银行掩饰资金来源。
- **工具**：进出口贸易贷款、发票贴现、信用证及其项下融资（Slide 51）。

### 打击TBML的挑战（Slide 52–56）

- **调查与起诉难点**：洗钱与前犯罪往往由不同团体执行，需证明被告知情且资金属犯罪所得，跨境犯罪增加取证难度（Slide 54）。
- **私营部门视角**：模式多变难预警，碎片化网络令单一机构仅见一部分，价格验证耗时且资料多样，开账贸易因文件少而更具吸引力（Slide 55–56）。

### TBML红旗信号（Slide 57–65）

- **客户层面**：交易结构异常复杂、偏离历史模式、高额费用邀约、回避沟通等（Slide 58–60）。
- **文件层面**：信用证与运输单据不符、合同或发票修改频繁、文件缺失或逻辑不清（Slide 60–62）。
- **交易层面**：循环交易、多中介、高风险支付方式、跨境转运路线不合理等（Slide 62–63）。
- **商品层面**：高风险商品（贵金属、军火等）、与客户常规业务不符、重大估价差异（Slide 64–65）。

### 计算机取证四步模型（Slide 67–72）

- **数据采集**：使用防写入设备对原始硬盘制作镜像以保全证据完整性，并建立举证链（Slide 69）。
- **验证**：通过哈希比对报告证明镜像与原盘一致，为后续分析提供法庭证据（Slide 70）。
- **调查分析**：在镜像上检索关键信息（关键词、日期、文件类型等），分类整理证据（Slide 71）。
- **报告**：出具证据报告、日志报告、保管表单及标准化审查协议，用于法庭提交（Slide 72）。

## 第六章

### 数据集不平衡定义 (Imbalanced Dataset) [第5页]

数据集不平衡（也称为**skewed dataset**）是指在分类问题中，各类别样本分布不均匀的情况。通常包含一个多数类（majority class）和一个少数类（minority class），例如在信用卡欺诈检测中，欺诈样本往往只占总样本的1%或更少 。

### 不平衡数据带来的问题 (Problems of Imbalance Dataset) [第6页]

1. 大多数机器学习模型假设各类别分布均匀
2. 模型更易学习多数类特征，导致对少数类的识别能力差
3. 轻度不平衡（如4:6）可勉强使用；严重不平衡时需特别处理 。

### 变动采样窗口 (Varying Sample Window) [第8页]

通过扩大观测时间窗口（observation period），增加少数类样本量。例如，将6个月样本扩展为12个月，或对同一少数类样本重复采样，以获得更多类似但不完全相同的样本 。

### 过采样 (Over-sampling) [第9页]

在不丢失任何样本信息的前提下，通过复制少数类样本来增加其数量，从而平衡类别分布。优点是保留了原始多数类和少数类信息 。

### 欠采样 (Under-sampling) [第10页]

通过随机删除多数类样本来减少其数量，以达到与少数类相近的比例，适用于多数类样本过多时，但会丢失部分信息 。

### ROSE (Random Over Sampling Examples) [第12页]

结合过采样和欠采样的方法，通过对少数类数据进行合成生成（augmented sampling），在保持类别分布的同时强化模型学习，对估计分类规则更准确有帮助 。

### SMOTE (Synthetic Minority Over-Sampling Technique) [第13–14页]

1. 对每个少数类样本计算k个最近邻
2. 随机选取其中n个邻居
3. 在样本与邻居之间线性插值生成新样本
    优点是合并过采样与欠采样，效果优于单纯的欠/过采样；缺点是若少数类样本分布边界含噪声，可能生成跨越类别的“桥接”样本 。

### ADASYN (Adaptive Synthetic Sampling) [第15页]

在SMOTE基础上，根据少数类样本周围邻居的“纯度比”（impurity ratio）自适应地生成合成样本。邻居多为多数类的少数类样本会生成更多新样本，增强模型对难学样本的关注 。

### 线性回归 (Linear Regression) [第17–18页]

用于预测连续目标变量Y与多个自变量X₁…Xₙ之间的线性关系，目标是最小化均方误差（MSE），拟合直线公式：
 Y=β0+β1X1+⋯+βnXn+εY = β_0 + β_1 X_1 + \dots + β_n X_n + ε
 残差（residuals）为预测值与真实值之差 。

### 回归系数解释 (Interpretation of Coefficients) [第19页]

- **斜率βᵢ**：在其他变量不变时，Xᵢ每增加1单位，Y的期望变化量
- **截距β₀**：当所有X=0时Y的期望值（在X从不为0时无实际意义） 。

### 回归性能评估指标 (Regression Performance Measures) [第20–22页]

- **MAE (Mean Absolute Error)**：平均绝对误差
- **MSE (Mean Squared Error)**：平均平方误差，更敏感异常值
- **RMSE (Root MSE)**：MSE开方，量纲与原变量一致 。

### 决定系数R² (R-Squared) [第24页]

表示回归模型解释的总方差比例，即1 – (残差平方和/总平方和)，值越接近1，模型拟合越好 。

### 调整后R² (Adjusted R-Squared) [第25页]

在R²基础上惩罚无关自变量，增加自变量不一定提升Adjusted R²，用于多元回归模型对比 。

### 线性回归优缺点 (Linear Regression Advantages & Disadvantages) [第26页]

**优点**：可解释性强、简单、高效
 **缺点**：表达能力有限、对异常值敏感、需满足线性、正态性、同方差性假设 。

### 逻辑回归 (Logistic Regression) [第27–28页]

适用于二分类问题，通过logit函数将概率映射至线性模型：
 logit(p)=ln⁡p1−p=β0+β1X1+⋯+βnXn\text{logit}(p)=\ln\frac{p}{1-p}=β_0 + β_1 X_1 + \dots + β_n X_n
 输出为[0,1]之间的概率 。

### 概率、赔率与对数几率 (Probability, Odds & Log-Odds) [第29–30页]

- **概率p**：事件发生比例
- **赔率(p/(1-p))**：事件发生与不发生之比
- **对数几率logit(p)**：赔率取自然对数，用于线性化 。

### 逻辑回归性能指标 (Logistic Regression Metrics) [第33–35页]

- **AIC (Akaike Information Criterion)**：评估拟合优度并惩罚复杂度，值越低越好
- **BIC (Bayesian Information Criterion)**：惩罚更严格 。

### 训练/验证/测试集划分 (Data Splitting) [第39–45页]

- 常见比例：70%训练+30%测试，或40%训练+30%验证+30%测试
- **训练集**：构建模型
- **验证集**：调参、早停
- **测试集**：评估最终性能，防止过拟合 。

### 混淆矩阵 (Confusion Matrix) [第48页]

二分类结果的TP、FP、FN、TN分布，用于进一步计算多种分类性能指标 。

### 准确率 Accuracy [第49页]

( TP + TN ) / 总样本数，易受类别不平衡影响 。

### 召回率 Recall (Sensitivity) [第51页]

TP / (TP + FN)，衡量少数类（如欺诈）被正确识别的比例 。

### 精确率 Precision [第52页]

TP / (TP + FP)，衡量预测为少数类中真正少数类的比例 。

### F1 分数 F1-Score [第53页]

Precision和Recall的调和平均，综合考虑FP和FN 。

### 特异度/假阳率 (TNR & FPR) [第55页]

- **TNR (Specificity)** = TN / (FP + TN)
- **FPR** = 1 – TNR 。

### ROC曲线与AUC (ROC Curve & AUC) [第56–59页]

通过改变预测阈值绘制TPR对FPR曲线，AUC代表曲线下面积，越接近1区分能力越强 。

### 决策树基础 (Decision Tree Basics) [第77页]

由根节点(root)、决策节点(decision nodes)和叶节点(leaf/terminal nodes)组成，用于分类或回归 。

### 划分与停止决策 (Splitting & Stopping Decisions) [第78页]

- **划分决策**：选择哪个属性、何种阈值进行分裂
- **停止决策**：何时停止分裂（如最大深度、最小样本数）
- **赋值决策**：叶节点类别或回归值的确定 。

### 纯度度量 (Impurity Measures) [第79页]

分类使用**基尼系数 (Gini impurity)\**或\**信息熵 (entropy)**，回归使用**方差 (variance)**衡量节点纯度 。

### 信息增益示例 (Information Gain Example) [第80–82页]

以“AGE”和“INCOME”为划分属性，计算IG(D,AGE)和IG(D,INCOME)，选择IG更大的属性进行分裂 。

### 回归树 (Regression Tree) [第83页]

对连续目标变量，节点分裂以最小化子节点内MSE为目标，实现回归预测 。

### 分类树 vs 回归树 (Classification vs Regression Tree) [第84–85页]

- **分类树**：叶节点输出类别模式(mode)
- **回归树**：叶节点输出均值(mean) 。

### 剪枝与过拟合 (Pruning & Overfitting) [第86–87页]

- **过拟合**：树过深，训练误差低但测试误差高
- **预剪枝**：提前停止分裂
- **后剪枝**：先生成全树，再基于验证集剪枝 。

### 决策树优缺点 (Decision Tree Advantages & Disadvantages) [第89页]

**优点**：易解释、处理缺失值、可处理混合变量
 **缺点**：易过拟合、不稳定、离散化连续变量 。

### 集成学习概述 (Ensemble Learning) [第92–93页]

通过组合多个“基模型”（weak learners）提高性能与鲁棒性。分为同质集成（homogeneous）和异质集成（heterogeneous） 。

### Bagging, Boosting, Stacking [第94页]

- **Bagging**：并行训练同质模型，降低方差
- **Boosting**：序列化训练同质模型，降低偏差
- **Stacking**：并行训练异质模型，再训练元模型融合 。

### 自助抽样 (Bootstrap Sampling) [第95–96页]

从原始样本重复有放回抽样，生成多份子样本，再对每份子样本训练模型并汇总统计量 。

### Bagging流程与示例 (Bagging Procedure & Example) [第97–98页]

1. 对原始数据集抽取N个bootstrap样本
2. 分别训练N个分类器/回归器
3. 分类采用多数投票，回归取平均，得到最终预测 。

## 第七章

### 集成学习定义 (Ensemble Learning) [第4页]

集成学习是一种将多个预测模型（也称为**基模型**或**弱学习器**）组合在一起以改进性能的机器学习方法。其主要优势包括：

- **性能提升 (Performance)**：通过结合多个模型的预测，整体预测效果通常优于任何单一模型。
- **鲁棒性增强 (Robustness)**：集成可以降低单模型预测结果的方差，使性能更稳定 。

### 同质与异质集成 (Homogeneous vs Heterogeneous Ensembles) [第5页]

- **同质集成 (Homogeneous)**：使用相同类型的基模型并行训练，如多个决策树。
- **异质集成 (Heterogeneous)**：使用不同类型的基模型并行训练，并通过元模型（meta-model）进行融合。

> **Note**：选取不同基模型时，需要考虑如何对它们的输出进行合理汇总 。

### Bagging、Boosting 与 Stacking [第7页]

- **Bagging (Bootstrap Aggregating)**：同质基模型并行训练，通过对训练集进行**有放回抽样 (Bootstrap Sampling)\**生成多个子集，每个子集训练一个模型，最终分类采用“多数投票”、回归取平均，旨在\**降低方差 (reduce variance)** 。
- **Boosting**：同质基模型串行训练，每一轮通过强调前一轮分类错误的样本来调整样本权重，最终按确定性策略加权融合，旨在**降低偏差 (reduce bias)** 。
- **Stacking**：异质基模型并行训练，然后训练一个**元模型 (meta-model)**以不同基模型的预测结果为输入，实现性能提升 。

### 有放回抽样过程 (Bootstrap Sampling) [第8–9页]

1. 选定抽样次数与样本大小；
2. 每次从原始数据集中随机**有放回**地抽取子样本，保证样本分布代表原始总体；
3. 在每个子样本上计算统计量，最终取其均值作为估计结果。
    该方法基于**大数定律 (law of large numbers)**，重复抽样可逼近总体分布 。

------

### 随机森林概述 (Random Forest) [第14页]

随机森林由多棵决策树组成，每棵树在：

1. **有放回抽样**生成的Bootstrap样本上训练；
2. 每个节点仅从**随机子集特征 (random subset of features)**中选取最优分裂，通常子集大小m=1,2或⌊log₂(N)+1⌋；
    通过样本和特征的双随机化来增加树间差异性，最终多数投票或平均预测 。

### 随机森林训练步骤 (RF Training Steps) [第14–16页]

1. **Step 1**：从原始数据产生Bootstrap样本；
2. **Step 2**：在该样本上构建决策树，每个节点随机选取m个特征进行分裂；
3. **Step 3**：重复以上过程T次，得到T棵树；
    适用于分类和回归任务 。

### 包外样本评估 (Out-of-Bag, OOB) [第17页]

未被抽中进入某棵树训练的样本称为该树的**包外样本 (OOB sample)**，可用于：

- 将OOB样本输入未见过它们的所有树，记录多数预测；
- 计算**OOB分数 (OOB score)**，即包外样本的预测准确率，作为无偏误的模型评估指标 。

### 随机森林优缺点 (RF Advantages & Disadvantages) [第18页]

- **优点**：预测性能优秀，能处理高维特征且样本量少；
- **缺点**：属于**黑盒模型 (black-box model)**，可通过**特征重要性 (variable importance)**分析来辅助解释 。

### 特征重要性解释 (Variable Importance) [第19–23页]

- **全局解释 (Overall Interpretation)**：评估哪些特征对整体模型最重要；
- **局部解释 (Local Interpretation)**：分析单个观测的预测是由哪些特征驱动。
   常用两种计算方法：

1. **Mean Decrease in Impurity (MDI)**：基于所有树在节点分裂时**基尼不纯度 (Gini impurity)**的减少量累积；
2. **Mean Decrease in Accuracy (MDA)**：在OOB样本上随机打乱某特征值后，计算准确率下降程度 。

------

### 人工神经网络概念 (Artificial Neural Network) [第45页]

- 模拟人脑结构的数学模型，由输入层、一个或多个**隐藏层 (hidden layers)**和输出层组成；
- **前馈网络 (Feedforward ANN)**信息单向传播，无循环；
- **反馈网络 (Recurrent ANN)**含循环，信息可在层间往返 。

### 神经元结构 (Neuron Structure) [第48页]

- **组合函数 (combination function)**：加权求和输入与偏置；
- **激活函数 (activation function)**：线性或非线性映射，如ReLU、Sigmoid、Tanh、Softplus，用于引入非线性 。

### 常见激活函数 (Activation Functions) [第50–53页]

- **线性 (Linear)**：仅适用于线性可分问题；
- **阶跃 (Threshold)**：输出0或1；
- **Sigmoid**：将输出映射至(0,1)，梯度平滑；
- **Tanh**：零中心化，输出(-1,1)；
- **ReLU**：max(0,x)；
- **Softplus**：ln(1+eˣ)，输出(0,∞) 。

### 网络训练 (Network Training) [第55–57页]

- 使用**损失函数 (loss/cost function)**（如均方误差MSE）评估预测误差；
- **Epoch**：对完整训练集的单次迭代，多Epoch训练直至收敛；
- 对欺诈分析通常仅需一隐藏层，隐藏层用非线性激活，输出层二分类用Sigmoid 。

### 神经网络解释 (NN Interpretation) [第60–66页]

1. **变量选择 (Variable Selection)**：通过权重可视化（如Hinton图）筛除贡献小的输入；
2. **规则提取 (Rule Extraction)**：
   - **分解式 (Decompositional)**：聚类隐藏单元激活并提取输入—隐藏—输出规则；
   - **教学式 (Pedagogical)**：将NN视为黑盒，用决策树等白盒模型学习NN预测；
3. **双阶段模型 (Two-Stage Models)**：先用可解释模型，再用第二阶段模型拟合其残差 。

### 神经网络优缺点 (NN Advantages & Disadvantages) [第69页]

- **优点**：支持多种输入、非线性映射，适用广泛；
- **缺点**：黑盒模型、易过拟合、需仔细预处理输入 。

------

### 支持向量机概述 (Support Vector Machine) [第76页]

用于分类与回归，目标是在特征空间中寻找**最优分隔超平面 (hyperplane)**，使两类样本间**间隔 (margin)**最大化 。

### 最大化间隔与软间隔 (Margin & Soft Margin) [第77–79页]

- **支持向量 (support vectors)**：距离超平面最近的样本；
- 引入误差项εₖ与**正则化参数C**以平衡间隔最大化与错误分类最小化 。

### 核技巧 (Kernel Trick) [第80–81页]

- 通过映射ϕ(x)将数据提升至高维空间，利用内积计算避免显式变换；
- 常见核函数包括线性、多项式、径向基函数(RBF)等 。

### 超参数调优 (Hyperparameter Tuning) [第83–85页]

- **Gamma (γ)**：控制RBF核影响范围；
- **C**：控制软间隔惩罚强度；
- 典型流程：40%/30%/30%分割数据，网格搜索最佳(γ,C)，再在训练+验证集上重训并测试 。

### SVM优缺点 (SVM Advantages & Disadvantages) [第87页]

- **优点**：适用于高维空间、记忆高效，仅依赖支持向量；
- **缺点**：对大规模和高噪声数据表现欠佳，核函数选择与调优成本高 。

## 第八章

### K折交叉验证 (K-fold Cross-Validation) [第5页]

交叉验证是在样本量非常小（如少于1000条观测）时常用的评估方法。将原始数据随机分成K个互不重叠的子集，其中K−1个子集用于**训练**（training），剩余1个子集用于**评估**（evaluation）。重复K次，使每个子集都能做一次测试集，最终将K次得到的误差（test errors）取平均，作为模型的性能估计 。

### 选择K的取值 (How to Choose K) [第6页]

- 应保证每个训练/测试组对总体具有代表性（representative）。
- 常用K=5或10，此时既能控制偏差（bias）又能保持方差（variance）适中。
- 当K=n时，即留一交叉验证（leave-one-out），每次用1个样本做测试，其余n−1个做训练，适用于极小数据集 。

### 多模型选择 (Model Selection via Cross-Validation) [第7页]

当通过交叉验证训练得到多个模型时，可采用以下策略来选取最终模型：

1. 类似集成学习（ensemble）使用投票（voting）方法；
2. 留一法（leave-one-out）可随机挑选一个模型，因仅差异于一个观测，其性能应相近；
3. 使用所有观测做训练，交叉验证的性能作为对模型的独立估计 。

### 多类别问题处理 (Handling Multiple Classes) [第8页]

在欺诈检测中，除了“Fraud”、“No fraud”二分类外，有时需使用更多标签：

- **名义型标签**（nominal labels）：如“Fraud”、“Suspected fraud”、“No fraud”。
- **有序型标签**（ordinal labels）：如“Severe fraud”、“Medium fraud”、“Light fraud”、“No fraud”。
   所有前述的分类模型都可扩展到多类别分类（multiclass classification）场景 。

### 多类别逻辑回归 (Logistic Regression for Multiclass) [第10–11页]

对名义型目标，可选定类别K为**基类**（base class），并基于概率总和为1的约束，分别对其他类别构建logit模型，参数通过最大后验估计（maximum a posteriori）确定 。

### 多类别决策树 (Decision Tree for Multiclass) [第12页]

决策树同样易于扩展至多类别。将**不纯度指标**（impurity criterion）修改为适用于K类别的形式，其**划分决策**（splitting decision）和**停止决策**（stopping decision）与二分类保持一致 。

### 多类别神经网络 (Neural Network for Multiclass) [第13页]

只需将输出层神经元数增加到K，对应K个类别，预测时选择激活值最高的输出神经元。网络结构和训练方法与二分类相同 。

### 聚类分析简介 (Clustering Overview) [第23页]

聚类是一种**无监督分类**（unsupervised classification），没有预定义的目标类别，簇数和簇的含义未知，且不同簇可能具有歧义，需要根据具体业务或统计指标来决定最佳簇数 。

### 连续变量距离度量 (Distance Metrics for Continuous Variables) [第25页]

当输入为连续变量时，可使用**明可夫斯基距离**（Minkowski distance）：

- 当p=1时，为曼哈顿距离（Manhattan distance）；
- 当p=2时，为欧氏距离（Euclidean distance）。
   例如两点(50,20)与(30,10)之间的欧氏距离为√[(50−30)²+(20−10)²]=√500≈22 。

### 分类变量距离度量 (Distance Metrics for Categorical Variables) [第27页]

对二元类别（Yes/No），可用**简单匹配系数**（Simple Matching Coefficient, SMC）或**雅卡尔指数**（Jaccard Index）。

- SMC将“Yes–Yes”和“No–No”视为同等匹配；
- Jaccard只计算“Yes–Yes”匹配，忽略“No–No”，适用于红旗指标少而乱的场景 。

### 聚类算法类型 (Types of Clustering Algorithms) [第30页]

- **连通性**（connectivity-based）：如层次聚类（hierarchical）按距离聚点。
- **中心点**（centroid-based）：如K均值（K-means），以簇中心代表簇。
- **分布式**（distribution-based）：如高斯混合模型（GMM），基于概率分布。
- **密度型**（density-based）：如DBSCAN/OPTICS，定义高密度区域，稀疏点为噪声 。

### K均值聚类原理 (K-means Clustering Basics) [第31–32页]

1. 指定簇数K；
2. 随机选K个观察值为初始中心（seeds）；
3. 将每个观察分配到最近中心；
4. 重新计算各簇中心；
5. 重复3–4直到中心不变或达到迭代上限 。

### K均值聚类示例 (K-means Example, K=2) [第33–38页]

- 随机选2个种子；
- 将观测分配到最近中心；
- 计算新的中心；
- 重复分配与中心计算，直至中心收敛 。

### K均值优缺点 (K-means Advantages & Disadvantages) [第33页]

**优点**：计算效率较高、易实现、可扩展到大数据集；
 **缺点**：需预先指定K、易陷入局部最优、对异常值和噪声敏感 。

### 簇解释方法 (Cluster Interpretation) [第34页]

可比较簇内外指标分布差异，如簇C1的“近端值”（recency）低而“金额”（monetary）高，也可借助决策树将簇标签作为目标，利用监督学习技术解释聚类结果 。

### 聚类评估指标 (Clustering Evaluation) [第35页]

- **组内平方和**（Within-cluster SSE, WSS）：越低簇内越同质；
- **组间平方和**（Between-cluster SSE, BSS）：越高簇间越异质；
   无监督场景下可结合**统计视角**与**可解释性**一起评估 。

### 最优簇数确定：肘部法 (Elbow Method) [第36页]

1. 对不同K运行K均值并计算WSS；
2. 绘制WSS对K曲线；
3. 在“肘部”（曲线出现弯折）处选取K，作为最佳簇数 。

### 最优簇数确定：轮廓系数法 (Average Silhouette Method) [第37页]

1. 对不同K计算各观测的轮廓系数，并取平均；
2. 绘制平均轮廓系数对K曲线；
3. 在最大值对应的K处选取最佳簇数 。

### 保险欺诈案例 (Insurance Fraud Case Study) [第47–51页]

- 保险欺诈类型包括人寿险、健康险、车险等，涉及**代理人**（agent）、**投保人**（subscriber）、**服务提供者**（provider）及合谋欺诈。
- 欺诈情景识别需考虑主体（如假服务方、真实共谋方）、行为（夸大索赔、伪造病史等），并生成场景组合（permutation of fraud scenarios） 。

### 欺诈分析流程 (Fraud Analytics Methodology) [第51–54页]

1. 定义范围（scope），如针对医疗保险索赔；
2. 场景识别（scenario identification）；
3. 分析策略（data analytics strategies），包括特征选择、变换（transformation）、异常检测；
4. 模型选择（model selection），本例采用**聚类分析**以最大化簇内同质性和簇间异质性 。

### EDA实例：医疗保险欺诈 (EDA Example: Health Insurance Fraud) [第61–63页]

- 数据集来自CMS，美国医保和医疗补助服务中心；
- 观察到**负支付**（negative payments）异常，需要核实；
- 有28名受益人在一年内住院天数>365天，超出合理范围 。

### 聚类分析结果与解读 (Cluster Analysis Results & Interpretation) [第64–68页]

- 在7簇分析中，簇2对应长住院期、短旅行距离和高支付；簇1、5、6、7为短住院、短距离、小支付；簇3和4分别揭示新异常模式（长距离小支付、大支付短住院）。
- 通过聚类将可疑索赔从195,343条缩减至3,718条，更便于人工审查 。

### R语言示例：聚类分析 (Clustering in R Example) [第70–80页]

- 数据源为BankSim模拟器生成的银行交易数据；
- 流程包含EDA、特征工程（feature engineering）、去除无关列、标准化（scaling）、矩阵转换；
- 使用gap_stat、wss或silhouette函数绘制碎石图（scree plot）或评估轮廓系数；
- 调用kmeans进行聚类，并检查聚类结果与原始标签对比 。

## 第九章

本次讲座的议程包括三个主要部分：

- 单类支持向量机：单类异常检测 (One-Class SVM: Anomaly Detection with a Single Class)
- 本福特定律 (Benford's Law)
- 案例研究 - 洗钱方案 (Case study - Money Laundering Scheme)。

### 支持向量机 (Support Vector Machines, SVM) (PPT, Page 4-5)

- **定义:** 支持向量机 (Support Vector Machine, SVM) 是一种**监督学习模型 (supervised learning model)**，既可以用于**分类 (classification)** 任务，也可以用于**回归 (regression)** 任务。
- **常见用途:** 更常用于分类任务。
- **基本思想:** 寻找一条线或一个**超平面 (hyperplane)**，能够最好地将数据集分成两个类别。

### 决策边界 (Decision Boundary) (PPT, Page 6)

- **概念:** 决策边界 (Decision Boundary) 是将不同类别数据点分开的界限。
- 不同维度下的表示:
  - **一维 (1-d):** 一个点 (a dot)
  - **二维 (2-d):** 一条线 (a line)
  - **n 维 (n-d):** 一个超平面 (a hyperplane)
- **最佳决策边界 (Best Decision Boundary):** 在多条可能的决策边界中，寻找能够最佳地分离两个类别的边界。例如，在图中，B2 被认为是最佳的决策边界，因为它能最大化**间隔 (margin)**。

### 支持向量 (Support Vectors) 和间隔 (Margin) (PPT, Page 7-8)

- **支持向量 (Support Vectors):** 离决策边界最近的数据点。这些点对于定义决策边界至关重要。
- **间隔 (Margin):** 支持向量与决策边界之间的距离。SVM 的目标是最大化这个间隔。
- **最大间隔超平面 (Maximum Margin Hyperplane):** 能够最大化间隔的决策边界。
- **作用:** 最大化间隔有助于提高模型的**泛化能力 (generalization ability)**，因为它在保持数据点尽可能远离决策边界的同时，降低了**过拟合 (overfitting)** 的风险。

### 软间隔 (Soft Margin) SVM (PPT, Page 9-11)

- **问题:** 现实世界的数据通常不是**线性可分离的 (linearly separable)**，这意味着无法找到一条直线（或超平面）完美地将两个类别分开。数据集中可能存在**异常值 (outliers)** 或**噪声 (noise)**。

- **解决方案:** 软间隔 (Soft Margin) SVM 引入了**惩罚项 (penalty term)**，允许一些数据点落在间隔内或决策边界的错误一侧。

- **目标:** 在最大化间隔的同时，最小化分类错误的惩罚。

- **松弛变量 (Slack Variables, ξ):** 用于度量数据点违反间隔或位于错误一侧的程度。

- 惩罚参数 (Cost Parameter, C):

   控制对错误分类的惩罚程度。

  - C 值越大，惩罚越重，模型会更倾向于减小分类错误，即使这可能导致更小的间隔。
  - C 值越小，惩罚越轻，模型会更倾向于更大的间隔，允许更多的分类错误。

- 优化目标:

  w,b,ξmin21∣∣w∣∣2+Ci=1∑nξi

  - 其中，w 是超平面的法向量，b 是偏置项，ξi 是第 i 个数据点的松弛变量。
  - 约束条件为： yi(w⋅xi+b)≥1−ξi ξi≥0
  - 此目标函数旨在在最大化间隔（由 21∣∣w∣∣2 最小化实现）和最小化分类错误（由 C∑i=1nξi 最小化实现）之间取得平衡。

### 核函数 (Kernel Functions) (PPT, Page 12-14)

- **概念:** 当数据在原始特征空间 (original feature space) 中不是线性可分离时，核函数 (Kernel Functions) 可以将数据映射到更高维的**特征空间 (feature space)**，从而使其在该新空间中变得线性可分离。
- **核技巧 (Kernel Trick):** 避免了显式地计算高维特征，而是直接计算高维空间中的内积。这使得在实践中处理高维数据成为可能，而无需承担巨大的计算成本。
- 常用核函数:
  - **线性核 (Linear Kernel):** K(xi,xj)=xiTxj。适用于数据本身线性可分离的情况。
  - **多项式核 (Polynomial Kernel):** K(xi,xj)=(γxiTxj+r)d。适用于数据具有多项式关系的情况。
  - **径向基函数核 (Radial Basis Function Kernel, RBF Kernel) / 高斯核 (Gaussian Kernel):** K(xi,xj)=exp(−γ∣∣xi−xj∣∣2)。这是最常用的核函数之一，适用于非线性、复杂关系的数据。γ 参数控制了核函数的宽度。
  - **Sigmoid 核 (Sigmoid Kernel):** K(xi,xj)=tanh(γxiTxj+r)。在某些神经网络中也用作激活函数。

### 单类支持向量机 (One-Class SVM) (PPT, Page 15-18)

- **目的:** 异常检测 (Anomaly Detection) 或离群点检测 (Outlier Detection)。与传统 SVM 针对分类任务不同，One-Class SVM 用于识别与正常数据模式显著不同的数据点。

- **应用场景:** 当只有正常数据可用，而异常数据很少或难以定义时。例如，在欺诈检测中，通常只有大量的正常交易数据，而欺诈交易数据非常稀少。

- **基本思想:** 学习一个边界，能够将大部分正常数据点包围起来。任何落在该边界之外的数据点都被视为异常。

- **核心思想 (PPT, Page 16):** One-Class SVM 的目标是找到一个最优的超平面，将所有训练数据点从原点 (origin) 分离出来，并且最大化从原点到该超平面的距离。

- **软间隔扩展 (Soft Margin Extension) (PPT, Page 17):** 类似标准的软间隔 SVM，One-Class SVM 也允许部分数据点（被认为是异常点）落在超平面的错误一侧或间隔内。这通过引入松弛变量 ξi 和惩罚参数 C 实现。

- 优化目标 (PPT, Page 18):

  w,ρ,ξmin21∣∣w∣∣2+νn1i=1∑nξi−ρ

  - 其中，w 是超平面的法向量，ρ 是超平面到原点的距离，n 是训练样本的数量。

  - ν∈(0,1]

     是一个控制异常点比例的参数：

    - 它为异常点（落在决策边界外部的样本）的比例设置了上限。
    - 它为支持向量（在决策边界上的样本）的比例设置了下限。

  - 约束条件为： w⋅ϕ(xi)≥ρ−ξi ξi≥0

  - ϕ(xi) 是将数据点 xi 映射到高维特征空间的函数。

### One-Class SVM 的超参数 (**ν** 和 **γ**) (PPT, Page 19-20)

- ν (Nu):
  - 代表模型允许的异常值的预期比例，通常设置在 0 到 1 之间。
  - 较小的 ν 值会创建一个更紧密的边界，将更多的点视为异常。
  - 较大的 ν 值会创建一个更宽松的边界，将更少的点视为异常。
- γ (Gamma):
  - RBF 核函数中的参数，控制了单个训练样本的影响范围。
  - 较小的 γ 值表示影响范围更大，模型的决策边界更平滑。
  - 较大的 γ 值表示影响范围更小，模型的决策边界更复杂，可能导致过拟合。
- **参数选择 (PPT, Page 20):** ν 通常通过交叉验证 (cross-validation) 进行调优。

### 欺诈检测案例 (PPT, Page 21-22)

- **场景:** 使用 One-Class SVM 进行欺诈检测。
- **假设:** 绝大多数交易是正常的。
- 步骤:
  1. **训练模型:** 使用大量的正常交易数据训练 One-Class SVM 模型，使其学习正常交易的模式。
  2. **识别异常:** 将新的交易数据输入训练好的模型。如果交易落在模型定义的“正常”区域之外，则将其标记为潜在的欺诈行为。
- 挑战:
  - **参数选择:** 确定最佳的 ν 和 γ 参数是关键。
  - **数据非平稳性 (Data Non-stationarity):** 欺诈模式可能会随着时间演变，导致模型需要定期更新和重新训练。
  - **标签数据稀缺 (Scarcity of Labeled Data):** 很难获取标记好的欺诈数据来评估模型。

### 本福特定律 (Benford's Law) (PPT, Page 23-24)

- **别名:** 第一位数字定律 (First-Digit Law)。

- **内容:** 在许多自然产生的数值数据集中，首位数字的出现频率不是均匀分布的，而是遵循一个特定的对数分布。数字 1 作为首位数字出现的频率最高，其次是 2，以此类推，9 的出现频率最低。

- 分布概率 (PPT, Page 24):

   首位数字 d(d∈{1,…,9}) 的概率为：$P(D_1=d)=\log_{10}(1+d_1)$

  - 根据此公式，数字 1 出现的概率约为 30.1%，数字 9 出现的概率约为 4.6%。

- **适用范围:** 适用于跨越几个数量级的数据集，例如人口数据、股价、发票金额、电费账单等。

- **不适用范围:** 预先设定了范围的数字（例如身份证号码、电话号码）、受人为限制的数字（例如某个固定阈值以下或以上的数据）。

#### 本福特定律在欺诈分析中的应用 (PPT, Page 25-27)

- **检测异常 (PPT, Page 25):** 通过比较实际数据集中首位数字的分布与本福特定律预测的分布，可以发现潜在的异常或欺诈行为。
- **欺诈指标 (Fraud Indicator):** 如果某个数据集的首位数字分布与本福特定律显著偏离，可能表明数据是被人为操纵或伪造的。
- **应用领域:** 审计、选举舞弊检测、财务欺诈、科学研究中的数据真实性检查等。
- 局限性 (PPT, Page 27):
  - **数据量要求:** 需要足够大的数据集才能显示出本福特定律的分布模式。
  - **数据性质:** 并非所有数据都遵循本福特定律（如前所述）。
  - **仅为指标:** 偏离本福特定律只是欺诈的潜在指标，不能作为确凿证据。需要结合其他分析方法。

#### 洗钱案例研究 (Case Study - Money Laundering Scheme) (PPT, Page 28)

- **洗钱 (Money Laundering):** 将非法获得的资金（“黑钱”）通过一系列交易和金融操作，使其看起来像是合法来源的资金（“白钱”）的过程。
- **目标:** 掩盖非法资金的来源和所有权。

#### 洗钱的三个阶段 (Three Stages of Money Laundering) (PPT, Page 29)

1. 安置 (Placement):

    将非法资金引入金融系统。

   - **方法:** 小额存款、购买货币工具（如汇票、旅行支票）、兑换外币、走私现金等。
   - **目的:** 将大量现金转换为更容易移动和隐藏的金融资产。

2. 分层 (Layering):

    通过复杂的交易链条混淆资金来源，使其难以追溯。

   - **方法:** 频繁的银行间转账、购买和出售资产（如房地产、股票、债券）、设立空壳公司、国际汇款等。
   - **目的:** 制造复杂的交易路径，切断资金与犯罪活动之间的联系。

3. 整合 (Integration):

    将洗干净的资金重新投入合法经济体系，使其看起来完全合法。

   - **方法:** 投资合法企业、购买奢侈品、房地产、通过工资或股息提取资金等。
   - **目的:** 让非法所得的资金看起来是合法商业活动的结果。

#### 洗钱检测挑战 (Money Laundering Detection Challenges) (PPT, Page 30)

- **数据量大 (Huge Data Volume):** 金融交易数据量庞大，难以人工审查。
- **交易复杂性 (Complex Transactions):** 洗钱者会设计复杂的交易模式以逃避检测。
- **误报率高 (High False Positive Rate):** 许多合法交易可能与洗钱模式相似，导致大量误报。
- **模型可解释性 (Model Interpretability):** 需要理解模型为何将某些交易标记为可疑，以便后续调查。

#### 检测洗钱的方法 (Methods to Detect Money Laundering) (PPT, Page 31-33)

- 数据分析技术 (Data Analytics Techniques):

  - **规则匹配 (Rule-Based Matching):** 基于预定义的洗钱模式和阈值来识别可疑交易。
  - **统计分析 (Statistical Analysis):** 使用统计方法（如均值、标准差、离群值检测）识别异常模式。
  - 机器学习 (Machine Learning):
    - **监督学习 (Supervised Learning):** 需要有标记的洗钱数据，用于训练分类模型。
    - **无监督学习 (Unsupervised Learning):** 在没有标记数据的情况下，识别异常行为或聚类可疑模式。
    - **半监督学习 (Semi-Supervised Learning):** 结合少量标记数据和大量未标记数据进行训练。
  - **社交网络分析 (Social Network Analysis, SNA):** 分析交易实体之间的关系网络，识别异常连接或模式。

- 规则匹配 (Rule-Based Matching) (PPT, Page 32):

  - **优点:** 简单、易于理解和实现。
  - **缺点:** 缺乏灵活性，难以适应新的洗钱模式；易产生高误报率；可能被洗钱者规避。
  - **例子:** 频繁的小额现金存款、大额现金交易、资金从多个账户流入一个账户等。

- 机器学习 (Machine Learning) (PPT, Page 33):

  - **优点:** 能够发现隐藏的模式，适应性强，可以处理复杂数据。
  - **缺点:** 需要大量数据进行训练，模型的**可解释性 (interpretability)** 可能较差。
  - 模型类型:
    - **监督学习 (Supervised Learning):** 分类模型（如决策树、随机森林、神经网络）。
    - **无监督学习 (Unsupervised Learning):** 聚类（如 K-Means）、异常检测（如 One-Class SVM）。

- 社交网络分析 (Social Network Analysis, SNA) (PPT, Page 34-36)

  - **目的:** 识别洗钱网络中的关键参与者和交易模式。

  - 方法:

    - **节点 (Nodes):** 参与交易的实体（个人、公司、账户）。
    - **边 (Edges):** 交易关系（资金流动、共同联系）。
    - **图结构 (Graph Structure):** 分析网络中的连接、密度、中心性等。

  - 关键指标 (PPT, Page 35):

    - 中心性 (Centrality):

       衡量节点在网络中的重要性。包括：

      - **度中心性 (Degree Centrality):** 与其他节点的连接数量。
      - **介数中心性 (Betweenness Centrality):** 作为其他节点之间最短路径的桥梁数量。
      - **接近中心性 (Closeness Centrality):** 到所有其他节点的平均距离。
      - **特征向量中心性 (Eigenvector Centrality):** 衡量与重要节点连接的重要性。

    - **社区检测 (Community Detection):** 识别网络中的紧密连接组。

  - 应用 (PPT, Page 36):

    - 识别可疑交易群体。
    - 发现新的洗钱模式。
    - 追踪资金流向。

#### 基于异常的欺诈检测模型构建步骤 (Steps for Building Anomaly-Based Fraud Detection Models) (PPT, Page 37)

1. **数据收集与准备 (Data Collection and Preparation):** 获取相关的交易数据、客户数据、历史欺诈数据等，并进行清洗、转换和特征工程。
2. **特征工程 (Feature Engineering):** 从原始数据中提取和创建有用的特征，以更好地描述交易和实体行为。
3. **模型选择 (Model Selection):** 根据问题类型和数据特性选择合适的机器学习模型（如 One-Class SVM、聚类算法等）。
4. **模型训练 (Model Training):** 使用正常数据训练模型，使其学习正常模式。
5. **模型评估 (Model Evaluation):** 使用各种指标（如准确率、召回率、F1 分数、AUC-ROC 曲线）评估模型的性能。
6. **部署与监控 (Deployment and Monitoring):** 将模型部署到生产环境，并持续监控其性能，及时调整和更新。

#### 示例：欺诈风险评分 (Fraud Risk Scoring) (PPT, Page 38-39)

- **概念:** 为每笔交易或每个账户分配一个**欺诈风险分数 (fraud risk score)**。分数越高，表示该交易或账户是欺诈的可能性越大。
- **阈值 (Threshold):** 设定一个阈值，超过该阈值的交易将被标记为可疑，需要人工审查或进一步调查。
- 例子 (PPT, Page 39):
  - 如果风险分数 > 0.9，则将交易标记为高风险。
  - 0.7 < 风险分数 <= 0.9，则为中风险。
  - 风险分数 <= 0.7，则为低风险。

#### 关联规则分析 (Association Rule Analysis) (PPT, Page 40-42)

- **目的:** 发现数据集中项之间的有趣关系或关联。

- 基本概念 (PPT, Page 40):

  - **项集 (Itemset):** 一组同时出现的项目（如商品、交易特征）。
  - **频繁项集 (Frequent Itemset):** 出现频率高于预定义最小支持度 (minimum support) 的项集。
  - **关联规则 (Association Rule):** 形如 X⇒Y，表示如果购买了 X（或发生了 X），那么很可能也会购买 Y（或发生 Y）。X 称为**先行项 (antecedent)**， Y 称为**后继项 (consequent)**。

- 度量标准 (Measures) (PPT, Page 41):

  - 支持度 (Support):

     项集在数据集中出现的频率。

    Support(X)=Total number of transactionsNumber of transactions containing X

    - 用于衡量项集的普遍性。

  - 置信度 (Confidence):

     规则的强度，表示在 X出现的情况下 Y出现的条件概率。$Confidence(X⇒Y)=Support(X)Support(X∪Y)$

    - 用于衡量规则的可靠性。

  - 提升度 (Lift):

    衡量 X和 Y之间的关联强度是否高于随机情况。

    $Lift(X⇒Y)=Support(X)×Support(Y)Support(X∪Y)=Support(Y)Confidence(X⇒Y)$

    - **Lift > 1:** X 和 Y 之间存在正相关。
    - **Lift = 1:** X 和 Y 之间相互独立。
    - **Lift < 1:** X 和 Y 之间存在负相关。

- **选择的关联规则 (Selected Association Rule) (PPT, Page 42):** 通常指置信度高于指定阈值的规则。

- 示例 (PPT, Page 43):

  - 规则：If insured A AND police officer X => auto repair shop 1
  - X = {insured A, police officer X}
  - Support(X) = 4/10 (出现 ID#1,2,6,9)
  - Y = {auto repair shop 1}
  - Support(X ∪ Y) = 3/10 (出现 ID#1,6,9)
  - Confidence(X ⇒ Y) = 3/4 = 75%

## 第十章

社会网络分析在欺诈检测中的应用 (Social Network Analysis for Fraud Detection)

### 基本概念 (Basic Concepts)

- **社会网络分析 (Social Network Analysis, SNA)**：SNA 是一种用于研究社会结构及其影响的工具和方法。它关注实体（如人、组织、机器等）之间的关系及其形成的模式。（来源：PPT第2页）

### 为什么需要研究社会网络？ (Why do we need to study social network?)

- 关联犯罪 (Guilt-by-association)

  - 这个概念假设一个人因为与犯罪分子或与犯罪相关的事物有联系，而被认为有罪。
  - “物以类聚” (Birds of same feathers flock together) 是其核心思想。
  - 例如，如果 Tom 的好朋友是罪犯，那么 Tom 很有可能也参与了相同或类似的犯罪活动。（来源：PPT第4页）

### 背景知识 (Some Background)

- 旅行推销员问题 (Traveling Salesman Problem, TSP)

  - 该问题旨在找出连接所有给定地点，且总距离最短的路径。
  - 数学家 Karl Menger 在1930年发现了 TSP。
  - 这是一个在现实生活中仍然难以解决的网络问题。（来源：PPT第5页）

### 图论 (Graph Theory)

- 图 (Graph)

  - 在数学中，一个图是由一组顶点 (Vertices) 和连接这些顶点的边 (Edges) 组成的结构。

  - 在社会网络分析中，顶点通常代表个体或实体，边则代表他们之间的关系。（来源：PPT第6页）

- **节点/顶点 (Nodes/Vertices)**：图中的基本元素，可以代表个体、组织、事件等。

- **边/链接 (Edges/Links)**：连接图中两个节点的关系。边可以是有方向的 (Directed) 或无方向的 (Undirected)。

### 社会网络分析基础 (Social Network Analysis Basics)

- 社会网络 (Social Network)

  - 由一组实体（如人、组织、机器等）和它们之间的关系组成的结构。

  - 在欺诈检测中，这些实体可以是个人、银行账户、电话号码、IP 地址等，关系可以是交易、电话通话、共享地址等。（来源：PPT第7页）

- **节点 (Nodes)**：网络中的实体。

- **边 (Edges)**：节点之间的关系。

### 图的表示 (Graph Representation)

- 邻接矩阵 (Adjacency Matrix)

  - 一种用矩阵来表示图的方法，其中矩阵的行和列都代表图中的节点。
  - 矩阵中的元素 Aij 表示节点 i 和节点 j 之间是否存在边（或边的权重）。
  - 如果 Aij=1，表示节点 i 和节点 j 之间有边；如果 Aij=0，则没有边。
  - 对于无向图，邻接矩阵是对称的，即 Aij=Aji。
  - 对于有向图，邻接矩阵可能不对称。（来源：PPT第8-9页）
  
- 邻接列表 (Adjacency List)

  - 一种用列表来表示图的方法，其中每个节点都有一个列表，包含其所有邻居节点。
- 这种表示方法通常在图比较稀疏（边数相对较少）时更高效。（来源：PPT第10页）

### 网络属性 (Network Attributes)

- 网络密度 (Network Density)

  - 网络密度是衡量网络中连接紧密程度的指标。
  - 它计算了网络中实际存在的边数与所有可能存在的边数之间的比率。
  - 对于无向图，可能存在的最大边数为 N(N−1)/2，其中 N 是节点数。
  - 密度值介于 0 到 1 之间，1 表示所有节点之间都有连接（完全图），0 表示没有连接。（来源：PPT第11页）
  - 公式：Density=N(N−1)/2E，其中 E 是实际边数，N 是节点数。（来源：PPT第12页）
  
- 度 (Degree)

  - 节点的度是指与该节点相连的边的数量。
  - 在无向图中，度就是直接连接到该节点的边的数量。
  - 在有向图中，有入度 (In-degree) 和出度 (Out-degree)：
    - **入度 (In-degree)**：指向该节点的边的数量。
    - **出度 (Out-degree)**：从该节点发出的边的数量。（来源：PPT第13页）
  - 在社会网络中，度可以表示一个人的影响力或活跃度。（来源：PPT第14页）
  
- 中心性 (Centrality)

  - 中心性指标用于衡量网络中节点的重要性。

  - 度中心性 (Degree Centrality)

    - 直接衡量一个节点连接的边的数量。度高的节点通常被认为是更重要的节点。
  - 标准化度中心性：除以可能的最大度数，使不同规模的网络之间可以比较。
    - 公式：Normalized_Degree_Centrality=N−1Degree(Node)，其中 N 是节点数。（来源：PPT第15页）
  
  - 紧密中心性 (Closeness Centrality
  
    - 衡量一个节点与网络中其他所有节点的距离（最短路径长度）的倒数。
  - 紧密中心性高的节点通常能更快地将信息传播到整个网络。（来源：PPT第16页）
    - 公式：Closeness_Centrality(Node)=∑j=id(i,j)N−1，其中 d(i,j) 是节点 i 和节点 j 之间的最短路径长度，N 是节点数。（来源：PPT第17页）
  
  - 中介中心性 (Betweenness Centrality)

    - 衡量一个节点在网络中充当“桥梁”或“中间人”的程度。
    - 中介中心性高的节点在网络中具有重要的控制作用，因为它们处于许多最短路径上。
    - 公式：Betweenness_Centrality(Node)=∑s=v=tσstσst(v)，其中 σst 是从节点 s 到节点 t 的最短路径总数，σst(v) 是通过节点 v 的最短路径数量。（来源：PPT第18页）
  
  - 特征向量中心性 (Eigenvector Centrality)

    - 衡量一个节点的影响力不仅取决于其连接的数量，还取决于其连接的节点的影响力。
- 连接到高影响力节点的节点具有更高的特征向量中心性。（来源：PPT第19页）

### 欺诈检测中的社会网络分析 (Social Network Analysis in Fraud Detection)

- 欺诈类型 (Types of Fraud)

  - **孤立欺诈 (Isolated fraud)**：个人或少数人独自进行的欺诈活动，通常不涉及复杂的网络结构。
  - **合谋欺诈 (Collusive fraud)**：多个人通过合谋或协作进行的欺诈活动，通常形成复杂的欺诈网络。（来源：PPT第20页）
  
- SNA在欺诈检测中的应用 (SNA application in fraud detection)

  - 识别隐藏的欺诈模式。
  - 揭示欺诈团伙之间的关系。
  - 发现异常行为。
  - 评估风险。（来源：PPT第20页）
  
- 欺诈场景 (Fraud Scenarios)

  - **保险欺诈 (Insurance Fraud)**：例如，多个“受害者”在同一事故中索赔，或者不同的医生为同一病人开出相同的诊断和治疗方案。（来源：PPT第21-22页）
  - **信用卡欺诈 (Credit Card Fraud)**：例如，通过网络发现欺诈团伙，或者识别出共享相同特征的欺诈交易。（来源：PPT第23-24页）
  - **电信欺诈 (Telecommunications Fraud)**：例如，识别出具有异常通话模式的电话号码，或者通过电话网络发现欺诈团伙。（来源：PPT第25页）
  - **洗钱 (Money Laundering)**：通过识别可疑的资金流向和交易网络来检测洗钱活动。（来源：PPT第26页）

### 欺诈分析的步骤 (Steps for Fraud Analytics)

- 理解业务背景和现有系统 (Understanding the Business Context and Existing Systems)

  - 深入了解业务流程，识别欺诈的潜在点。
  - 分析现有欺诈检测系统的优缺点。（来源：PPT第28页）
  
- 数据理解和准备 (Data Understanding and Preparation)

  - 收集、清洗、整合数据。
  - 特征工程 (Feature Engineering)：从原始数据中提取有用的特征。（来源：PPT第29页）
  
- 欺诈分析技术 (Fraud Analytics Techniques)

  - **描述性分析 (Descriptive Analytics)**：通过汇总和可视化数据来理解欺诈的特征和模式。
  - **预测性分析 (Predictive Analytics)**：构建模型来预测未来的欺诈行为。
  - **规定性分析 (Prescriptive Analytics)**：提供建议，指导如何应对欺诈行为。（来源：PPT第30页）
  
- 模型部署、监控和评估 (Model Deployment, Monitoring, and Evaluation)

  - 将模型集成到实际系统中。
  - 持续监控模型的性能。
  - 定期评估模型的有效性并进行调整。（来源：PPT第31页）

### 欺诈数据分析方法 (Fraud Data Analytics Methodology)

- 欺诈情景法 (Fraud Scenario Approach)

  - 识别可能的欺诈情景，并为每个情景开发检测规则或模型。
  - 这种方法侧重于具体欺诈类型的检测。（来源：PPT第32页）
  
- **迭代和适应性 (Iterative and Adaptive)**：欺诈检测是一个持续的过程，需要不断地调整和改进模型。（来源：PPT第33页）

### 监督式欺诈检测模型 (Supervised Fraud Detection Models)

- 监督式学习 (Supervised Learning)

  - 使用带有标签（已知欺诈或非欺诈）的数据集来训练模型。
  - 模型学习输入特征与输出标签之间的映射关系。（来源：PPT第34页）
  
- 模型选择 (Model Selection)

  - 选择适合特定欺诈检测任务的机器学习模型。
  - 常见的模型包括逻辑回归、决策树、支持向量机、神经网络等。（来源：PPT第34页）
  
- 模型评估 (Model Evaluation)

  - 使用各种指标来评估模型的性能。

  - 混淆矩阵 (Confusion Matrix)

    - 用于展示分类模型性能的表格。
  - **真阳性 (True Positives, TP)**：实际是欺诈，模型预测为欺诈。
    - **真阴性 (True Negatives, TN)**：实际不是欺诈，模型预测为非欺诈。
  - **假阳性 (False Positives, FP)**：实际不是欺诈，模型预测为欺诈（I类错误）。
    - **假阴性 (False Negatives, FN)**：实际是欺诈，模型预测为非欺诈（II类错误）。（来源：PPT第35-36页）
    
  - 准确率 (Accuracy)
  
    ：

    - 所有正确预测的样本占总样本的比例。
  - 公式：Accuracy=TP+TN+FP+FNTP+TN
    - 在欺诈检测中，由于欺诈样本通常很少，准确率可能不是最好的指标。（来源：PPT第37页）

  - 精确率 (Precision)
  
    - 在所有被模型预测为欺诈的样本中，实际是欺诈的比例。
  - 衡量模型识别欺诈的准确性，减少误报。
    - 公式：Precision=TP+FPTP（来源：PPT第38页）
  
  - 召回率 (Recall) / 敏感度 (Sensitivity) / 真阳性率 (True Positive Rate, TPR)

    - 在所有实际是欺诈的样本中，被模型正确识别出来的比例。
    - 衡量模型发现欺诈的能力，减少漏报。
    - 公式：Recall=TP+FNTP（来源：PPT第39页）
  
  - F1分数 (F1-score)

    - 精确率和召回率的调和平均值。
  - 综合考虑了精确率和召回率，尤其在类别不平衡的数据集中非常有用。
    - 公式：F1=2×Precision+RecallPrecision×Recall（来源：PPT第40页）
    
  - ROC曲线 (Receiver Operating Characteristic Curve)

    - 绘制了真阳性率 (TPR) 和假阳性率 (False Positive Rate, FPR) 在不同分类阈值下的关系。
  - **假阳性率 (FPR)**：所有实际不是欺诈的样本中，被模型错误预测为欺诈的比例。
    - 公式：FPR=FP+TNFP
  - 曲线越靠近左上角，模型性能越好。（来源：PPT第41-42页）
  
  - AUC (Area Under the Curve)
  
  - ROC曲线下的面积。
    - AUC值越大，模型性能越好。
  - AUC为1表示完美分类器，AUC为0.5表示随机分类器。（来源：PPT第43页）
    
  - KS统计量 (Kolmogorov-Smirnov Statistic)
  
    - 衡量好客户和坏客户累计分布之间最大距离的指标。
  - KS值越大，模型区分好坏客户的能力越强。（来源：PPT第44-45页）
  
- 升力图 (Lift Chart)
  
  - 衡量模型相对于随机猜测的提升效果。
    - 通过比较模型在识别目标事件（如欺诈）方面的能力与随机选择的能力来评估模型的有效性。（来源：PPT第46-47页）
  
  - 增益图 (Gain Chart)

    - 显示了随着考虑更多样本，模型识别目标事件的比例。
  - 通常用于评估模型在不同召回率水平下的表现。（来源：PPT第48-49页）

### 非监督式欺诈检测模型 (Unsupervised Fraud Detection Models)

- 非监督式学习 (Unsupervised Learning)

  - 不对数据进行标签，而是通过发现数据中的内在模式和结构来进行学习。
  - 常用于异常检测 (Anomaly Detection)，即识别与大多数数据模式不符的异常点。（来源：PPT第50页）
  
- 异常检测 (Anomaly Detection)

  - 识别数据中不符合预期行为模式的离群点。
  - 在欺诈检测中，欺诈行为通常是异常的，因此异常检测模型可以有效地发现它们。（来源：PPT第51页）
  
- 非监督式学习算法 (Unsupervised Learning Algorithms)

  - 聚类 (Clustering)

    - 将数据点分组，使同一组内的点相似，不同组间的点不相似。
  - 异常点可能不属于任何现有簇，或者形成非常小的簇。（来源：PPT第52页）
    - **k-Means**：一种流行的聚类算法，将数据点分配到最近的k个中心点所在的簇。（来源：PPT第53页）
  
  - 离群点分析 (Outlier Analysis)
  
    - 专门用于识别数据中的异常点。
- **LOF (Local Outlier Factor)**：基于密度的局部异常因子算法。它衡量一个数据点相对于其邻居的局部密度。局部密度显著低于其邻居的数据点被认为是异常点。（来源：PPT第54页）

### 其他欺诈检测技术 (Other Fraud Detection Techniques)

- 规则引擎 (Rule Engines)

  - 基于预定义的业务规则来识别欺诈。
  - 优点是易于理解和解释，但缺点是难以适应新的欺诈模式，且规则维护成本高。（来源：PPT第55页）
  
- 生成式AI在金融欺诈检测中的作用 (Generative AI’s Role in Financial Fraud Detection)

  - 生成式AI可以用于合成欺诈数据，以扩充数据集，解决欺诈样本稀少的问题。
  - 也可以用于生成对抗性样本，帮助测试和增强欺诈检测模型的鲁棒性。
  - 还可以通过学习正常的金融交易模式，生成“正常”交易数据，从而更好地识别异常模式。（来源：PPT第56页）

### 模型可解释性 (Model Explainability)

- 可解释性 (Explainability)

  - 模型可解释性是指理解模型如何做出预测或决策的能力。
  - 在欺诈检测中，可解释性尤为重要，因为这有助于调查人员理解欺诈的机制，并采取相应的措施。（来源：PPT第57页）
  
- “黑箱”模型 (“Black Box” Models)

  - 指那些内部工作机制复杂，难以理解其决策过程的模型，例如深度学习模型。（来源：PPT第58页）

- 可解释性技术 (Explainability Techniques)

  - LIME (Local Interpretable Model-agnostic Explanations)

    - 局部解释，通过对输入样本进行微扰，观察模型预测的变化，从而解释单个预测。
  - 与模型无关 (Model-agnostic)，可以用于解释任何机器学习模型。（来源：PPT第59页）
  
- SHAP (SHapley Additive exPlanations)
  
    - 基于博弈论，计算每个特征对模型预测的贡献。
- 提供全局和局部解释。（来源：PPT第60页）

### 模型评估指标回顾 (Recap of Model Evaluation Metrics)

- 准确率 (Accuracy)

  - 适用于平衡数据集。
  - 在欺诈检测中，由于类别不平衡，可能导致误导性结果。（来源：PPT第62页）
  
- 精确率 (Precision)

  - 关注模型预测为正例（欺诈）的样本中有多少是真正的正例。
  - 在高召回率的情况下，可以通过降低精确率来增加召回率。（来源：PPT第63页）
  
- 召回率 (Recall)

  - 关注所有真正的正例中有多少被模型正确识别。
  - 在高精确率的情况下，可以通过降低召回率来增加精确率。（来源：PPT第64页）
  
- F1分数 (F1-score)

  - 精确率和召回率的调和平均值，在不平衡数据集上表现良好。（来源：PPT第65页）

- AUC-ROC (Area Under the Receiver Operating Characteristic Curve)

  - 衡量模型在不同分类阈值下的区分能力。
  - 对不平衡数据集不敏感，是评估欺诈检测模型的重要指标。（来源：PPT第66页）
  
- 平均精确率 (Average Precision, AP)

  - 通常用于评估在不平衡数据集上模型的性能，特别是在信息检索和目标检测等领域。
  - 是精确率-召回率曲线下的面积。（来源：PPT第67页）
  
- R-squared (R2) / 决定系数 (Coefficient of Determination)

  - 用于回归模型，表示输入变量解释输出变量变异的程度。
  - R2 越高，模型对输出变量的解释能力越强。
  - 公式：R2=1−SStotSSres，其中 SSres 是残差平方和，SStot 是总平方和。
  - R2 可以帮助我们比较当前模型与基线值（例如均值）的优劣。（来源：PPT第73-74页）
