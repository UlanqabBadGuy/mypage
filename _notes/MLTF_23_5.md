# COMP7409 机器学习在交易与金融中的应用 - 考试答案  
# COMP7409 Machine Learning in Trading and Finance - Exam Answers  

---

## 问题1: 欺诈检测系统设计  
## Question 1: Fraud Detection System Design  

### 1. 数据清洗与预处理  
### 1. Data Cleaning and Preprocessing  

- 处理缺失值（标记为"."）：  
- Handle missing values (marked with "."):  
```python  
import pandas as pd  
df = pd.read_csv('tranrecords.cvs', na_values=['.'])  
```
- 检查并删除重复值  
- Check for and remove duplicates  
- 转换数据类型（如将财年转换为整数，月份转换为分类变量）  
- Convert data types (e.g., Fiscal Year to integer, Month to categorical)  
- 处理缺失值：  
- Handle missing values by either:  
  - 删除含缺失值的行（如果数量少）  
  - Dropping rows with missing values (if few)  
  - 填充（如用均值/中位数填充Amount，用众数填充分类变量）  
  - Imputing (e.g., mean/median for Amount, mode for categorical variables)  

### 2. 探索性数据分析（EDA）  
### 2. Exploratory Data Analysis (EDA)  

- 检查目标变量（RedFlag）的分布  
- Check distribution of target variable (RedFlag)  
- 分析其他变量的分布  
- Analyze distributions of other variables  
- 检查特征间的相关性  
- Check for correlations between features  
- 可视化关系（如按RedFlag分组的Amount箱线图）  
- Visualize relationships (boxplots of Amount by RedFlag, etc.)  
- 特征重要性分析  
- Feature importance analysis  

### 3. 特征工程  
### 3. Feature Engineering  

- 创建新特征（如各部门的交易频率）  
- Create new features if helpful (e.g., transaction frequency per department)  
- 编码分类变量（Department, Month, Status）使用独热编码  
- Encode categorical variables (Department, Month, Status) using one-hot encoding  
- 标准化数值特征（Amount）  
- Normalize numerical features (Amount)  
- 处理类别不平衡（RedFlag=1可能较少）  
- Handle class imbalance if present (RedFlag=1 likely rare)  

### 4. 模型选择与训练  
### 4. Model Selection and Training  

- 将数据分为训练集和测试集（如80-20）  
- Split data into training and testing sets (e.g., 80-20)  
- 考虑适合分类的模型：  
- Consider models suitable for classification:  
  - 逻辑回归（基线模型）  
  - Logistic Regression (baseline)  
  - 随机森林（处理非线性关系效果好）  
  - Random Forest (handles non-linearity well)  
  - 梯度提升（XGBoost，适合不平衡数据）  
  - Gradient Boosting (XGBoost, good for imbalanced data)  
  - 神经网络（如果数据量足够大）  
  - Neural Networks (if data is large enough)  

示例代码（随机森林）：  
Example code for Random Forest:  
```python  
from sklearn.ensemble import RandomForestClassifier  
from sklearn.model_selection import train_test_split  

X = df.drop('RedFlag', axis=1)  
y = df['RedFlag']  
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)  

model = RandomForestClassifier(class_weight='balanced')  
model.fit(X_train, y_train)  
```

### 5. 模型评估  
### 5. Evaluation  

- 使用适合不平衡数据的评估指标：  
- Use appropriate metrics for imbalanced data:  
  - 精确率、召回率、F1分数  
  - Precision, Recall, F1-score  
  - ROC-AUC  
  - 混淆矩阵  
  - Confusion matrix  
- 通过交叉验证调整超参数  
- Tune hyperparameters using cross-validation  
- 考虑误报和漏报的业务成本  
- Consider business costs of false positives vs false negatives  

### 6. 部署考虑  
### 6. Deployment Considerations  

- 模型可解释性（SHAP/LIME值）  
- Model interpretability (SHAP/LIME values)  
- 监控概念漂移  
- Monitoring for concept drift  
- 定期重新训练计划  
- Regular retraining schedule  

---

## 问题2  
## Question 2  

### (a) 最大乘积子序列  
### (a) Maximum Product Subsequence  

