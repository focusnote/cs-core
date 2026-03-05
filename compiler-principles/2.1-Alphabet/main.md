# 字母表

## 字母表的定义

字母表（Alphabet）是一个非空的有穷集合，其元素称为符号（Symbol）。

通常用大写希腊字母 $\Sigma$ 表示字母表。

### 示例

- 二进制字母表：$\Sigma = \{0, 1\}$
- 英文字母表：$\Sigma = \{a, b, c, ..., z\}$
- ASCII 字符集：$\Sigma = \{所有ASCII字符\}$

---

## 字符串

### 定义

字符串（String）是由字母表中的符号组成的有限序列。

字符串 $\omega$ 的长度记作 $|\omega|$，表示其中符号的个数。

### 特殊字符串

- **空串**（Empty String）：不包含任何符号的字符串，记作 $\varepsilon$ 或 $\lambda$
- $|\varepsilon| = 0$

### 字符串的运算

#### 连接（Concatenation）

字符串 $\alpha$ 和 $\beta$ 的连接记作 $\alpha\beta$，是将 $\beta$ 接在 $\alpha$ 后面。

**性质**：
- $|\alpha\beta| = |\alpha| + |\beta|$
- $\varepsilon\alpha = \alpha\varepsilon = \alpha$

#### 幂运算（Power）

字符串 $\alpha$ 的 $n$ 次幂记作 $\alpha^n$：

$$
\alpha^n = \underbrace{\alpha\alpha\cdots\alpha}_{n个}
$$

**规定**：$\alpha^0 = \varepsilon$

#### 子串（Substring）

字符串 $\alpha$ 的子串是从 $\alpha$ 中删除零个或多个符号后得到的字符串。

#### 前缀和后缀

- **前缀**（Prefix）：从字符串开头开始的子串
- **后缀**（Suffix）：到字符串结尾的子串

---

## 语言

### 定义

语言（Language）是字母表 $\Sigma$ 上字符串的集合，即 $L \subseteq \Sigma^*$。

其中 $\Sigma^*$ 表示字母表 $\Sigma$ 上所有字符串（包括空串）的集合。

### $\Sigma^*$ 和 $\Sigma^+$

- $\Sigma^* = \{\omega \mid \omega \text{ 是 }\Sigma\text{ 上的字符串}\}$
- $\Sigma^+ = \Sigma^* - \{\varepsilon\} = \{\omega \mid \omega \text{ 是 }\Sigma\text{ 上的非空字符串}\}$

### 语言的运算

#### 并（Union）

$L_1 \cup L_2 = \{\omega \mid \omega \in L_1 \text{ 或 } \omega \in L_2\}$

#### 交（Intersection）

$L_1 \cap L_2 = \{\omega \mid \omega \in L_1 \text{ 且 } \omega \in L_2\}$

#### 差（Difference）

$L_1 - L_2 = \{\omega \mid \omega \in L_1 \text{ 且 } \omega \notin L_2\}$

#### 连接（Concatenation）

$L_1L_2 = \{\alpha\beta \mid \alpha \in L_1, \beta \in L_2\}$

#### Kleene 闭包（Kleene Closure）

$L^* = \bigcup_{i=0}^{\infty} L^i = L^0 \cup L^1 \cup L^2 \cup \cdots$

其中 $L^0 = \{\varepsilon\}$，$L^{i+1} = L^iL$

#### 正闭包（Positive Closure）

$L^+ = \bigcup_{i=1}^{\infty} L^i = L^1 \cup L^2 \cup L^3 \cup \cdots = LL^*$

### 语言的性质

- $\emptyset^* = \{\varepsilon\}$
- $\{\varepsilon\}^* = \{\varepsilon\}$
- $L^* = L^+ \cup \{\varepsilon\}$
- $L^+ = LL^* = L^*L$

---

## 示例

设 $\Sigma = \{a, b\}$：

| 概念 | 示例 |
|------|------|
| 字母表 | $\Sigma = \{a, b\}$ |
| 字符串 | $a, b, aa, ab, ba, bb, aaa, \varepsilon$ |
| 字符串长度 | $|a| = 1, |ab| = 2, |\varepsilon| = 0$ |
| 字符串连接 | $ab \cdot ba = abba$ |
| 字符串幂 | $a^2 = aa, a^0 = \varepsilon$ |
| $\Sigma^*$ | $\{\varepsilon, a, b, aa, ab, ba, bb, aaa, \dots\}$ |
| $\Sigma^+$ | $\{a, b, aa, ab, ba, bb, aaa, \dots\}$ |
| 语言 | $L = \{a^n b^n \mid n \geq 0\}$ |
