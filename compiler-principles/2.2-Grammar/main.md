# 文法

## 文法的定义

文法（Grammar）是一个四元组 $G = (V_N, V_T, P, S)$，其中：

- $V_N$：非终结符集合（Nonterminal Symbols）
- $V_T$：终结符集合（Terminal Symbols），$V_N \cap V_T = \emptyset$
- $P$：产生式集合（Production Rules），形式为 $\alpha \rightarrow \beta$
- $S$：开始符号（Start Symbol），$S \in V_N$

### 产生式

产生式（Production）的形式为 $\alpha \rightarrow \beta$，其中 $\alpha \in (V_N \cup V_T)^+$，$\beta \in (V_N \cup V_T)^*$。

### 推导

若 $\alpha \rightarrow \beta \in P$，且 $\gamma = \delta\alpha\eta$，则 $\gamma \Rightarrow \delta\beta\eta$（一步推导）。

$\Rightarrow^*$ 表示零步或多步推导，$\Rightarrow^+$ 表示一步或多步推导。

### 句型和句子

- **句型**（Sentential Form）：$S \Rightarrow^* \alpha$，$\alpha$ 称为句型
- **句子**（Sentence）：$S \Rightarrow^* \alpha$ 且 $\alpha \in V_T^*$，$\alpha$ 称为句子
- **语言**（Language）：文法 $G$ 生成的语言 $L(G) = \{\omega \mid S \Rightarrow^* \omega, \omega \in V_T^*\}$

---

## 文法的分类

根据产生式的限制，Chomsky 将文法分为四类：

### 0型文法（无限制文法）

产生式形式：$\alpha \rightarrow \beta$，其中 $\alpha \in (V_N \cup V_T)^+$，$\beta \in (V_N \cup V_T)^*$，且 $|\alpha| \leq |\beta|$。

**特点**：对产生式无特殊限制（除长度限制外）。

### 1型文法（上下文有关文法 CSG）

产生式形式：$\alpha A \beta \rightarrow \alpha \gamma \beta$，其中 $A \in V_N$，$\alpha, \beta \in (V_N \cup V_T)^*$，$\gamma \in (V_N \cup V_T)^+$。

**特点**：替换 $A$ 时需要考虑上下文 $\alpha$ 和 $\beta$。

### 2型文法（上下文无关文法 CFG）

产生式形式：$A \rightarrow \alpha$，其中 $A \in V_N$，$\alpha \in (V_N \cup V_T)^*$。

**特点**：替换 $A$ 时不需要考虑上下文，是编译原理中最常用的文法类型。

**示例**：
$$
\begin{align}
E &\rightarrow E + T \mid T \\
T &\rightarrow T * F \mid F \\
F &\rightarrow (E) \mid id
\end{align}
$$

### 3型文法（正则文法 RG）

产生式形式：$A \rightarrow aB$ 或 $A \rightarrow a$，其中 $A, B \in V_N$，$a \in V_T$（右线性文法）。

或 $A \rightarrow Ba$ 或 $A \rightarrow a$（左线性文法）。

**特点**：产生式右部最多有一个非终结符，且必须位于最左或最右。

**示例**：
$$
\begin{align}
S &\rightarrow aA \mid b \\
A &\rightarrow aA \mid bA \mid a
\end{align}
$$

---

## 文法间的关系

![](./1.drawio.svg)

### 包含关系

- 3型文法 $\subset$ 2型文法 $\subset$ 1型文法 $\subset$ 0型文法
- 即：正则文法 $\subset$ 上下文无关文法 $\subset$ 上下文有关文法 $\subset$ 无限制文法

### 对应的语言类型

| 文法类型 | 语言类型 | 识别机器 |
|---------|---------|---------|
| 0型 | 递归可枚举语言 | 图灵机 |
| 1型 | 上下文有关语言 | 线性有界自动机 |
| 2型 | 上下文无关语言 | 下推自动机 |
| 3型 | 正则语言 | 有限自动机 |

---

## 上下文无关文法的性质

### 二义性

若存在一个句子有两棵不同的分析树，则该文法是二义性文法。

### 范式

- **Chomsky 范式**：产生式形式为 $A \rightarrow BC$ 或 $A \rightarrow a$
- **Greibach 范式**：产生式形式为 $A \rightarrow a\alpha$，其中 $a \in V_T$，$\alpha \in V_N^*$

### 递归

- **左递归**：$A \rightarrow A\alpha$
- **右递归**：$A \rightarrow \alpha A$
- **间接递归**：通过多个产生式形成递归
