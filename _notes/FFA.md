# FFA 中文版

## 第一章

由于内容较多，我将分块进行详细阐述。

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

### 支持向量机概述 (Support Vector Machine) [第4页]

支持向量机是一种**监督学习模型 (supervised learning model)**，既可用于分类 (classification) 也可用于回归 (regression)，但更常用于二分类问题。基本思想是寻找一个**超平面 (hyperplane)**，最大化两类之间的**间隔 (margin)**，以最佳地将数据分开。

### 决策边界与最大化间隔 (Decision Boundary & Maximal Margin) [第5–7页]

- **决策边界 (decision boundary)**：一维为点 (dot)，二维为直线 (line)，多维为超平面。
- **支持向量 (support vectors)**：最靠近超平面的训练样本。
- **间隔 (margin)**：支持向量到超平面的距离，SVM通过优化求解使间隔最大。

### 线性不可分与松弛变量 (Linear Non-separable & Slack Variables) [第8页]

当两类数据重叠时，引入**误差项 (error term, εₖ)**，允许少量误分类，并用正则化参数**C**在“最大化间隔 (maximize margin)”与“最小化误差 (minimize error)”之间权衡。

### 非线性分类与核技巧 (Non-linear Classification & Kernel Trick) [第9–10页]

- 将数据映射到更高维特征空间（mapping function ϕ(x)）以实现线性可分。
- **核函数 (kernel function)** 直接在原空间计算点积，避免显式映射，常见的有线性 (linear)、多项式 (polynomial)、径向基函数(RBF) 等。

### 超参数调优 (Hyperparameter Tuning) [第11–14页]

- **Gamma (γ)**：决定单个训练样本影响范围，γ低→松散拟合，γ高→紧密拟合。
- **Regularization C**：C小→允许更多违规、更大间隔；C大→强调少误分类、更紧间隔。
- 调优流程：按40%/30%/30%划分训练/验证/测试集，网格搜索(γ,C)，选验证集最佳组合，再在训练+验证集上重训并测试。

### SVM优缺点 (SVM Advantages & Disadvantages) [第16页]

**优点**：在高维空间中表现良好，仅依赖支持向量，内存高效；
 **缺点**：对大规模及高噪声数据效果差，核函数选择与调优计算量大。

### One-Class SVM 概述 (One-Class SVM: Anomaly Detection with a Single Class) [第19–21页]

- 只以“正常类 (normal class)”数据训练，用于异常检测 (anomaly detection)。
- 构造一个包围大多数正常点的超平面，落在外部的新样本视为异常 (anomaly)。
- 常用RBF核以创建非线性边界。

### One-Class SVM 优缺点 (Advantages & Disadvantages) [第23页]

**优点**：仅需正常样本，无需负样本；对训练数据异常值不敏感；可处理高维数据。
 **缺点**：参数选择（核及其参数）敏感；对互异新型异常检测能力有限；决策边界难解释。

### One-Class SVM 在R中的应用示例 (One-Class SVM in R) [第24–25页]

在R中可通过指定`one-classification`和`RBF`核对数据集（通常选2个变量）进行训练与预测。

### 性能评估指标回顾 (Revision of Performance Metrics) [第28–29页]

- **TP, TN, FP, FN**：混淆矩阵基本构件。
- **True Positive Rate (TPR/Recall)** = TP/(TP+FN)。
- **False Positive Rate (FPR)** = FP/(FP+TN)。
- **Precision** = TP/(TP+FP)。
- **F1 Score** = 2·Precision·Recall/(Precision+Recall)。
- **AUC (Area Under ROC Curve)**：衡量分类器在不同阈值下区分能力。

### ROC与PR曲线 (ROC Curve & Precision-Recall Curve) [第30–34页]

- **ROC曲线**：绘制TPR对FPR；AUC越接近1，分类性能越好。
- **PR曲线**：绘制Precision对Recall；在类别不平衡时更具判别力。
- 对比：ROC对不平衡敏感度低，PR对不平衡更敏感。

### 本福特定律 (Benford’s Law) [第36–40页]

- 自然数值分布的首位数字频率遵循对数衰减：Pr(D₁=d)=log₁₀(1+1/d)，d∈1…9。
- 数字1出现频率最高 (~30％)，数字9最低 (~4.6％)。

### 本福特定律的历史与应用条件 (History & Conditions) [第41–43页]

- Newcomb (1881)与Benford (1938)观察到这一现象。
- 适用数据：无固定上下限、非标识符、分布范围宽、均值小于中位数。

### 本福特定律在欺诈检测中的作用 (Fraud Detection via Benford’s Law) [第44–46页]

- 真实财务或交易数据应符合本福特定律，伪造数据往往出现偏离。
- 仅作“红旗 (red flag)”提示，需结合其他分析验证。

### 拟合检验：卡方检验 (Chi-square Goodness-of-Fit Test) [第47–50页]

