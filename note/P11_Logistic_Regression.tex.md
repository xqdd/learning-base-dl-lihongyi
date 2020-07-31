# Logistic Regression

## 分类概率函数(或者说model，由P10分类得到)

$f_{w,b}(x)=\sigma(z)$
$\sigma(x)=\frac{1}{1+exp(-x)}=\frac{1}{1+e^{-x}}$
$z=\sum_iw_ix_i+b$

## 损失函数

1. 训练数据

| $x^1$ | $x^2$ | $x^3$ | ... | $x^N$ |
| ----- | ----- | ----- | --- | ----- |
| $C_1$ | $C_1$ | $C_2$ | ... | $C_1$ |

2. 设$f_{w,b}(x)=P_{w,b}(C_1|x)$
3. 则得到损失函数$L(w,b)=f_{w,b}(x^1)f_{w,b}(x^2)(1-f_{w,b}(x^3))...f_{w,b}(x^N)$
4. 最适合的$w,b$是$w*,b*=arg\max_{w,b}L(w,b)=\arg\min_{w,b}-lnL(w,b)$
5. 设$\hat{y}^n的取值范围为${1,0}，$C_1=1，C_2=0$（即当前为二分类问题）：

| $x^1$         | $x^2$         | $x^3$         | ... | $x^N$             |
| ------------- | ------------- | ------------- | --- | ----------------- |
| $\hat{y}^1=1$ | $\hat{y}^2=1$ | $\hat{y}^3=0$ | ... | $\hat{y}^N=${1,0} |

6. 最终的损失函数为：$-lnL(w,b)=lnf_{w,b}(x^1)+lnf_{w,b}(x^2)+ln(1-f_{w,b}(x^3))...lnf_{w,b}(x^N)=\sum_n-[\hat{y}^nlnf_{w,b}(x^n)+(1-\hat{y}^n)ln(1-f_{w,b}(x^n))]=C(f(x^n),\hat{y}^n)$

## 梯度下降更新函数

将最终的损失函数通过一系列微分计算得到
$w_i\gets{w_i-}\eta\sum_n(-\hat{y}^n-f_{w,b}(x^n)x_i^n)$