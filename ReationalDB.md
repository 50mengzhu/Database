### 关系型数据库

#### 一、什么是数据库，为什么会产生数据库

&emsp;&emsp;原来人们都是使用文件来存储数据。对于普通的数据还好，但是最后由于数据量的庞大以及最后的无结构数据的情况越来越多，导致查询和管理数据相当不方便。最后直接就导致了数数据库的产生。具体也有很多渊源，从最开始的树形存储以及其他的图存储等，到后来的以mysql为代表的关系型数据库的出现以及产生，近几年比较火的no-sql的非关系型数据库，反而采用键值对的形式对数据进行存储。

#### 二、数据模型

现实世界		`数据模型`	信息世界		``	机器世界

##### （一）（包括）概念模型

$概念模型\begin{cases} 实体（“类名”）\\ 属性（“属性”）\\ 码（能够唯一标识实体的值）\\ 实体型（“类和她的属性”）\\ 实体集（“类内的成员集合”）\\ 联系（就是类之间的关系）\end{cases}$

> 注意：联系在这里主要是一对一、一对多以及多对多的关系。

#####（二）数据模型的组成

数据模型的组成主要是以下三部分：

+ 数据结构：也就是数据之间的关系
+ 数据操作：数据的增删改查的操作
+ 数据完整性约束：主要是针对属性的范围——例如：人的年龄不能超过150岁等等这样的一些约束

##### （三）关系型数据库

+ 关系（就是数据表）
+ 元组（行）
+ 属性（列）
+ 码（关键字）
+ 域（列属性的数值的集合）
+ 分量（元组中的一个属性值）
+ 关系模型（用来简单表示一张表）

> 关系模型要求关系必须规范化，最基本的一条就是：
>
> <font color="red">每一个元组必须是最小的，不可分的。关系的每个属性也是不可分割的</font>
>
> <table>
>     <tr>
>         <td rowspan="2"><center>职工ID</center></td>
>         <td rowspan="2"><center>姓名</center></td>
>         <td colspan="3"><center>工资</center></td>
>     </tr>
>     <tr>
>         <td><center>基本工资</center></td>
>         <td><center>岗位津贴</center></td>
>         <td><center>业绩津贴</center></td>
>     </tr>
> </table>
>
> 这就不符合规范化的要求

#### 三、关系型数据库

定义一个集合操作：笛卡尔积

> $D_1\times D_2\times D_3\times \cdots \times D_n = \{(d_1, d_2, d_3,\cdots, d_n)| d_i\in D_i , i = 1, 2, \cdots, n\}$

【概念】候选码

&emsp;&emsp;如果关系中的某属性的值能够唯一地标识一个元组，而它的子集不能，那么这个属性组集合称为候选码。在候选码中任取一个称为主键。

> 换而言之，候选码就是属性值中最小的唯一属性码的集合

【概念】外码（外键）

&emsp;&emsp;在两个数据表存在某种关系的时候（比如一对一、一对多、多对多等），从而在数据库设计的时候将其中某一个表的主键放到另一个表中充当的一个属性叫做外键。（不准确的定义）

##### （一）数据操作

&emsp;&emsp;因为关系型数据库的数据结构是关系，也就是表。因此我们对于数据的操作总体来说是增、删、改、查，我们的重点主要放在查询上。

&emsp;&emsp;查询的操作主要有选择、投影、链接、除法、并、差、交、笛卡尔积。主要的精力放在选择、投影、并、差、笛卡尔积上。

##### （二）数据完整性

+ 实体完整性：主码不能为空
+ 参照完整性：外码取值为空或者只能取所限定的值
+ 用户定义

#### 四、关系代数

&emsp;&emsp;由于关系型数据库的数据结构是表，也算是集合的一种，因此主要的运算可大致分为两类：

