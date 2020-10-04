## NP问题

#### 1. 相关概念

- **P问题**：
  - 对于<u>任意大小输入</u>，可以在线性时间（Polynominal） 内**解决**。

- **NP问题**：
  - 给一个<u>候选输入</u>，可以在线性时间（Polynominal） 内**判断**是不是正确的解。
- **NP-hard问题**：
  - **至少**和NP问题一样难
- **NPC问题**：
  - 给一个<u>候选输入</u>，可以在线性时间（Polynominal） 内**判断**是不是正确的解。
  - 可以把任何一个NP问题在polynomial的时间内把他的input转化，使之成为一个NPC问题（即**规约**）

#### 2. 问题之间的关系

![这里写图片描述](https://img-blog.csdn.net/20160521163640138)

#### 3. 规约

![这里写图片描述](https://img-blog.csdn.net/20160521174000898)

#### 4. 问题的证明方法

- **证明NP问题**。即给你一个结果，你能在polynomial的时间内验证该结果的正确性。
- **证明NP-hard问题**。找到一个已被证明了的NPC问题，并把这个NPC问题归约到该问题上去（即NPC<=NP-hard）。
- **证明NP-Complete问题**
  1. 第一步证明这个问题属于NP；
  2. 第二步，证明这个问题是NP-hard的。

#### 5. NPC问题

##### **5.1 SAT问题:**

给定一个有穷的布尔变量集合X $=\left\{x_{1}, x_{2}, \ldots ., x_{n}\right\},|X|=n,$ 每个变量能取0或1，一组子句C $=\left\{C_{1}, C_{2}, \ldots ., C_{n}\right\},|C|=m$  $C=C_{1} \wedge C_{2} \wedge \ldots \wedge C_{m},$ 每个C,是由**多个变量**组成的析取范式，长度不限，即 $z_{1} \vee z_{2} \vee z_{3}, \ldots \vee z_{k^{\circ}}$

问：给定一个布尔变量集合X和子句集合C，是否存在一个真值赋值，使得C为真，即每个子句为真。

##### 5.2 3SAT问题:

给定一个有穷的布尔变量集合X $=\left\{x_{1}, x_{2}, \ldots ., x_{n}\right\}|X|=n,$ 每个变量能取0或 $1,-$组子句C$=\left\{C_{1}, C_{2}, \ldots ., C_{n}\right\},|C|=m$ $C=C_{1} \wedge C_{2} \wedge \ldots \wedge C_{m^{\prime}}$ 每个C,是一个由**三个变量**组成的析取范式，即 $z_{1} \vee z_{2} \vee z_{j}$

问：给定一个布尔变量集合X和子句集合C，是否存在一个真值烃值，使得C为真，即每个子句为真。

##### 5.3 **最大点独立集问题**

在图*G*中选出若干个顶点，这些顶点之间没有边相连接，称为点独立集。一个图中所有点独立集中点数最多的集合称为图的**最大点独立集**

##### 5.4 最小点覆盖问题

在图*G*中选出若干个顶点组成集合*S*，使得图中每一条边的两个顶点都至少有一个顶点在*S*中，则集合*S*称为图的点覆盖集。一个图中所有的点覆盖集中点数最少的集合称为图的**最小点覆盖**

#### 6. NPC问题规约例子

![这里写图片描述](https://img-blog.csdn.net/20160521163156306)

##### 6.1. 3SAT<=SAT

###### 1.证明3SAT是NP问题

3SAT的实例为X $=\left\{x_{1}, x_{2}, \ldots, x_{n}\right\}, \mathrm{C}=\left\{C_{1}, C_{2}, \ldots ., C_{n}\right\},$ 证为对每个变量的赋值，我们只要验证每个子句都为真即可 **很明显这个过程是多项式时间的**。

###### 2.给出规约过程

对于每个C，有以下四种情况:

1. $\left|C_{i}\right|=1,$ 则创建2个变量 $: y_{i, 1}, y_{i, 2},$ 使得 $C_{i}^{\prime}=\left(z_{i, 1} \vee y_{i, 1} \vee \overline{y_{i, 2}}\right) \wedge\left(z_{i, 1} \vee y_{i, 1} \vee y_{i, 2}\right) \wedge\left(z_{i, 1} \vee \overline{y_{i, 1}} \vee \overline{y_{i, 2}}\right) \wedge\left(z_{i, 1} \vee \overline{y_{i, 1}} \vee y_{i, 2}\right)$
2. $\left|C_{t}\right|=2,$ 则创建一个变量 $: y_{t, r},$ 使得 $C_{i}^{\prime}=\left(z_{t 1} \vee z_{t, 2} \vee \overline{y_{i}}\right) \wedge\left(z_{t, 1} \vee z_{t, 2} \vee y_{t, 1}\right)$
3. $\left|C_{t}\right|=3,$ 则不变即可
4. $\left|C_{i}\right| \geq 4,$ 假设为k，则添加k -3 个变量，使得 $C_{i}^{\prime}=\left(z_{i, 1} \vee z_{i, 2} \vee y_{u, 1}\right) \wedge\left(\overline{y_{i, 1}} \vee z_{i, 3} \vee y_{t, 2}\right) \wedge\left(\overline{y_{i, 2}} \vee z_{i, 4} \vee y_{t, 3}\right) \wedge \ldots \wedge\left(\overline{y_{i, k-3}} \vee z_{i, k-1} \vee z_{i, k}\right)$

###### 3. 证明此规约是多项式时间的

对于每个子句C, C,比C多了最多k-3个变量，因此多个m( $k$ -3)个变量和m (k-3)个子句。 接下来我们要证明C'是可满足的当且仅当C是可满足的。

对于每个SAT的实例，如果存在一个真值赋值，则每个子句C一定有一个literal为1，即 $z_{i, 1} \vee z_{t, 2} \vee z_{i, 3} \ldots . \vee z_{i, k}$ 中一定有一个为1,
$(1)\left|C_{t}\right|=1, \quad$ 则 $z_{t, 1}=1,$ 因此不论 $y_{t, r} y_{t, 2}$ 为何值， $\quad C_{t}^{\prime}=1$
$(2)\left|C_{t}\right|=2, \quad$ 则 $z_{t, 1} \vee z_{t, 2}=1, \quad$ 不论 $y_{t, 1}$ 为何值， $\quad C_{t}^{\prime}=1_{\circ}$
$(3)\left|C_{t}\right|=3, \quad$ 则 $C_{t}^{\prime}=1_{0}$
(4) $\left|C_{i}\right| \geq 4,$ 则假设 :
$-z_{t, 1} \vee z_{t, 2}=1, \quad$ 则 $y_{i, j}=0(j=1,2,3, \ldots ., k-3), \quad 因此C_{i}^{\prime}=1$
$-z_{i, k-1} \vee z_{i, k}=1, \quad$ 则 $y_{i, j}=1(j=1,2,3, \ldots, k-3),因此  C_{i}^{\prime}=1$
$-z_{t, j}=1(2<j<k-1), \quad$ 则 $] \overline{y_{t, a}}=0(\mathrm{a} \leq j-2), y_{i, a}=0(\mathrm{a} \geq j-1) 因此 C_{i}^{\prime}=1$

因此得到C' 的真值赋值t'。

假设t' 是C' 的真值赋值，很容易得出C存在真值赋值t‘。