1. 自由度 df = 9–1 = 8。
2. 计算每位数字的期望频次 Ei = n·pi。
3. 统计量 χ² = Σ(Oi–Ei)²/Ei。
4. 查表 p-value；若p<0.05，拒绝符合假设。

### 案例：2016美国选举数据 (2016 US Election Example) [第51–55页]

- 分析伊利诺伊州按县投票，结果χ²<临界值，未拒绝符合本福特定律。
- 可演示如何“欺骗”本福特定律保持拟合同时篡改结果。

### 欺诈检测方法学回顾 (Fraud Analytics Methodology) [第63–65页]

包含范围定义 (scope)、场景识别 (scenario identification)、数据分析策略 (data analytics strategies) 及模型选择 (model selection)，强调循环迭代而非线性流程。

### 洗钱案例：背景与数据 (Money Laundering Case Background & Data) [第70–72页]

- 西班牙法院真实案例，核心公司与643供应商间285,774次交易，仅26家已知欺诈。
- 变量包括商品、地点、记录者、成本、数量、日期、供应商ID、交易金额等。

### 洗钱过程三阶段 (Money Laundering Stages) [第75页]

1. **投放 (Placement)**：分拆大额存款 (smurfing) 以规避报告限额。
2. **分层 (Layering)**：跨境、多次中间交易掩盖资金来源。
3. **整合 (Integration)**：将“洗净”资金重新投入合法经济，如房产销售、离岸贷款等。

### 数据分析测试点 (Data Analytical Tests) [第78页]

可检查损益表、资产负债表、销售及资产登记等，并用本福特测试、异常值检测等方法寻找洗钱痕迹。

## 第十章

### 社会网络分析在欺诈检测中的应用 (PPT 第1页)

- **Social Network Analysis for Fraud Detection**
   本讲介绍如何利用社会网络分析（Social Network Analysis）技术，挖掘网络中节点与节点之间的关系，以发现和预测潜在的欺诈行为。

### 为什么要研究社会网络？ (PPT 第4页) 

- **Guilt-by-association（关联定罪假设）**
   假设一个人因其与已知犯罪分子的关联而更可能参与犯罪。“Birds of same feathers flock together”（物以类聚）体现了同类节点倾向于形成团体。
- **实际例子**
   如果 Tom 的好友大多是犯罪分子，则 Tom 涉案风险显著增高。

### 背景知识：旅行商问题与“小世界”现象 (PPT 第5–6页) 

- **Traveling Salesman Problem (TSP)**
   1930 年 Karl Menger 提出，寻找一条最短路径，需要经过一系列指定的“站点”。该问题在现实网络中仍属 NP-hard。
- **Six Degrees of Separation（六度分隔）**
   Milgram（1967）实验表明，现实人际网络的平均最短路径长度约为 6；在线社交网络（Kwak et al., 2010）平均约为 4 hops，但关系强度各异。

### 应用场景 (PPT 第7页) 

- **保险欺诈**：同一目击者或理赔人出现于多笔可疑理赔中。
- **公司破产**：同一股东或雇员频繁关联的公司破产。
- **舆论欺诈**：针对某产品/公司的虚假在线评论。
- **价值**：社会网络分析能捕捉传统模型难以识别的关系模式。

### 基本概念 — 网络组件 (PPT 第8–12页) 

- **Complex Network Analysis（复杂网络分析）**：研究网络结构、特性与动态变化。

- **Graph Theory（图论）**：用数学图（graph）来建模网络，G = (V, E)，其中 V 是节点集（vertices），E 是边集（edges）。

- **Directed vs. Undirected Graph**

  - Directed graph（有向图）：边有方向性。
  - Undirected graph（无向图）：边无方向。

- **Self-edge（自环）**：节点自身的连接，例如同一人账户间转账。

- **Multi-edge（多重边）**：两节点间多条并行边，例如多次交易产生多重连接。

- **Hyper-edge（超边）**：同时连接多个节点，例如多人共同参加同一活动。

- **Weighted Graph（加权图）**：边具有强度或权重

  - Binary weight（二元权重）：{0,1} 或 {-1,0,1}。
  - Numeric weight（数值权重）：可表示共同事件次数或消息数量。
  - Normalized weight（归一化权重）：一个节点所有出边权重和为 1。

- **Jaccard Weight（雅卡尔德权重）** (Gupte & Eliassi-Rad 2012)：

  wij=∣Ai∩Aj∣∣Ai∪Aj∣  w_{ij} = \frac{|A_i \cap A_j|}{|A_i \cup A_j|}  wij=∣Ai∪Aj∣∣Ai∩Aj∣

  例如 A 参加 10 场活动，B 参加 5 场，两者共同参加 3 场，则 Jaccard = 3/(10+5−3)=1/4。

### 欺诈节点与Egonet (PPT 第12页) 