<center>R</center>
<table>
    <tr>
        <td><center>A</center></td>
        <td><center>B</center></td>
        <td><center>C</center></td>
    </tr>
    <tr>
        <td><center>a<sub>1</sub></center></td>
        <td><center>b<sub>1</sub></center></td>
        <td><center>c<sub>1</sub></center></td>
    </tr>
    <tr>
        <td><center>a<sub>1</sub></center></td>
        <td><center>b<sub>2</sub></center></td>
        <td><center>c<sub>2</sub></center></td>
    </tr>
    <tr>
        <td><center>a<sub>2</sub></center></td>
        <td><center>b<sub>2</sub></center></td>
        <td><center>c<sub>1</sub></center></td>
    </tr>
</table>

<center>S</center>
<table>
    <tr>
        <td><center>A</center></td>
        <td><center>B</center></td>
        <td><center>C</center></td>
    </tr>
    <tr>
        <td><center>a<sub>1</sub></center></td>
        <td><center>b<sub>2</sub></center></td>
        <td><center>c<sub>2</sub></center></td>
    </tr>
    <tr>
        <td><center>a<sub>1</sub></center></td>
        <td><center>b<sub>3</sub></center></td>
        <td><center>c<sub>2</sub></center></td>
    </tr>
    <tr>
        <td><center>a<sub>2</sub></center></td>
        <td><center>b<sub>2</sub></center></td>
        <td><center>c<sub>1</sub></center></td>
    </tr>
</table>

#####（一）传统的集合运算

###### 1. 并

$R\cup S = \{t\mid t \in R \vee t \in S\}$

<center>R&cup;S</center>
<table>
    <tr>
        <td><center>A</center></td>
        <td><center>B</center></td>
        <td><center>C</center></td>
    </tr>
    <tr>
        <td><center>a<sub>1</sub></center></td>
        <td><center>b<sub>1</sub></center></td>
        <td><center>c<sub>1</sub></center></td>
    </tr>
    <tr>
        <td><center>a<sub>1</sub></center></td>
        <td><center>b<sub>2</sub></center></td>
        <td><center>c<sub>2</sub></center></td>
    </tr>
    <tr>
        <td><center>a<sub>2</sub></center></td>
        <td><center>b<sub>2</sub></center></td>
        <td><center>c<sub>1</sub></center></td>
    </tr>
    <tr>
        <td><center>a<sub>1</sub></center></td>
        <td><center>b<sub>3</sub></center></td>
        <td><center>c<sub>2</sub></center></td>
    </tr>
</table>

###### 2.差

$R - S = \{t\mid t \in R \wedge t \notin S\}$

<center>R-S</center>
<table>
    <tr>
        <td><center>A</center></td>
        <td><center>B</center></td>
        <td><center>C</center></td>
    </tr>
    <tr>
        <td><center>a<sub>1</sub></center></td>
        <td><center>b<sub>1</sub></center></td>
        <td><center>c<sub>1</sub></center></td>
    </tr>
</table>

###### 3.交

$R\cap S = \{t \mid t\in R \wedge t \in S\}$

<center>R&cap;S</center>
<table>
    <tr>
        <td><center>A</center></td>
        <td><center>B</center></td>
        <td><center>C</center></td>
    </tr>
    <tr>
        <td><center>a<sub>1</sub></center></td>
        <td><center>b<sub>2</sub></center></td>
        <td><center>c<sub>2</sub></center></td>
    </tr>
    <tr>
        <td><center>a<sub>2</sub></center></td>
        <td><center>b<sub>2</sub></center></td>
        <td><center>c<sub>1</sub></center></td>
    </tr>
</table>

###### 4.笛卡尔积

$R\times S = \{(t_r, t_s)\mid t_r\in R\wedge t_s\in S\}$

