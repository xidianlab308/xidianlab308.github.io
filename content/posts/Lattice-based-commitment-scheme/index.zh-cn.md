---
title: Lattice based commitment scheme
date: 2025-05-13 19:55:54
draft: false
tags: "格密码"
author: "anonymous"

lightgallery: true

---

>本篇博客利用prompt工程撰写

# 格密码承诺方案： Ajtai , BDLOP 和 ADBLOP

在密码学领域，承诺方案 (Commitment Scheme) 扮演着至关重要的角色。它允许一方（承诺者）对某个值或声明进行承诺，同时保持该值的秘密性（隐藏性），并在稍后阶段向另一方（验证者）揭示该值（绑定性）。近年来，随着量子计算的兴起对传统公钥密码体系构成威胁，基于格的密码学 (Lattice-based Cryptography) 因其抗量子特性而受到广泛关注。本文将探讨几种基于格的承诺方案，特别是 Lantern 提出的结合了 Ajtai 和 BDLOP 方案优势的新型 ABDLOP 方案。

## 承诺方案的核心属性

一个安全的承诺方案通常需要满足两个基本属性：

1.  **隐藏性 (Hiding):** 承诺本身不会泄露关于承诺值的任何信息。
2.  **绑定性 (Binding):** 承诺者一旦做出承诺，就不能在揭示阶段改变承诺的值。

## Ajtai 承诺方案

Ajtai 承诺方案是一种经典的基于格的方案。其核心思想是利用格中的短向量问题 (Shortest Vector Problem, SVP) 或最近向量问题 (Closest Vector Problem, CVP) 的困难性。

在该方案中，承诺者想要承诺一个消息 $\mathbf{s}_1$。为此，他会选择一个随机向量 $\mathbf{s}_2$，其中 $\mathbf{s}_1$ 和 $\mathbf{s}_2$ 的范数（长度）都要求很小。承诺的计算方式如下：

$$
\mathbf{A}_1 \mathbf{s}_1 + \mathbf{A}_2 \mathbf{s}_2 = \mathbf{t}
$$

这里：
* $\mathbf{A}_1$ 和 $\mathbf{A}_2$ 是公开的矩阵。
* $\mathbf{s}_1$ 是要承诺的消息。
* $\mathbf{s}_2$ 是承诺者选择的随机值（也称为盲化因子）。
* $\mathbf{t}$ 是生成的承诺。

为了揭示承诺，承诺者需要公开 $\mathbf{s}_1$ 和 $\mathbf{s}_2$。验证者可以通过检查等式是否成立以及 $\mathbf{s}_1$ 和 $\mathbf{s}_2$ 是否确实是“小”向量来验证承诺。由于找到满足该等式的其他短向量对 $(\mathbf{s}_1', \mathbf{s}_2')$ 非常困难，因此该方案具有绑定性。同时，由于存在许多可能的 $\mathbf{s}_2$ 可以生成相同的 $\mathbf{t}$（对于不同的 $\mathbf{s}_1$），因此方案也具有隐藏性。

## BDLOP 承诺方案

BDLOP 承诺方案 ([BDL+18]) 是另一种重要的基于格的承诺方案。它允许承诺者对消息 $\mathbf{m}$ 进行承诺，并使用随机性 $\mathbf{s}$。其承诺形式如下：

$$
\left[\begin{array}{l}
\mathbf{A} \\
\mathbf{B}
\end{array}\right] \mathbf{s} + \left[\begin{array}{c}
\mathbf{0} \\
\mathbf{m}
\end{array}\right] = \left[\begin{array}{l}
\mathbf{t}_A \\
\mathbf{t}_B
\end{array}\right]
$$

这里：
* $\mathbf{A}$ 和 $\mathbf{B}$ 是公开的矩阵。
* $\mathbf{s}$ 是承诺者选择的随机向量。
* $\mathbf{m}$ 是要承诺的消息。
* $\mathbf{0}$ 是一个零向量。
* $\left[\begin{array}{l} \mathbf{t}_A \\ \mathbf{t}_B \end{array}\right]$ 是生成的承诺。