- **Fraudulent vs. Legitimate Nodes（欺诈/合法节点）**
   根据历史记录将节点标记为“Fraud”（欺诈）或“Legitimate”（合法）。
- **Edge Weight 表征社交强度**：与多位已标记欺诈节点相连时，节点被标为欺诈的概率更高。
- **Egonet（节点自我网络）**：一个节点及其一阶邻居构成的子网络；在欺诈分析中通常只需一跳。

### 网络表示方法 (PPT 第13–15页) 

- **Adjacency Matrix（邻接矩阵）**
   n×n 矩阵 A，若节点 i 与 j 存在连边则 a_{ij} = 1，否则 0；稀疏矩阵对应真实社交网络的低连通度。
- **Adjacency List（邻接表）**：对邻接矩阵的抽象列表表示。
- **Weight Matrix（权重矩阵）**
   若 i-j 连边则 w_{ij}=权重，否则 0。
- **Weight List（权重表）**：对权重矩阵的列表形式表示。

1. ### 邻居度量详解 — Degree Metrics (PPT 第16页) 

   - **Degree（度）**：节点的邻居数，即 node’s degree。对于有向图，区分 in-degree（入度）和 out-degree（出度）。
   - **Triangles（三角数）**：与该节点形成三角形的连接数，用于衡量局部聚集性（local clustering）。
   - **Density（密度）**：Egonet 中实际存在的边数量与可能存在的最大边数量之比（density = 2×|E|/[k×(k−1)]，k 为邻居数）。
   - **Relational Neighbor（关联邻居）**：计算节点与其邻居在属性空间（attribute space）中的相似度加权总和。
   - **Probabilistic Relational Neighbor（概率关联邻居）**：在关联邻居基础上，进一步将相似度归一化为概率分布，以减少高度相似节点对结果的过度影响。

   ### 中心性度量 — Centrality Metrics (PPT 第17页) 

   - **Closeness Centrality（接近中心性）**：节点到所有其他节点最短路径长度之和的倒数，表征节点的传播效率。
   - **Betweenness Centrality（中介中心性）**：所有最短路径中经过该节点的比例，衡量节点在网络信息流中的桥梁作用。
   - **Eigenvector Centrality（特征向量中心性）**：节点与高中心性邻居相连的程度更高时，其自身中心性也更高，基于 adjacency matrix 的特征向量计算。
   - **PageRank（网页排名算法）**：随机游走模型（random walk），节点分数受其入边节点分数累积影响，并加入阻尼因子（damping factor）。

   ### 集体推断算法 — Collective Inference (PPT 第18页) 

   - **Iterative Classification（迭代分类）**：通过初始分类器预测节点标签，然后将预测结果作为新特征反馈，迭代更新直至收敛。
   - **Loopy Belief Propagation（循环置信传播）**：在有环图（loopy graph）上运行的 Belief Propagation，通过消息传递（message passing）估计节点标签的边际概率。
   - **Gibbs Sampling（吉布斯抽样）**：一种 MCMC 方法（Markov Chain Monte Carlo），通过随机采样逐步逼近节点标签的联合分布。
   - **Relaxation Labelling（松弛标注）**：初始化标签概率后，通过最优化能量函数（energy function）迭代调整标签概率，使整体一致性最大化。

   ### 特征化 — Featurization (PPT 第19页) 

   - **Node Attribute Features（节点属性特征）**：基于节点自身属性（如账户余额、注册时间）。
   - **Structural Features（结构特征）**：基于网络度量（如 degree、clustering coefficient）。
   - **Relational Features（关系特征）**：基于邻居标签分布（如 fraud neighbor ratio）。
   - **Graph Embedding（图嵌入）**：使用 DeepWalk、node2vec 等算法，将节点映射到低维向量空间以捕捉网络结构。

   ### 二部图模型 — Bipartite Graph (PPT 第20页) 

   - **定义**：节点分为两类（如 用户-商品），只有不同类别节点间存在边；用 G = (U, V, E) 表示。
   - **应用**：分析共现关系（co-occurrence），如多个用户购买同一商品可能构成欺诈团伙。
   - **投影图（Projection）**：将二部图投影为单一类别节点的加权图，例如用户-用户投影，根据共同购买次数设置 weight。

   ### 案例研究 — Tax Fraud Detection (PPT 第21–22页) 

   - **数据集**：税务局提供的申报记录与关联账户网络。
   - **流程**：
     1. 构建网络（Construct Graph）：节点为纳税人，边为资金流向。
     2. 特征提取（Extract Features）：计算 degree、eigenvector centrality、fraud neighbor ratio 等。
     3. 模型训练（Train Classifier）：使用随机森林（Random Forest）或 GCN。
     4. 结果评估（Evaluate）：ROC-AUC、Precision-Recall 曲线。
   - **结果**：利用网络特征的模型相比仅使用传统财务特征，欺诈检测率提升约 15%。