<center>R&times;S</center>
<table>
    <tr>
        <td><center>R.A</center></td>
        <td><center>R.B</center></td>
        <td><center>R.C</center></td>
        <td><center>S.A</center></td>
        <td><center>S.B</center></td>
        <td><center>S.C</center></td>
    </tr>
    <tr>
        <td><center>a<sub>1</sub></center></td>
        <td><center>b<sub>1</sub></center></td>
        <td><center>c<sub>1</sub></center></td>
        <td><center>a<sub>1</sub></center></td>
        <td><center>b<sub>2</sub></center></td>
        <td><center>c<sub>2</sub></center></td>
    </tr>
    <tr>
        <td><center>a<sub>1</sub></center></td>
        <td><center>b<sub>1</sub></center></td>
        <td><center>c<sub>1</sub></center></td>
        <td><center>a<sub>1</sub></center></td>
        <td><center>b<sub>3</sub></center></td>
        <td><center>c<sub>2</sub></center></td>
    </tr>
    <tr>
        <td><center>a<sub>1</sub></center></td>
        <td><center>b<sub>1</sub></center></td>
        <td><center>c<sub>1</sub></center></td>
        <td><center>a<sub>2</sub></center></td>
        <td><center>b<sub>2</sub></center></td>
        <td><center>c<sub>1</sub></center></td>
    </tr>
    <tr>
        <td><center>a<sub>1</sub></center></td>
        <td><center>b<sub>2</sub></center></td>
        <td><center>c<sub>2</sub></center></td>
        <td><center>a<sub>1</sub></center></td>
        <td><center>b<sub>2</sub></center></td>
        <td><center>c<sub>2</sub></center></td>
    </tr>
    <tr>
        <td><center>a<sub>1</sub></center></td>
        <td><center>b<sub>2</sub></center></td>
        <td><center>c<sub>2</sub></center></td>
        <td><center>a<sub>1</sub></center></td>
        <td><center>b<sub>3</sub></center></td>
        <td><center>c<sub>2</sub></center></td>
    </tr>
    <tr>
        <td><center>a<sub>1</sub></center></td>
        <td><center>b<sub>2</sub></center></td>
        <td><center>c<sub>2</sub></center></td>
        <td><center>a<sub>2</sub></center></td>
        <td><center>b<sub>2</sub></center></td>
        <td><center>c<sub>1</sub></center></td>
    </tr>
    <tr>
        <td><center>a<sub>2</sub></center></td>
        <td><center>b<sub>2</sub></center></td>
        <td><center>c<sub>1</sub></center></td>
        <td><center>a<sub>1</sub></center></td>
        <td><center>b<sub>2</sub></center></td>
        <td><center>c<sub>2</sub></center></td>
    </tr>
    </tr>
    <tr>
        <td><center>a<sub>2</sub></center></td>
        <td><center>b<sub>2</sub></center></td>
        <td><center>c<sub>1</sub></center></td>
        <td><center>a<sub>1</sub></center></td>
        <td><center>b<sub>3</sub></center></td>
        <td><center>c<sub>2</sub></center></td>
    </tr>
    <tr>
        <td><center>a<sub>2</sub></center></td>
        <td><center>b<sub>2</sub></center></td>
        <td><center>c<sub>1</sub></center></td>
        <td><center>a<sub>2</sub></center></td>
        <td><center>b<sub>2</sub></center></td>
        <td><center>c<sub>1</sub></center></td>
    </tr>
</table>

#####（二）专门的集合运算

###### 1.选择（选行）

选择是从关系R中选择满足给定条件的诸元组。

$$\sigma _F(R) = \{t\mid t\in R\wedge F(t) = true\}$$

> 注意，此处的F是一个条件选择函数
>
> 例：$\sigma_{A = 'a1'}(R) $的结果如下：
>
> <center>&sigma;<sub>A="a1"</sub>(R)</center>
> <table>
>     <tr>
>         <td><center>A</center></td>
>         <td><center>B</center></td>
>         <td><center>C</center></td>
>     </tr>
>     <tr>
>         <td><center>a<sub>1</sub></center></td>
>         <td><center>b<sub>1</sub></center></td>
>         <td><center>c<sub>1</sub></center></td>
>     </tr>
>     <tr>
>         <td><center>a<sub>1</sub></center></td>
>         <td><center>b<sub>2</sub></center></td>
>         <td><center>c<sub>2</sub></center></td>
>     </tr>
> </table>

###### 2.链接

链接是从两个关系的笛卡尔积中选取属性间满足一定条件的元组。