为了高效计算所有j的f(j)，我们可以使用动态规划，通过维护每个位置结束的最大和最小乘积（因为负数乘以另一个负数可以使小乘积变大）。  
To efficiently compute f(j) for all j, we can use dynamic programming by maintaining the maximum and minimum product ending at each position (since a negative number can make a small product large when multiplied by another negative number).  

Python实现：  
Python implementation:  
```python  
def max_product_subsequence(arr):  
    if not arr:  
        return []  
      
    n = len(arr)  
    max_prod = min_prod = arr[0]  
    result = [arr[0]]  
      
    for i in range(1, n):  
        curr = arr[i]  
        candidates = (curr, max_prod * curr, min_prod * curr)  
        max_prod, min_prod = max(candidates), min(candidates)  
        result.append(max_prod)  
      
    return result  
```

### (b) 使用Q-learning改进CartPole游戏  
### (b) Q-learning for CartPole  

使用Q-learning改进的版本：  
Improved version using Q-learning:  
```python  
import numpy as np  
import gym  

env = gym.make('CartPole-v0')  

# Q-learning参数  
# Q-learning parameters  
learning_rate = 0.1  
discount = 0.95  
episodes = 1000  
epsilon = 1.0  
epsilon_decay = 0.995  

# 离散化状态空间  
# Discretize state space  
bins = 10  
q_table = np.zeros((bins, bins, bins, bins, env.action_space.n))  

def discretize_state(state):  
    upper_bounds = [env.observation_space.high[0], 0.5, env.observation_space.high[2], math.radians(50)]  
    lower_bounds = [env.observation_space.low[0], -0.5, env.observation_space.low[2], -math.radians(50)]  
      
    ratios = [(state[i] + abs(lower_bounds[i])) / (upper_bounds[i] - lower_bounds[i]) for i in range(4)]  
    discretized = [int(round((bins - 1) * ratios[i])) for i in range(4)]  
    discretized = [min(bins-1, max(0, x)) for x in discretized]  
    return tuple(discretized)  

for episode in range(episodes):  
    state = discretize_state(env.reset())  
    done = False  
    steps = 0  
      
    while not done and steps < 200:  
        if np.random.random() < epsilon:  
            action = env.action_space.sample()  
        else:  
            action = np.argmax(q_table[state])  
          
        next_state, reward, done, _ = env.step(action)  
        next_state = discretize_state(next_state)  
          
        # Q-learning更新  
        # Q-learning update  
        current_q = q_table[state + (action,)]  
        max_next_q = np.max(q_table[next_state])  
        new_q = (1 - learning_rate) * current_q + learning_rate * (reward + discount * max_next_q)  
        q_table[state + (action,)] = new_q  
          
        state = next_state  
        steps += 1  
      
    epsilon *= epsilon_decay  

# 测试训练好的智能体  
# Test the trained agent  
state = discretize_state(env.reset())  
done = False  
steps = 0  

while not done and steps < 200:  
    action = np.argmax(q_table[state])  
    state, _, done, _ = env.step(action)  
    state = discretize_state(state)  
    steps += 1  
    env.render()  

print(f"Steps survived: {steps}")  
env.close()  
```

---

## 问题3  
## Question 3  

### (a) 神经网络输出  
### (a) Neural Network Output  

由于没有提供具体的权重和激活函数，一般方法是：  
Without specific weights and activation functions provided, a general approach would be:  
1. 计算每个节点的加权和  
1. Calculate weighted sum at each node  
2. 应用激活函数（可能是ReLU或sigmoid）  
2. Apply activation function (likely ReLU or sigmoid)  
3. 通过网络传播  
3. Propagate through network  
4. 最终输出是输出节点的加权和（可能带有激活函数）  
4. Final output would be the weighted sum at output node (possibly with activation)  

### (b) 协方差为零但相关的序列  
### (b) Zero Covariance but Related Sequences  

将序列补充为：  
Complete the sequences as:  
x = [-2, -1, 0, 1, 2]  
y = [x_i² for x_i in x] = [4, 1, 0, 1, 4]  

