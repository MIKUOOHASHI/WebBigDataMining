# Web大数据挖掘作业
## 目录
作业一：Compute the PageRank scores on the Wikipedia dataset
作业二：

## 写在前面
1、如果需要作业细节，请联系作者获取。  
2、作者联系方式(WeChat)：  
![image](https://github.com/MIKUOOHASHI/IntelligentSoftwareTesting/blob/master/all_needed_images/Hello.png)

3、添加作者请备注来源(github)

---------------------------------
## 作业一：
### 描述：
Dataset: WikiData.txt
The format of the lines in the file is as follow: 
                 FromNodeID ToNodeID
In this project, you need to report the Top 100 NodeID with their PageRank scores. You can choose different parameters, such as the teleport parameter, to compare different results. One result you must report is that when setting the teleport parameter to 0.85.
In addition to the basic PageRank algorithm, you need to implement the Block-Stripe Update algorithm (see pages 52-61 in the PPT: LinkAnalysis1).

### 要求：
        (1)语言: C/C++/JAVA/Python.
        (2)考虑dead ends 和spider trap节点.
        (3)优化稀疏矩阵.
        (4)实现分块计算.
        (5)程序需要迭代至收敛.
        (6)不可直接调接口，例如实现pagerank时，调用Python的networkx包.
        (7)结果格式(.txt文件)：[NodeID]   [Score].
        
### 实现细节：
1 算法简介：略

2 WikiData数据集说明
2.1 数据总行数：103689
![image]()

2.2 节点总数：7115
![image]()

2.3 最大节点ID：8297
![image]()

2.4 数据调用位置
![image]()

3 关键代码细节
3.1考虑dead ends和spider trap节点
考虑到这两种情况下的节点，PageRank算法引入了随机浏览模型。定义阻尼因子α，代表了用户按照跳转链接来上网的概率，通常取一个固定值0.85，而 1- α = 0.15 则代表了用户不是通过跳转链接的方式来访问网页的。
![image]()

3.2优化稀疏矩阵

3.3实现分块计算

......

4 本机(Win10)运行截图
4.1	alpha = 0.75，分为1块进行计算
![image]()

......

5 云主机运行截图
![image]()

6.	实验结果
6.1 alpha取值相同，分块不同
![image]()

......




