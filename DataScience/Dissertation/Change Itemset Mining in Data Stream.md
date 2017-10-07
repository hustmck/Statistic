# Change Itemset Mining in Data Streams
>

> 数据流包含一个实例的有序序列，因为实例太多而计算和存储空间的限制，一次性（read only once）读取数据的算法备受推崇。

### 摘要
* 根据先前数据流中的实例，很多研究集中在发现什么时候目标变量（预测分析中，用模型来预测的目标变量的统计学属性）发生了不可预知的改变。但几乎没有研究确定这些改变的特性。
* 本文利用高频项集挖掘技术那些改变之特性。
* 结合启发式的和统计学上的方法，在数据流中项集层面分析这些变化，识别其中三种：扩大的，缩小的，波动支撑的。
* 用人工合成的数据和真实世界的数据来评估我们的算法

## 1. 介绍：
> Hoeffding Bound：Hoeffding inequality 在概率论中，Hoeffding 不等式提供了一个上限，这是所有随机变量偏离其期望值的综合。

**一个新的领域：**
+ 变化挖掘
+ 目标：我们称之为窗口的一个按时间排序的数据集的延续上，数据流发生了进化。我们用模式来描述这个变化中的数据流，现在的目标就是要发现这个模式的变化。

+ 一个方面：变化挖掘的一方面是要检测数据流中高频模式的变化。
  - 这依赖于基本模型的强壮假设的可用性，在我们试图发现变化的是这是不够的。
  - 大量的模式建立在数据流中不同的点上。
+ 因此我们需要自动化的发放来发现这些变化，因为手动核实这些模式的变化是不可行的。

+ 三个层面：
  - 项
  - 项集
  - 模式／规则

+ 最常见的变化监测技术主要看项层面的变化和模式层面的变化，本研究着眼于中间层，项集的变化。模式来源于规则挖掘终端有效项集。

**应用领域：**

+ 项集的变化可以被再现为客户的购买行为变化，销量的增加／减少
+ 经由考虑了项集的变化再形成的模式才能降低生成_overhead generating_的开支，修剪掉我们不关心的规则

**算法**
+ 本文给出一种新的算法来查找数据流中高频项集的变化
+ 我们关注三种变化的项集：扩张，收缩，支持度震荡。

## 2. 前人的研究

1. 高频模式的模版匹配，驱使被再现为形状查询：关联模式的支持度和置信度的历史的描绘。
2. 用统计测试的机制来描述变化检测的特征。
3. 用一种启发来确定模式中是否有变化。
  - 框架模式监视器用来监视规则历史，用来发现有趣的短期或长期变化。与其他方法不同的是它视历史为动态对象。
  - 早期检测长期变化是这项工作的重点。

以上研究集中在发现模式的变化，本文聚焦在找出用来产生模式的项集里的变化。

## 3. 准备工作**

+ 使用用数据上滑动窗口的高频项集的挖掘，用如下3个概念描述。

+ 三个阶段：项集生成，规则挖掘，检测变化
  - 起始阶段，由支持度确定有效的高频项集，然后传到规则挖掘阶段。然后发生变化的模式被评估变化是否已经发生，
  - 我们只通过值传递已经转换成模式挖掘算法的项集来推论
  - 我们降低生成的开支并修剪我们的机制

+ 定义
  - L：名称不同的多个项目的集合
  - 这些项目的一个子集称为项集
  - t=(TID, X)是一个元组，TID是交易ID，X是采购项集
  - S：数据流中的所有交易
  - I：频繁项集
  - $W_k$: 代表滑动窗口，k是标志符，N为元素个数


## 4. 项集变化挖掘

### 4.1 项集变化的种类

* 扩展集:
  + 扩展集在$W_k$的支持度／扩展集在$W_k^{'}$ 无限大，意味着差距无限大
*  缩小集：

> Hoeffding’s Inequality 用来确定边界 $\epsilon$
> 前后两个滑动窗口内的项集支持度发生的变化大小边界
> 超过这个阀值说明是显著的变化


* 支持度波动项集 $W_k$

I still need time to understand where is the $\epsilon$ comes from.
### 4.2 算法

## 5. 实验结果
**三个实验：**

1. 准确度
> Precision and recall measures
> Precision：准确度：提取的实例当中，有相关的比例
> Recall：查全率：所有相关实例中，被提取的比例
> See. https://en.wikipedia.org/wiki/Precision_and_recall

2. 运行时间
3. 在真是数据集上运行
与启发式的用用户自定义阀值的方法不同，我们用hoeffding 边界来帮我们指出一个变化。

### 5.1

## 6. 给出结论
pri