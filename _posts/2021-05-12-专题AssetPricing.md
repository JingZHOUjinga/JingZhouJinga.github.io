---
layout:     post
title:      专题阅读|资产定价
subtitle:   总结与梳理
date:       2021-05-12
author:     Jinga
header-img: img/grey.jpg
catalog: true
tags:
    - Asset Pricing


---
# 资产定价

* [1.介绍](#1)


<h2 id="1">1.介绍</h2>


[自编码器网络在条件风险因子和资产定价中的应用（上）](https://zhuanlan.zhihu.com/p/267362008)   

变分自编码器

变分自编码VAE（Variational AutoEncoder）是自编码器模型中较新的一类，其主要用于生成模型。

区别于AE模型要求复现原始输入，VAE学习的是能够生成原始数据的概率分布的参数。对于训练成功的VAE模型，可以对VAE学到的概率分布进行采样生成新的数据。

Wang et al. (2019)将VAE与采用LSTM的RNN网络结合应用于期货市场，其模型结果打败了许多经典模型。

    Wang, J., Sun, T., Liu, B., Cao, Y., & Zhu, H. (2019, August). CLVSA: A convolutional LSTM based variational sequence-to-sequence model with attention for predicting trends of financial markets. In Proceedings of the 28th International Joint Conference on Artificial Intelligence (pp. 3705-3711). AAAI Press. https://doi.org/10.24963/ijcai.2019/514.
  

GKX根据Green等人(2017)的方法测试了94种资产属性，并确定了20个最具影响力的指标，同时断言剩余指标的重要性迅速下降。

前20个股票特征可分为三类，分别是

    价格趋势，包括(行业)动量，短期和长期逆转或最近的最大回报 流动性，例如营业额，美元数量或市值 风险度量，例如总回报率和特殊回报率波动率或市场beta   







![process.png](/img/20210512process.png)




[Machine Learning for Algorithmic Trading: Predictive models to extract signals from market and alternative data for systematic trading strategies with Python, 2nd Edition](https://2lib.org/book/5867328/b4c5ff)   
[Machine Learning for Algorithmic Trading code](https://github.com/packtpublishing/machine-learning-for-algorithmic-trading)   






##### 参考:
<div id="refer-anchor-1"></div>
- [1] []