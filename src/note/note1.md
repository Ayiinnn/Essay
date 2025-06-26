---
layout: default
---



#### 2025.6.26

---
### 自监督/无监督学习 （默认目标：训练模型f() 从样本映射到特征向量

创新策略：实例级区分（每一个样本作为一个类）

$$
P(i | \mathbf{v}) = \frac{\exp\left(\frac{\mathbf{v} i^T \mathbf{v}}{\tau}\right)}{\sum_{j=1}^n \exp\left(\frac{\mathbf{v}_j^T \mathbf{v}}{\tau}\right)}
$$

```
分类器本身不包含可训练神经元，利用上游CNN backbone 和projection head的神经元，非参数分类器及训练中积累的特征库进行训练（原先产生的特征向量作为空间中的参考点）
在每个训练循环都会更新神经元参数 同时将 特征库（memory bank）中的向量初始化为随机值
损失函数：
```

$$
J(\boldsymbol{\theta})=-\sum_{i=1}^n\log P(i|f_{\boldsymbol{\theta}}(x_i))
$$


对比：传统策略:指定个实例对应到一个类，用vm...vn优化权重矩阵wi

$$
P(i | \mathbf{v}) = \frac{\exp\left(\mathbf{w}_ i^T \mathbf{v}\right)}{\sum_{j=1}^n\exp\left(\mathbf{w}_j^T\mathbf{v}\right)}
$$

```
过程中wi与vi在特征空间中无位置联系，优化过程脱节，同时大数据场景下计算和存储w梯度占用资源
```

---

### 大数据优化 （类别量极大）

存在问题：类别数量极多时softmax计算开销大

解决策略：
1.hierarchical softmax
- [A Survey of Neural Network Techniques for Feature Extraction from Text](http://arxiv.org/abs/1704.08531)
  **[`arXiv 2017`]** *Vineet John*
2. negative sampling
- [Distributed Representations of Words and Phrases and their Compositionality](http://arxiv.org/abs/1310.4546)
  **[`arXiv 2013`]** *Tomas Mikolov*
3. NCE
- [Noise-contrastive estimation: A new estimation principle for unnormalized statistical models](https://proceedings.mlr.press/v9/gutmann10a/gutmann10a.pdf)
  **[`PMLR2010`]** *Tomas Mikolov*
  
---

