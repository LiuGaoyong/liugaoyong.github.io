---
title: "计算化学方法分类与简介"
date: 2019-09-15T11:30:03+00:00
tags: ["Theory"]
author: "Me"
---

<img width = '300' height ='180' src ="https://qiniu.smitee.cn/images/2019-09-19/image-9CHjfVQn.png"/>

### 一、量子化学方法(QC)

#### 1、从头算(ab initio)

从头算量子化学方法是基于量子化学的计算化学方法。ab initio 最初由 Robert Parr 及其同事在量子化学中使用，包括 David Craig 在苯的激发态的半经验研究中。ab initio 最开始意味着“从第一原理开始”，这意味着从头算的唯一输入是基本物理常数。常见的 ab initio 电子结构方法有：

1. Hartree-Fock 方法

- Hartree–Fock (HF)
- 限制性开壳层 HF 方法 (ROHF)
- 非限制性 HF (UHF)

2. 后 Hartree-Fock 方法

- Møller-Plesset 微扰理论（MPn）
- 组态相互作用方法（CI）
- 耦合簇方法（CC）
- 二次组态相互作用方法（QCI）
- 量子化学复合方法

3. 多参考方法

- 多组态自洽场方法（MCSCF, 包括 CASSCF 和 RASSCF）
- 多参考态组态相互作用（MRCI）
- π 电子价态微扰理论（NEVPT）
- Complete active space perturbation theory（CASPTn）
- State universal multi-reference coupled-cluster theory（SUMR-CC）

#### 2、密度泛函理论(DFT)

密度泛函理论是一种研究多电子体系电子结构的量子力学方法，其核心思想为使用用电子密度取代波函数做为研究的基本量，大大降低体系的自变量个数，从而简化计算。密度泛函理论在物理和化学上都有广泛的应用，特别是用来研究分子和凝聚态的性质。

该理论起源于材料电子结构的 Thomas-Fermi 模型，但其理论基础首先在 Walter Kohn 和 Pierre Hohenberg 的两个 Hohenberg-Kohn 定理的中给予证明。H-K 第一定理证明了多电子系统的基态特性是由仅依赖于三个空间坐标的电子密度唯一确定的，它通过使用电子密度泛函，将具有 3N 个坐标的 N 电子多体问题简化到 3 个空间坐标。此定理已经扩展到含时薛定谔方程的求解过程中，以发展了含时密度泛函理论(TDDFT)，可用于描述激发态。H-K 第二定理定义了系统的能量泛函，并证明正确的基态电子密度使该泛函取最小。

#### 3、半经验量子化学方法(semi-empirical)

半经验量子化学方法基于 Hartree-Fock 方法形式，但做了许多近似并从经验数据中获得了一些参数。从 60 年代到 90 年代，它们在计算化学中非常重要，特别是对于处理大分子，其中没有近似的完整 Hartree-Fock 方法成本太高。经验参数的使用似乎允许将相关效应包含在方法中。

由于该方法是基于薛定谔方程的，包含了对电子结构的描述，故该方法是可以求得和电子结构相关的性质，包括过渡态。常见的半经验方法有 AM1，PM7 等。

### 二、分子动力学(MD)

分子动力学依靠计算机来模拟分子、原子体系的运动，并通过对分子、原子在一定时间内运动状态的模拟，从而以动态观点考察系统随时间演化的行为。分子、原子的轨迹通常是通过数值求解牛顿运动方程得到，势能通常可以由分子间相互作用势能函数、分子力学力场给出。对于考虑分子本身的量子效应的体系，往往采用波包近似处理或采用量子力学的费恩曼路径积分表述方式进行处理。
<img width = '300' height ='160' src ="https://upload.wikimedia.org/wikipedia/commons/f/f4/MD_water.gif"/>

### 三、蒙特卡洛方法(MC)

