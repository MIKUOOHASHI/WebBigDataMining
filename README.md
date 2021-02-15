# Web大数据挖掘作业
## 目录
作业一：Compute the PageRank scores on the Wikipedia dataset  
作业二：Predict the rating scores of the pairs (u, i) in the Test.txt file

## 写在前面
1、如果需要作业细节，请联系作者获取。  
2、作者联系方式(WeChat)：  
![image](https://github.com/MIKUOOHASHI/WebBigDataMining/blob/main/all_needed_image/Hello.png)

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
  
  ![image](https://github.com/MIKUOOHASHI/WebBigDataMining/blob/main/all_needed_image/1.1.png)

  2.2 节点总数：7115
  
  ![image](https://github.com/MIKUOOHASHI/WebBigDataMining/blob/main/all_needed_image/1.2.png)

  2.3 最大节点ID：8297
  
  ![image](https://github.com/MIKUOOHASHI/WebBigDataMining/blob/main/all_needed_image/1.3.png)

  2.4 数据调用位置
  
  ![image](https://github.com/MIKUOOHASHI/WebBigDataMining/blob/main/all_needed_image/1.4.png)

3 关键代码细节  
  3.1考虑dead ends和spider trap节点  
  考虑到这两种情况下的节点，PageRank算法引入了随机浏览模型。定义阻尼因子α，代表了用户按照跳转链接来上网的概率，通常取一个固定值0.85，而 1- α = 0.15 则代表了用户不是通过跳转链接的方   式来访问网页的。
  
  ![image](https://github.com/MIKUOOHASHI/WebBigDataMining/blob/main/all_needed_image/1.5.png)

  3.2优化稀疏矩阵

  3.3实现分块计算

......

4 本机(Win10)运行截图
  4.1	alpha = 0.75，分为1块进行计算
  
  ![image](https://github.com/MIKUOOHASHI/WebBigDataMining/blob/main/all_needed_image/1.6.png)

......

5 云主机运行截图

![image](https://github.com/MIKUOOHASHI/WebBigDataMining/blob/main/all_needed_image/1.7.png)

6 实验结果
  6.1 alpha取值相同，分块不同
  
  ![image](https://github.com/MIKUOOHASHI/WebBigDataMining/blob/main/all_needed_image/1.8.png)

......

---------------------------------------
## 作业二：
### 描述：
Dataset:   
        (1)Train.txt, which is used for training your models.  
        (2)Test.txt, which is used for test.   
        (3)ItemAttribute.txt, which is used for training your models (optional).  
        (4)ResultForm.txt, which is the form of your result file.  
        
The formats of datasets are explained in the DataFormatExplanation.txt.   
Note that if you can use ItemAttribute.txt appropriately and improve the performance of the algorithms, additional points (up to 10) can be added to your final course score. 

### 要求：
In this project, you need to report the predicted rating scores of the unknown pairs (u, i) in the Test.txt file. You can use any algorithms you have learned from the course or from other resources (such as MOOC). One group (consisting of at most two students) needs to write a report about this project. The report should include but not limited to the following contents:

(1)Basic statistics of the dataset (e.g., number of users, number of ratings, number of items, etc);   
(2)Details of the algorithms;   
(3)Experimental results of the recommendation algorithms (RMSE, training time, space consumption);   
(4)Theoretical analysis or/and experimental analysis of the algorithms. 
        
### 实现细节：
1 问题描述  
利用 train.txt 文件给定的数据，根据不同用户对不同电影的已知评分，结合 协同过滤的思想，预测 test.txt 文件中用户对其他电影的可能评分。 

2 实验原理  
协同过滤（Collaborative Filtering Recommendation）技术是推荐系统中应用 最早和最为成功的技术之一。协同过滤简单来说是利用某兴趣相投、拥有共同经 验之群体的喜好来推荐用户感兴趣的信息。它一般采用最近邻技术，利用用户的 历史喜好信息计算用户之间的距离，然后利用目标用户的最近邻居用户对商品评 价的加权评价值来预测目标用户对特定商品的喜好程度，系统从而根据这一喜好 程度来对目标用户进行推荐。 本次实验采用的是基于 item 的协同过滤算法。通过不同用户对不同 item 的 评分来评测 item 之间的相似性，基于 item 的相似性做推荐。 基于 item 的协同过滤算法主要分为两步：1）计算 item 之间的相似度；2） 根据 item 的相似度和用户的历史行为给用户生成推荐列表。因此，我们可以用 公式(2.1)定义 item 的相似度： 

......

3 数据集统计信息   
经过对给定的 train.txt 和 test.txt 文件进行分析和统计，训练集 train.txt 和测 试集 test.txt 的相关统计信息分别如下所示。   
1）训练集 训练集 train.txt 文件中所包含的用户数，评分记录以及项目数量等统计信息 如表所示。   
2）测试集 测试集 test.txt 文件中所包含的用户数，评分记录以及项目数量等统计信息 如表所示。

4 算法细节   
1)读取磁盘上测试集 test.txt 文件，获取 user 和要预测 user 评分的 items；  
2)获取 user 之后，在训练集中得到每个 user 曾评分过的 items，它们是用于 计算预测分数的相似项； 

5 实验结果

![image](https://github.com/MIKUOOHASHI/WebBigDataMining/blob/main/all_needed_image/2.1.png)

......
