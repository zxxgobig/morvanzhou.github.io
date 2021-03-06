---
youku_id: XMTY5MjU1MTg0NA
youtube_id: 1YpKUpitT98
title: 特征标准化 (Feature Normalization)
description: 今天我们会来聊聊机器学习所需要的数据,为了让机器学习方面消化, 我们需不需要对数据动些手脚呢. 所以今天就会提到特征数据的标准化, 也可以说正常化, 归一化, 正规化等等. 使用这些标准化手段. 我们不仅可以快速推进机器学习的学习速度, 还可以避免机器学习 学得特扭曲.
chapter: 3
post-headings:
  - 现实中的数据
  - 数据方程
  - 举例说明
---

学习资料:
  * Sklearn: feature normalization [教程]({% link _tutorials/machine-learning/sklearn/3-1-normalization.md %})


今天我们会来聊聊机器学习所需要的数据,为了让机器学习方面消化, 我们需不需要对数据动些手脚呢. 所以今天就会提到特征数据的标准化, 也可以说正常化, 归一化, 正规化等等.

**注: 本文不会涉及数学推导. 大家可以在很多其他地方找到优秀的数学推导文章.**




 {% include assign-heading.html %}


<img class="course-image" src="/static/results/ML_intro/norm1.png" alt="{{ page.title }}{% increment image-count %}">

在说特征标准化之前, 我们先来说说现实生活中, 我们的数据是什么样的. 它们很可能来自不同的地方, 被不同的人采集, 有着不同的规格. 用最经典的房价预测例子来和大家说说. 我们用机器学习从房屋的各个层面来预测房价, 房屋的特征可能包括, 离市中心的距离, 房屋楼层, 房屋面积, 所在城市, 几室几厅等等. 这些数据的取值范围往往差距悬殊, 比如楼层一般在2-30层以内, 面积可能上百, 离市中心距离可以以千来记.


 {% include assign-heading.html %}

<img class="course-image" src="/static/results/ML_intro/norm2.png" alt="{{ page.title }}{% increment image-count %}">

回到机器学习中, 如果我们以一个简单的线性回归方程来预测房屋的价格, 那方程可能会是这样 . 价格= a* 离市中心 + b * 楼层 + c * 面积. 其中的 a b c 就是机器学习需要努力努力再努力 来优化的参数.

<img class="course-image" src="/static/results/ML_intro/norm3.png" alt="{{ page.title }}{% increment image-count %}">

我们说的在具体一点, 用 abc 算出来的价格是预测价格 . 机器学习需要计算预测值和实际值的差别, 然后对这个误差进行一些数学上的处理, 使之变成进步的阶梯, 然后反向地传递回参数 a b c 来提升下次的预测准确度. 好了. 这些概念和我们要提到的标准化有什么关系呢?



{% include google-in-article-ads.html %}

 {% include assign-heading.html %}

<img class="course-image" src="/static/results/ML_intro/norm4.png" alt="{{ page.title }}{% increment image-count %}">

我们可以把 abc 想想成3个人. 他们共同努力解决一个问题, 在某一个问题中, a工作的时候总是不知道发生了什么, b 的能力适中, c 工作能力最强, 老板看了他们一起工作的结果, 发现还有很多可以提高的地方, 然后不屑地说: 你们这个结果和我期望的还有很大差距, 你们快去缩小差距. 老板给的要求只是缩小差距. 可是 abc 都不知道差距在哪. 所以他们这次只好平分接下来的任务, 不过 c 很快就做完了, b 第二, a 做得很慢, 所以花的总时间很长, c 和 b 都要等 a 把剩下的工作做完才能再给老板看结果, 这样 效率并不高.

<img class="course-image" src="/static/results/ML_intro/norm5.png" alt="{{ page.title }}{% increment image-count %}">

把这个问题放在机器学习中, 为了好理解, 我们把 b 先排除掉. 再把房价问题也简化一下, 留下两个特征. 因为面积的跨度一般可以从0 到 2-300, 而离市中心的距离跨度一般在10以内. 所以在这个公式中, c 只要稍稍变化一点, 他乘以面积的变化就会很大, 因为面积的值可以很大, 但是当a也变化那一点点时, 他对预测价格的影响力不会像 c 那样巨大. 这样的差别就会影响最终的工作效率. 所以, 我们要提高效率, 特征的标准化就可以帮上忙. 我们在机器学习训练之前, 先对数据预先处理一下, 取值跨度大的特征数据, 我们浓缩一下, 跨度小的括展一下, 使得他们的跨度尽量统一.

<img class="course-image" src="/static/results/ML_intro/norm6.png" alt="{{ page.title }}{% increment image-count %}">

通常用于 特征标准化的途径有两种, 一种叫做 min max normalization, 他会将所有特征数据按比例缩放到0-1的这个取值区间. 有时也可以是-1到1的区间. 还有一种叫做 standard deviation normalization, 他会将所有特征数据缩放成 平均值为0, 方差为1. 使用这些标准化手段. 我们不仅可以快速推进机器学习的学习速度, 还可以避免机器学习 学得特扭曲.


