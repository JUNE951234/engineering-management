---
created: 2025/11/19 16:22
updated: 2025/11/20 11:20
aliases:
---
熵权 TOPSIS 是一种**客观赋权+多属性逼近排序**的两阶段综合评价方法：  
1. 先用**熵权法**从数据本身提取各指标权重（避免人为主观）；  
2. 再用**TOPSIS**计算每个方案与“理想解”的相对贴近度，给出排序。

---

### 1 数据标准化
设有 n 个方案、m 个指标，构成矩阵
$$
X=(x_{ij})_{n\times m},\quad i=1,\dots,n;\; j=1,\dots,m
$$

对正向指标（越大越好）常用归一化
$$
r_{ij}=\frac{x_{ij}-\min_i x_{ij}}{\max_i x_{ij}-\min_i x_{ij}};
$$

对负向指标（越小越好）
$$
r_{ij}=\frac{\max_i x_{ij}-x_{ij}}{\max_i x_{ij}-\min_i x_{ij}}.
$$

得到标准化矩阵
$$
R=(r_{ij})_{n\times m},\quad 0\le r_{ij}\le 1.
$$

---

### 2 计算熵权
第 j 项指标的“比重”
$$
p_{ij}=\frac{r_{ij}}{\sum_{i=1}^n r_{ij}},\quad \text{令 } p_{ij}=0 \text{ 若 } r_{ij}=0.
$$

熵值
$$
e_j=-\frac{1}{\ln n}\sum_{i=1}^n p_{ij}\ln p_{ij},\quad 0\le e_j\le 1.
$$

差异系数
$$
d_j=1-e_j.
$$

熵权（客观权重）
$$
w_j=\frac{d_j}{\sum_{k=1}^m d_k},\quad \sum_{j=1}^m w_j=1.
$$

---

### 3 构造加权规范阵
$$
V=(v_{ij})_{n\times m},\quad v_{ij}=w_j\,r_{ij}.
$$

---

### 4 确定正、负理想解


$$
\begin{aligned}
V^+&=\bigl(\max_i v_{i1},\,\max_i v_{i2},\,\dots,\,\max_i v_{im}\bigr)= (v_1^+,v_2^+,\dots,v_m^+),\\[2pt]
V^-&=\bigl(\min_i v_{i1},\,\min_i v_{i2},\,\dots,\,\min_i v_{im}\bigr)= (v_1^-,v_2^-,\dots,v_m^-).
\end{aligned}
$$


---

### 5 计算欧氏距离
方案 i 到正理想解距离
$$
D_i^+=\sqrt{\sum_{j=1}^m (v_{ij}-v_j^+)^2}.
$$

到负理想解距离
$$
D_i^-=\sqrt{\sum_{j=1}^m (v_{ij}-v_j^-)^2}.
$$

---

### 6 相对贴近度
$$
C_i=\frac{D_i^-}{D_i^++D_i^-},\quad 0\le C_i\le 1.
$$

按 $C_i$ 从大到小排序，**值越大方案越优**。

---

### 7 一句话总结
熵权 TOPSIS = **用数据说话定权重** + **找离“最优模板”最近的方案**，全过程无需人为主观打分。