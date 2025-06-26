---
layout: default
---


#### 2025.6.26

#### 自监督/无监督学习 （默认目标：训练模型f() 从样本映射到特征向量

创新策略：实例级区分

$$
P(i | \mathbf{v}) = \frac{\exp\left(\frac{\mathbf{v} i^T \mathbf{v}}{\tau}\right)}{\sum_{j=1}^n \exp\left(\frac{\mathbf{v}_j^T \mathbf{v}}{\tau}\right)}
$$

分类器本身不包含可训练神经元，利用上游CNN backbone 和projection head的神经元，非参数分类器及训练中积累的特征库进行训练

传统策略：指定个实例对应到一个类，用vm...vn优化权重矩阵wi
wi与vi在特征空间中无位置联系，优化过程脱节
