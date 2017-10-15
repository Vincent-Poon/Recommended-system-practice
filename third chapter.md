# 推荐系统冷启动问题
## 冷启动问题简介
1. 冷启动问题的主要分类
	1. 用户冷启动
	2. 物品冷启动
	3. 系统冷启动
2. 一般解决方案
	1. 提供非个性化的推荐 非个性化推荐的最简单例子就是热门排行榜，我们可以给用户推荐热门排行榜，然后等到用户数据收集到一定的时候，再切换为个性化推荐。
	2. 利用用户注册时提供的年龄、性别等数据做粗粒度的个性化。
	3. 利用用户的社交网络账号登录（需要用户授权），导入用户在社交网站上的好友信息，然后给用户推荐其好友喜欢的物品。
	4. 要求用户在登录时对一些物品进行反馈，收集用户对这些物品的兴趣信息，然后给用户推荐那些和这些物品相似的物品。
	5. 对于新加入的物品，可以利用内容信息，将它们推荐给喜欢过和它们相似的物品的用户。
	6. 在系统冷启动时，可以引入专家的知识，通过一定的高效方式迅速建立起物品的相关度表。
## 利用用户注册信息
1. 用户注册信息分类
	* 人口统计学信息
	* 用户兴趣的描述
	* 从其他网站导入的用户站外行为数据
2. 基于注册信息的个性化推荐流程基本如下：
	1. 获取用户的注册信息；
	2. 根据用户的注册信息对用户分类；
	3. 给用户推荐他所属分类中用户喜欢的物品。
3. 计算每种特征的用户喜欢的物品。
	基于用户注册信息的推荐算法其核心问题是计算每种特征的用户喜欢的物品。也就是说，对于每种特征f，计算具有这种特征的用户对各个物品的喜好程度p(f, i)。
    ![喜好程度](https://github.com/easezyc/Recommended-system-practice/blob/master/pics/pic25.png?raw=true)
## 选择合适的物品启动用户的兴趣
解决用户冷启动问题的另一个方法是在新用户第一次访问推荐系统时，不立即给用户展示推荐结果，而是给用户提供一些物品，让用户反馈他们对这些物品的兴趣，然后根据用户反馈给提供个性化推荐。
能够用来启动用户兴趣的物品需要具有以下特点：
1. 比较热门
2. 具有代表性和区分性
3. 启动物品集合需要有多样性

如何选择启动物品集合呢。可以用决策树解决这个问题。
![选择启动物品](https://github.com/easezyc/Recommended-system-practice/blob/master/pics/pic26.png?raw=true)
![选择启动物品](https://github.com/easezyc/Recommended-system-practice/blob/master/pics/pic27.png?raw=true)
## 利用物品的内容信息
1. 物品的内容可以通过向量空间模型表示，该模型会将物品表示成一个关键词向量。如果物品的内容是一些诸如导演、演员等实体的话，可以直接将这些实体作为关键词。但如果内容是文本的形式，则需要引入一些理解自然语言的技术抽取关键词。
![关键词向量的生成过程](https://github.com/easezyc/Recommended-system-practice/blob/master/pics/pic28.png?raw=true)
得到物品相似度之后，可以用ItemCF算法的思想，给用户推荐和他历史上喜欢的物品内容相似的物品。
2. LDA话题模型
## 发挥专家的作用
为了在推荐系统建立时就让用户得到比较好的体验，很多系统都利用专家进
行标注。