计算：  
Calculations:  
x̄ = (-2-1+0+1+2)/5 = 0  
ȳ = (4+1+0+1+4)/5 = 2  
协方差 = Σ(x_i - 0)(y_i - 2)/5  
Covariance = Σ(x_i - 0)(y_i - 2)/5  
= [(-2)(2) + (-1)(-1) + (0)(-2) + (1)(-1) + (2)(2)]/5  
= (-4 + 1 + 0 -1 + 4)/5 = 0/5 = 0  

但y完全由x决定（y = x²），表明协方差为零并不意味着没有关系。  
But y is perfectly determined by x (y = x²), showing that zero covariance doesn't imply no relationship.  

---

## 问题4: Twitter情感分析  
## Question 4: Twitter Sentiment Analysis  

```python  
import tweepy  # Twitter API客户端库
from datetime import datetime, timedelta  # 日期时间处理
from flair.models import TextClassifier  # 情感分析模型
from flair.data import Sentence  # 文本句子处理
import matplotlib.pyplot as plt  # 数据可视化
import math  # 数学运算

# ----------------------------
# 1. 初始化情感分析器
# ----------------------------
# 加载预训练的英文情感分析模型
# 该模型可以将文本分类为POSITIVE(积极)或NEGATIVE(消极)
# 并给出置信度分数(0-1之间)
print("正在加载情感分析模型...")
classifier = TextClassifier.load('en-sentiment')

# ----------------------------
# 2. 设置Twitter API认证
# ----------------------------
# 从文件中读取Twitter API的Bearer Token
# Bearer Token是访问Twitter API v2的认证凭证
print("正在读取Twitter认证令牌...")
try:
    with open('BearerToken.txt', 'r') as f:
        # 读取文件第一行并去除首尾空白字符
        bearer_token = f.readline().strip()
        if not bearer_token:
            raise ValueError("Bearer Token文件为空")
except FileNotFoundError:
    raise FileNotFoundError("找不到BearerToken.txt文件")

# 初始化Twitter客户端
# 使用tweepy库与Twitter API交互
client = tweepy.Client(bearer_token=bearer_token)

# ----------------------------
# 3. 设置分析日期范围
# ----------------------------
# 分析2023年5月7日到5月16日的数据
start_date = datetime(2023, 5, 7)  # 开始日期
end_date = datetime(2023, 5, 16)   # 结束日期

# 生成日期列表，包含开始和结束日期之间的所有日期
date_range = [
    start_date + timedelta(days=x) 
    for x in range((end_date - start_date).days + 1)
]

# ----------------------------
# 4. 初始化结果存储字典
# ----------------------------
# 使用字典存储每天的分析结果
# 结构: {日期: {'Lenovo': [分数列表], 'Dell': [分数列表]}}
results = {
    date.strftime('%Y-%m-%d'): {
        'Lenovo': [],  # 存储Lenovo相关推文的情感分数
        'Dell': []     # 存储Dell相关推文的情感分数
    } 
    for date in date_range
}

# ----------------------------
# 5. 获取并分析每天的推文
# ----------------------------
print("开始获取和分析推文数据...")
for date in date_range:
    current_date_str = date.strftime('%Y-%m-%d')
    print(f"\n正在处理 {current_date_str} 的数据...")
    
    # 设置查询时间范围（当天00:00到次日00:00）
    next_day = date + timedelta(days=1)
    
    # ----------------------------
    # 5.1 获取Lenovo相关推文
    # ----------------------------
    print("  获取Lenovo相关推文...")
    try:
        lenovo_tweets = client.search_all_tweets(
            query='Lenovo lang:en -is:retweet',  # 查询条件：英文、非转推
            start_time=date.isoformat() + 'T00:00:00Z',  # 开始时间
            end_time=next_day.isoformat() + 'T00:00:00Z',  # 结束时间
            max_results=100,  # 最大结果数
            tweet_fields=['text']  # 只获取文本内容
        )
        
        # 分析每条推文的情感
        if lenovo_tweets.data:
            for tweet in lenovo_tweets.data:
                # 创建Sentence对象用于情感分析
                sentence = Sentence(tweet.text)
                # 进行情感预测
                classifier.predict(sentence)
                # 获取预测结果
                label = sentence.labels[0]
                # 计算情感分数：积极分数为正，消极分数为负
                score = label.score if label.value == 'POSITIVE' else -label.score
                # 存储结果
                results[current_date_str]['Lenovo'].append(score)
            print(f"  分析完成，共处理 {len(lenovo_tweets.data)} 条Lenovo推文")
        else:
            print("  当天没有找到Lenovo相关推文")
    
    except Exception as e:
        print(f"  获取Lenovo推文时出错: {str(e)}")
    
    # ----------------------------
    # 5.2 获取Dell相关推文
    # ----------------------------
    print("  获取Dell相关推文...")
    try:
        dell_tweets = client.search_all_tweets(
            query='Dell lang:en -is:retweet',
            start_time=date.isoformat() + 'T00:00:00Z',
            end_time=next_day.isoformat() + 'T00:00:00Z',
            max_results=100,
            tweet_fields=['text']
        )
        
        # 分析每条推文的情感
        if dell_tweets.data:
            for tweet in dell_tweets.data:
                sentence = Sentence(tweet.text)
                classifier.predict(sentence)
                label = sentence.labels[0]
                score = label.score if label.value == 'POSITIVE' else -label.score
                results[current_date_str]['Dell'].append(score)
            print(f"  分析完成，共处理 {len(dell_tweets.data)} 条Dell推文")
        else:
            print("  当天没有找到Dell相关推文")
    
    except Exception as e:
        print(f"  获取Dell推文时出错: {str(e)}")

# ----------------------------
# 6. 计算每日平均情感分数
# ----------------------------
print("\n计算每日平均情感分数...")
dates = list(results.keys())  # 获取所有日期

# 计算Lenovo每日平均分数
# 如果当天没有推文，则分数设为0
lenovo_avg = [
    sum(scores)/len(scores) if scores else 0 
    for scores in [results[d]['Lenovo'] for d in dates]
]

# 计算Dell每日平均分数
dell_avg = [
    sum(scores)/len(scores) if scores else 0
    for scores in [results[d]['Dell'] for d in dates]
]

# ----------------------------
# 7. 可视化结果
# ----------------------------
print("生成可视化图表...")
plt.figure(figsize=(12, 6))  # 设置图表大小

# 绘制Lenovo情感分数折线图
plt.plot(
    dates, 
    lenovo_avg, 
    label='Lenovo', 
    marker='o', 
    color='blue', 
    linestyle='-',
    linewidth=2
)

# 绘制Dell情感分数折线图
plt.plot(
    dates,
    dell_avg,
    label='Dell',
    marker='s',
    color='green',
    linestyle='--',
    linewidth=2
)

# 设置图表标题和标签
plt.title('Lenovo vs Dell 每日平均情感分数比较 (2023年5月)', fontsize=14)
plt.xlabel('日期', fontsize=12)
plt.ylabel('平均情感分数', fontsize=12)
plt.legend(fontsize=12)  # 显示图例
plt.grid(True, linestyle=':', alpha=0.7)  # 添加网格线
plt.xticks(rotation=45, ha='right')  # 旋转x轴标签

# 调整布局防止标签被截断
plt.tight_layout()

# 保存图表到文件
plt.savefig('sentiment_comparison.png', dpi=300)
print("图表已保存为 sentiment_comparison.png")

# 显示图表
plt.show()

# ----------------------------
# 8. 打印详细结果
# ----------------------------
print("\n每日详细情感分数:")
print("日期\t\tLenovo平均分数\tDell平均分数\t差值(Lenovo-Dell)")
for i, d in enumerate(dates):
    diff = lenovo_avg[i] - dell_avg[i]
    print(f"{d}\t{lenovo_avg[i]:.3f}\t\t{dell_avg[i]:.3f}\t\t{diff:.3f}")

# 计算整体平均分数
overall_lenovo = sum(lenovo_avg)/len(lenovo_avg)
overall_dell = sum(dell_avg)/len(dell_avg)
print(f"\n整体平均分数:")
print(f"Lenovo: {overall_lenovo:.3f}")
print(f"Dell: {overall_dell:.3f}")
print(f"平均差值: {overall_lenovo - overall_dell:.3f}")

print("\n分析完成！")
```