BDLOP 方案的一个有趣特性是它可以扩展到承诺多个消息。例如，如果除了 $\mathbf{m}$ 之外，还需要承诺另一个消息 $\mathbf{m}'$，可以使用公开的随机性 $\mathbf{B}'$ 来计算新的承诺部分：$\mathbf{B}' \mathbf{s} + \mathbf{m}' = \mathbf{t}_{B'}'$。那么，对 $(\mathbf{m}, \mathbf{m}')$ 的组合承诺就变成了：

$$
\left[\begin{array}{c}
\mathbf{A} \\
\mathbf{B} \\
\mathbf{B}'
\end{array}\right] \mathbf{s} + \left[\begin{array}{c}
\mathbf{0} \\
\mathbf{m} \\
\mathbf{m}'
\end{array}\right] = \left[\begin{array}{c}
\mathbf{t}_A \\
\mathbf{t}_B \\
\mathbf{t}_{B'}'
\end{array}\right]
$$

这种结构在需要对复杂数据结构进行承诺时非常有用。

## Lantern 的 ABDLOP 承诺方案：融合与提升

为了追求更高的效率和灵活性，Lantern 提出了一种名为 ABDLOP 的新型承诺方案。顾名思义，ABDLOP 旨在结合 Ajtai 和 BDLOP 方案的优点。

ABDLOP 方案的承诺形式如下：

$$
\left[\begin{array}{c}
\mathbf{A}_1 \\
\mathbf{0}
\end{array}\right] \mathbf{s}_1 + \left[\begin{array}{c}
\mathbf{A}_2 \\
\mathbf{B}
\end{array}\right] \mathbf{s}_2 + \left[\begin{array}{c}
\mathbf{0} \\
\mathbf{m}
\end{array}\right] = \left[\begin{array}{c}
\mathbf{t}_A \\
\mathbf{t}_B
\end{array}\right]
$$

这里：
* $\mathbf{A}_1, \mathbf{A}_2, \mathbf{B}$ 是公开的矩阵。
* $\mathbf{s}_1$ 可以被看作是 Ajtai 方案中的消息部分，具有范数较小的特性。
* $\mathbf{s}_2$ 可以被看作是 Ajtai 方案中的随机性部分，同时也扮演着 BDLOP 方案中随机性的角色，同样具有范数较小的特性。
* $\mathbf{m}$ 是要承诺的附加消息，类似于 BDLOP 方案中的消息。
* $\mathbf{0}$ 是零向量。
* $\left[\begin{array}{c} \mathbf{t}_A \\ \mathbf{t}_B \end{array}\right]$ 是生成的承诺。

在揭示阶段，承诺者需要提供 $\mathbf{s}_1$ 和 $\mathbf{s}_2$ 来打开承诺。

通过这种结构，ABDLOP 方案试图同时利用 Ajtai 方案中对短向量 $\mathbf{s}_1$ 的承诺能力，以及 BDLOP 方案中对附加消息 $\mathbf{m}$ 进行承诺的灵活性。这种融合可能在特定的应用场景下带来效率或功能上的优势。例如，$\mathbf{s}_1$ 可能代表一些核心的、需要强绑定性和隐藏性的秘密值，而 $\mathbf{m}$ 则可能是一些辅助数据。

## 结论

基于格的承诺方案是构建抗量子密码系统的重要基石。Ajtai 和 BDLOP 方案各自提供了独特的特性和优势。Lantern 提出的 ABDLOP 方案通过巧妙地结合这两种方案的元素，为设计更高效、更灵活的密码协议开辟了新的可能性。随着对基于格密码学的深入研究，我们可以期待未来出现更多创新的承诺方案，为数字安全领域提供更强大的保障。

---

**参考文献：**

* [Ajt96] Ajtai, M. (1996). Generating hard instances of lattice problems (extended abstract). In Proceedings of the twenty-eighth annual ACM symposium on Theory of computing (pp. 99-108).
* [BDL+18] Baum, C., Damgård, I., Lyubashevsky, V., Oechsner, S., & Peikert, C. (2018). Lattice-Based SNARGs and Their Application to Privacy-Preserving Computation. In Advances in Cryptology – ASIACRYPT 2018 (pp. 3-33). Springer. 