$\mathop{R⋈S}\limits_{A\theta B} ^ {}= \{\overset{\LARGE{\frown}}{t_rt_s} \mid t_s \in R\wedge t_s \in S \wedge t_r[A]\theta t_s[B] \}$

<center>R</center>
<table>
    <tr>
        <td><center>A</center></td>
        <td><center>B</center></td>
        <td><center>C</center></td>
    </tr>
    <tr>
        <td><center>a<sub>1</sub></sub></center></td>
        <td><center>b<sub>1</center></td>
        <td><center>5</center></td>
    </tr>
    <tr>
        <td><center>a<sub>1</center></td>
        <td><center>b<sub>2</center></td>
        <td><center>6</center></td>
    </tr>
    <tr>
        <td><center>a<sub>2</center></td>
        <td><center>b<sub>3</center></td>
        <td><center>8</center></td>
    </tr>
    <tr>
        <td><center>a<sub>2</center></td>
        <td><center>b<sub>4</center></td>
        <td><center>12</center></td>
    </tr>
</table>

<center>S</center>
<table>
    <tr>
        <td><center>B</center></td>
        <td><center>E</center></td>
    </tr>
    <tr>
        <td><center>b<sub>1</sub></center></td>
        <td><center>3</center></td>
    </tr>
    <tr>
        <td><center>b<sub>2</sub></center></td>
        <td><center>7</center></td>
    </tr>
    <tr>
        <td><center>b<sub>3</sub></center></td>
        <td><center>10</center></td>
    </tr>
    <tr>
        <td><center>b<sub>3</sub></center></td>
        <td><center>2</center></td>
    </tr>
    <tr>
        <td><center>b<sub>5</sub></center></td>
        <td><center>2</center></td>
    </tr>
</table>

<center>R⋈S (R.B = S.B)</center>
<table>
    <tr>
        <td><center>A</center></td>
        <td><center>R.B</center></td>
        <td><center>C</center></td>
        <td><center>S.B</center></td>
        <td><center>E</center></td>
    </tr>
    <tr>
        <td><center>a<sub>1</sub></center></td>
        <td><center>b<sub>1</sub></center></td>
        <td><center>5</center></td>
        <td><center>b<sub>1</sub></center></td>
        <td><center>3</center></td>
    </tr>
    <tr>
        <td><center>a<sub>1</sub></center></td>
        <td><center>b<sub>2</sub></center></td>
        <td><center>6</center></td>
        <td><center>b<sub>2</sub></center></td>
        <td><center>7</center></td>
    </tr>
    <tr>
        <td><center>a<sub>2</sub></center></td>
        <td><center>b<sub>3</sub></center></td>
        <td><center>8</center></td>
        <td><center>b<sub>3</sub></center></td>
        <td><center>10</center></td>
    </tr>
    <tr>
        <td><center>a<sub>2</sub></center></td>
        <td><center>b<sub>3</sub></center></td>
        <td><center>8</center></td>
        <td><center>b<sub>3</sub></center></td>
        <td><center>2</center></td>
    </tr>
</table>

【概念】等值连接、非等值连接、自然连接、外连接（左、右）

###### 3.投影（选列）

投影是从R选择出若干属性列组成的新的关系。

$\Pi_A(R) = \{t[A] \mid t \in R\}$

> 注意：A是R的属性列
>
> 例：$\Pi_{A, B}(R)$的结果为：
>
> <center>&pi;<sub>A,B</sub>(R)</center>
> <table>
>     <tr>
>         <td><center>A</center></td>
>         <td><center>B</center></td>
>     </tr>
>     <tr>
>         <td><center>a<sub>1</sub></center></td>
>         <td><center>b<sub>1</sub></center></td>
>     </tr>
>     <tr>
>         <td><center>a<sub>1</sub></center></td>
>         <td><center>b<sub>2</sub></center></td>
>     </tr>
>     <tr>
>         <td><center>a<sub>2</sub></center></td>
>         <td><center>b<sub>2</sub></center></td>
>     </tr>
> </table>

###### 4.除法

#### 五、SQL