蒙特卡洛(法语：Monte-Carlo)是摩纳哥公国最著名的地方之一，其以豪华的赌场闻名于世。摩纳哥公国地处法国南部，除了靠地中海的南部海岸线之外，全境北、西、东三面皆由法国包围，主要是由摩纳哥旧城和随后建立起来的周遭地区组成。
![](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a3/Monaco-CIA_WFB_Map.png/300px-Monaco-CIA_WFB_Map.png)

蒙特卡洛方法是一种以概率统计理论为指导的数值计算方法，即使用随机数（或更常见的伪随机数）来解决很多计算问题的方法。该方法的执行依赖于计算机技术的发展。

使用蒙特卡罗方法进行分子模拟计算是按照以下步骤进行的：

1. 使用随机数生成器产生一个随机的分子构型。
2. 对此分子构型的其中粒子坐标做无规则的改变，产生一个新的分子构型。
3. 计算新的分子构型的能量。
4. 比较新的分子构型与改变前的分子构型的能量变化，判断是否接受该构型。
   A. 若新的分子构型能量低于原分子构型的能量，则接受新的构型，使用这个构型重复再做下一次迭代。B.若新的分子构型能量高于原分子构型的能量，则计算玻尔兹曼因子，并产生一个随机数。B-1.若这个随机数大于所计算出的玻尔兹曼因子，则放弃这个构型，重新计算。B-2.若这个随机数小于所计算出的玻尔兹曼因子，则接受这个构型，使用这个构型重复再做下一次迭代。
5. 如此进行迭代计算，直至最后搜索出低于所给能量条件的分子构型结束。

<img width = '300' height ='300' src ="https://upload.wikimedia.org/wikipedia/commons/thumb/8/84/Pi_30K.gif/220px-Pi_30K.gif"/>

### 四、分子力学(MM)

分子力学是将分子看成通过弹簧连接的球模型，遵照经典力学规律，进行计算的模型，又称力场(FF)方法，常见的力场方法有 Amber、CHARMM、。该模型不考虑电子结构，因此，原则上，一切与电子相关的性质都不能通过该方法得到，包括过渡态(TS)的性质。但是近些年随着一些反应力场的出现，也可以计算某些化学反应的过渡态，比如比较有名的[ReaxFF](https://pubs.acs.org/doi/10.1021/jp004368u)，可以用于计算烃类化合物的反应性质，目前该力场已经被包含在 LAMMPS、ADF 和 PuReMD 等软件包中。

值得注意的是，一套力场往往只针对一类或几类分子的计算，用于计算不在其适用范围的分子会出现较大的偏差。且不同的力场之间参数并不能互用。详见[力场方法]()

### References：

1. https://en.wikipedia.org/wiki/Computational_chemistry
1. https://en.wikipedia.org/wiki/Ab_initio_quantum_chemistry_methods
1. https://en.wikipedia.org/wiki/Molecular_dynamics
1. https://zh.wikipedia.org/zh-hans/%E8%92%99%E5%9C%B0%E5%8D%A1%E7%BE%85%E6%96%B9%E6%B3%95
1. https://zh.wikipedia.org/wiki/%E8%92%99%E5%9C%B0%E5%8D%A1%E7%BE%85%E6%96%B9%E6%B3%95
1. https://baike.baidu.com/item/%E5%88%86%E5%AD%90%E5%8A%9B%E5%AD%A6
1. https://zh.wikipedia.org/wiki/%E5%8F%8D%E5%BA%94%E5%8A%9B%E5%9C%BA
1. https://zh.wikipedia.org/wiki/%E5%88%86%E5%AD%90%E5%8A%9B%E5%AD%A6
1. https://jerkwin.github.io/2015/12/09/%E5%8A%9B%E5%9C%BA%E4%B8%8E%E6%8B%93%E6%89%91%E4%B9%8B%E4%B8%80-%E5%8A%9B%E5%9C%BA%E7%9A%84%E6%A6%82%E5%BF%B5%E5%88%86%E7%B1%BB%E5%8F%8A%E5%8F%91%E5%B1%95%E6%96%B9%E6%B3%95/
1. [J. Phys. Chem. A 2001, 105, 41, 9396-9409](https://pubs.acs.org/doi/10.1021/jp004368u)
