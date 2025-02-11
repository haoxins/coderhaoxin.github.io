---
title: 量子计算和计算复杂性
description: 雨横风狂三月暮, 门掩黄昏, 无计留春住. 泪眼问花花不语, 乱红飞过秋千去.
date: 2021-07-16
---

* [Shtetl-Optimized](https://www.scottaaronson.com)
  - The Blog of Scott Aaronson
  - 哇喔, 原来我早先就收藏了作者的博客
  - https://scottaaronson.blog
  - https://www.scottaaronson.com/papers/

------------------

* [PHYS771 Quantum Computing Since Democritus](https://www.scottaaronson.com/democritus/)

------------------

* [量子计算公开课](https://book.douban.com/subject/35467917/)
  - 副标题: 从德谟克利特, 计算复杂性到自由意志
  - 原作名: Quantum Computing since Democritus
  - 网络书评: 自费曼以来, 还没有谁的公开课能如此精彩
  - `2021`年`ACM计算奖`得主
  - 标题其实和内容不是很匹配, __应改为__: `计算复杂性: 从经典计算到量子计算`

* [阿列夫数: Aleph number](https://en.wikipedia.org/wiki/Aleph_number)

```
人们会好奇这本书的目标受众究竟是哪类人群.
一方面, 作为一本科普读物, 它有点儿深奥.
就像罗杰·彭罗斯的 "通向实在之路: 宇宙法则的完全指南",
这本书不是写给那些畏惧数学的人看的.
一位好奇的门外汉确实可以从这本书中学到很多,
但他将不得不跳过一些难懂的部分.
因此, 如果你只能消化那些已经把科学仔细剔除干净的"科普读物",
那么你最好找别的书看.

另一方面, 这本书也不适合作为教科书或参考书,
因为它的内容太过广泛, 风格太过随意和充满个人趣味.
确实, 它包含定理, 证明和练习,
并且涵盖了多得惊人的领域的基础知识:
逻辑, 集合论, 可计算性, 复杂性, 密码系统,
量子信息, 计算学习理论, 等等. 除了这些基础知识,
这本书还包含相当多的涉及量子复杂性理论的内容
(比如, 关于量子证明和量子建议), 然而据我所知,
这些内容是首次在这里以图书的形式给出.
但不得不说, 这本书在不同话题之间切换得太快了,
以至于它无法成为对任何一个话题的权威讨论.
```

```
所以, 这本书是要卖给那些实际上连第 1 章都看不完,
却想在咖啡馆的桌上摆一本书来装门面的人吗?
唯一我能想到的其他可能性是, 其实, 存在一类需求未被满足的受众,
他们想读的既不是 "科普" 读物, 也不是 "学术" 著作,
而是从研究者带有严重倾向性的视角出发,
使用他们在楼道里与其他领域的同事交谈时所用的语言来描述某个科研领域的书.
也许, 除了这些同事, 这类假想的 "需求未被满足的受众"
还包括早慧的高中生, 或者曾很享受大学时代的理论课程,
而现在想了解最新研究进展的计算机程序员和工程师.
```

* 如果量子力学不是通常意义上的物理学
  (如果它不是关于物质, 能量, 波或粒子的),
  那它到底是关于什么的呢?
  在我看来, 它是关于
  **信息**, **概率**, **可观测量**,
  以及它们之间的关系的.

```
正如我们可以把宗教分成一神论和多神论, 我们也可以通过其对
"将你自己放入相干叠加中" 议题的站队来对量子力学的诠释加以分类.

在一边, 我们有一些诠释 -- 哥本哈根诠释, 量子贝叶斯以及认识论,
它们积极地把这个议题扫人地毯底下. 在这些诠释中,
这边是你的量子系统, 那边是你的测量设备, 两者之间有明确的界线.
确实, 这条界线在不同实验中会有变化, 但对于任何给定的实验,
它必须存在于某处. 在原则上, 你甚至可以想象,
将其他人放在量子力学的一侧, 而将你自己始终放在经典力学的一侧.

为什么? 因为量子状态只是你的知识的一种表象, 而你自己, 根据定义,
是一个经典的存在. 但如果你希望将量子力学运用于整个宇宙,
包括你自己, 又会发生什么? 根据认识论的诠释, 答案就是你别问这种问题!
顺便一提, 这是尼尔斯·玻尔最喜爱的哲学回应, 他的撒手锏是:
"你不能问这样一个问题!"

在另一边, 我们也有一些诠释 -- 多世界诠释, 玻姆力学等,
它们确实以不同方法试着让"将你自己放人相干叠加中"说得通.
```

## 集合

* **一阶逻辑规则**
  - 这些规则关注的都是如何构造出有效的语句 -- "有效",
    不正式地说, 意指`"恒真"` (对于变量的所有可能设定均为真);
  - 不过, 我们暂且可以只把它视为特定符号串的一种组合性质.

---

* 命题恒真式 (propositional tautology):
  - `A`或非`A`, 非 (`A`与非`A`) 等均有效.
* 假言推理 (modusponen):
  - 如果`A`有效, 并且`A`蕴涵`B`有效, 则`B`有效.
* 等词规则 (equalityrule):
  - `x=x` 且 `x=y` 蕴涵 `y=x`,
  - `x=y` 且 `y=z` 蕴涵 `x=z`,
  - 以及 `x=y` 蕴涵 `f(x)=f(y)` 均有效.
* 变量改变 (change of variable):
  - 改变变量名不影响陈述的有效性.
* 量词消去 (quantifier elimination):
  - 如果对于任意`x`, `A(x)`有效, 则对于任意`y`, `A(y)`有效.
* 量词引入 (quantifier addition):
  - 如果`y`是无约束变量时, `A(y)`有效, 则对于任意`x`, `A(x)`有效.
* 量词规则 (quantifierrule):
  - 如果非 (对于任意`x`, `A(x)`) 有效, 则存在`x`使得非`(A(x))`有效.

* 比如, 下面是用一阶逻辑语言写出的关于非负整数的皮亚诺公理.
  - 在其中 `S(x)` 为后继函数, 也就是说,
    `S(x)=x+1`, 并且我假设函数已被定义.

* 关于非负整数的皮亚诺公理
  - __零的存在性__:
  - 存在一个 `z`, 使得对于任意 `x`, `S(x)`
    不等于 `z` (这个 `z` 便被当作 `0`).
  - __每个整数至多有一个前驱数__:
  - 对于任意的 `x` 和 `y`,
    若 `S(x)=S(y)`, 则 `x=y`.

---

* 恰恰因为这一点, 我不认为我们可以通过公理和形式逻辑为算术奠定更坚实的基础.
  如果你还不同意 `1+1=2`, 那么,
  即使你耗尽毕生研究数理逻辑也不会把这弄得更清楚.
* 但这些东西依然非常有意思, 原因至少有三.
  - (1) 一旦我们讨论的不是整数, 而是不同大小的`"无穷大"`,
    情况就会发生变化. 届时, 写出公理并做出它们的推论,
    几乎是我们能做的全部.
  - (2) 一旦将一切形式化, 我们便可以利用计算机进行推理.
  - 前提 1: 对于任意 `x`, 若 `A(x)` 为真, 则 `B(x)` 为真.
  - 前提 2: 存在 `x`, 使得 `A(x)` 为真.
  - 结论: 存在 `x`, 使得 `B(x)` 为真.
  - 你一定看出来了. 这里的要点是,
    从前提推出结论的过程完全是一个句法运算,
    它不要求对命题的含义有任何理解.
  - (3) 除了让计算机为我们寻找证明,
    我们还可以把这些证明本身视为数学对象,
    从而开始涉足元数学.

---

* **集合论的公理**

* 这些公理均涉及被称为`"集合"`的对象, 以及集合之间的关系,
  称为`"成员关系"`或`"包含关系"`,
  - 用符号
    $$ \in $$
    表示.
  - 对集合的任一操作最终都将通过包含关系定义.
* **空集公理**: 存在一个空集.
  - 也就是说, 存在一个集合 `x`, 对于 `x`, 不存在 `y` 使得
    $$ y \in x $$.
* **外延公理**: 如果两个集合包含同样的元素, 则两者相等.
  - 也就是说, 对于任意的 `x` 和 `y`, 如果
    $$ z \in x $$,
    当且仅当对于任意的 `z`,
    $$ z \in y $$
    为真, 则 `x = y`.
* **无序对公理**: 对于任意的集合 `x` 和 `y`, 存在集合
  `z = {x, y}`.
  - 也就是说, 当且仅当 `w = x` 或 `w = y`,
    存在 `z` 使得对于任意的 `w`,
    $$ w \in z $$.
* **并集公理**: 对于任意集合 `x`, 存在一个集合等于 `x`
  中所有集合的并集.
* **无穷公理**: 存在一个集合 `x` 包含空集, 且对于任意的
  $$ y \in x $$,
  `x` 包含 `{y}`.
  - 为什么这个 `x` 一定有无穷多元素?
* **幂集公理**: 对于任意集合 `x`, 存在一个由 `x`
  的所有子集构成的集合.
* **替代公理**:
  - 它事实上是无穷多个公理, 对于每个将集合映射为集合的函数
    `A` 都有一个相应的公理:
  - 对于任意集合 `x`, 存在集合
    $$ z = \{ A(y) | y \in x \} $$,
  - 即 `z` 是将 `A` 作用在 `x` 上所有元素的结果.
  - 从技术上讲, 我们还需要定义`"从集合到集合的映射"`是什么意思,
    这可以做到, 但我不打算在这里展开.
* **基础公理**: 所有非空集合 `x` 均有这样一个元素 `y`,
  使得对于任意的 `z`,
  $$ z \notin x $$
  或
  $$ z \notin y $$.
  - 这是一个技术性公理, 旨在排除像
    `{ { { { ... } } } }`
    这样的集合.
* 这些公理称为策梅洛-弗兰克尔公理, 是几乎所有数学的基础.
  所以我觉得你一辈子怎么也应该见它们一次.

---

* 格奥尔格·康托尔 (`1845-1918`) 对于人类知识的重大贡献之一.
  他说, 当且仅当两个集合的元素有一一对应关系时,
  它们具有相同的**基数**.
  - 就是这样. 如果不管你怎样尝试将这些元素配对,
    其中一个集合总有元素剩下, 则这个集合更大.
* 集合有哪些可能的基数呢? 当然, 有些是有限的集合,
  它们的基数是一个自然数.
* 然后是第一个无穷基数, 整数的基数,
  - 康托尔称之为
    $$ X $$.
* 有理数具有同样的基数
  $$ N $$,
  这个事实也可以被表述为有理数是可数的,
  即它们可以与整数一一对应.
  - 换言之, 我们可以制作出一个无限列表,
    使得每个有理数最终都会出现在这个列表中.
* 我们该如何证明有理数可数呢? 你以前没有见过? 噢, 好吧.
  - 首先, 列出 `0`. 然后列出所有分子和分母的绝对值之和为 `2` 的有理数.
  - 接着, 列出分子和分母的绝对值之和为 `3` 的有理数, 以此类推.
  - 显然, 每个有理数最终都会出现在该列表中.
  - 因此, 它们仅仅是可数无穷多的. **证毕**.
* 但康托尔的最大贡献是表明**并非每个无穷均是可数的**. 比如,
  实数的无穷要比整数的无穷大.
  - 更一般地, 正如存在无穷多个数, 同样存在无穷多种`"无穷"`.
  - 你也没见过对它的证明?
* 没关系. 假设有一个无穷集 `A`. 我们将展示如何构造另一个无穷集 `B`,
  使得 `B` 比 `A` 更大.
  - 这里的 `B` 只需是 `A` 所有子集的集合,
    而根据**幂集公理**, 它必定存在.
* 我们如何知道 `B` 比 `A` 大? 假设我们可以将 `A` 中的每个元素
  $$ a \in A $$
  与 `B` 中的每个元素
  $$ f(a) \in B $$
  一一配对,
  使得 `B` 中没有剩余元素. 然后, 我们可以定义一个新的子集
  $$ S \subseteq A $$,
  它由所有不包含在 `f(a)` 之中的 `a` 组成.
* 注意, `S` 不可能已经与 `A` 中的任意元素 `a` 一一配对,
  否则便会有当且仅当 `a` 不属于 `f(a)` 时 `a` 属于 `f(a)`,
  出现矛盾.
  - 因此, `B` 要比 `A` 大, 并且我们从一个较小的无穷出发,
    得到了一个较大的无穷.
* 这无疑是数学中最伟大的四五个证明之一, 再一次地,
  你一辈子怎么也应该见它们一次.

## 哥德尔, 图灵和他们的小伙伴

* 不完备性定理说的是, 给定任意自洽的, 可计算的公理集,
  存在关于整数的真命题, 它不可能通过这些公理被证明.
  在这里, `"自洽"`意味着你不可能推出矛盾,
  而`"可计算"`意味着要么有有限个公理, 要么如果有无穷个公理,
  那么至少存在一个算法可以生成所有这些公理.
  - 如果没有可计算的要求,
    那么我们可以简单地让我们的`"公理集"`由所有关于整数的真命题组成.
  - 在实践中, 这可不是一个太有用的公理集.
* 但稍等一下! 完备性定理说, 任何由这些公理推出的命题都能为这些公理所证明,
  这难道不是与不完备性定理相矛盾吗?
  - 先记着这个问题, 我们会在之后把它搞清楚.
* 不过首先, 让我们看看不完备性定理是如何证明的. 人们总是说,
  不完备性定理的证明是一项技术杰作, 它要用到`30`页纸,
  它要用到一个涉及质数的巧妙构造, 如此等等. 真是令人难以置信,
  在哥德尔给出证明后`80`多年, 它在数学课上仍旧是以如此形式呈现的.
* 好, 要不要我来告诉你一个秘密? 不完备性定理的证明大约需要两行 -- 几近平凡.
  但我要提醒一下, 为了给出两行的证明, 你首先需要计算机的概念.
* 当我还在初中的时候, 我有一位非常擅长数学但不太擅长编程的朋友.
  他想用数组写一个程序, 但他并不知道什么是数组. 那么他是怎么做的呢?
* 他把数组的每个元素与一个独特的质数一一对应, 然后他把这些质数都乘了起来;
  这样每当他想要从这个数组中读出一些东西时, 他就对这个乘积进行质因数分解.
  - 要是他在一台量子计算机上编程, 这种做法可能也就没有那么糟糕!
  - 无论如何, 我朋友所做的, 基本上也就是哥德尔所做的.
    他打造了一位高明的黑客, 以便不通过编程来写程序.

---

* 这个机器能做什么? 显然, 它必须能够从纸带上读取符号并根据指令修改它们.
  为简单起见, 假设这个机器每次只读一个符号. 在这种情况下, 它最好能前后移动.
  要是这个机器在得到结果后便能停机, 那自然也是极好的.
* 那么在任意时候, 这个机器如何决定要做些什么呢? 在图灵看来,
  这应该只取决于两部分信息:
  - (1) 目前正在读取的符号, 以及
  - (2) 机器目前的`"内部构形"`或`"状态"`.
* 根据它的内部状态以及目前读取的符号, 这个机器应该
  - (1) 在目前的方格中写下一个新的符号, 覆盖那里原先的符号,
  - (2) 向前或向后移动一格, 并
  - (3) 转变到一个新的状态或者停机.
* 最后, 由于我们想让这个机器在物理上是可实现的,
  因此可能的内部状态数目应该是有限的. 以上就是它仅有的要求.
* 图灵的第一个结论是, 存在一种`"通用"`图灵机,
  它能够模拟任何其他通过纸带上的符号描述出来的机器.
  - 也就是说, __存在通用的可编程计算机__.

---

* 很多著名的数学问题. 比如, 哥德巴赫猜想
  - 任何大于 `2` 的偶数均可以写成两个质数的和.
* 现在, 我们可以简单地写一个程序, 验证 `4`, `6`, `8` 等,
  并且它只有在发现这样一个数不能写成两个质数之和时才停机.
  - 这样, 判断这个程序是否停机与判断哥德巴赫猜想是否成立便是等价的.
* 但我们能够证明这种解决停机问题的程序不存在吗? 这正是图灵所做的.
  他的关键思路不是去尝试分析这样一个程序的内部动态过程 (假设它存在的话).
* 相反, 他利用反证法假设这样的程序 `P` 存在.
  然后, 我们可以修改 `P`, 得到一个新的程序 `P'`, 使得用另一个程序 `Q`
  作为输入, `P'`
  - (1) 要么会一直运行下去, 如果用 `Q` 的自身代码作为输入, `Q` 会停机;
  - (2) 要么会停机, 如果用 `Q` 的自身代码作为输入, `Q` 会一直运行下去.
* 现在, 我们用 `P'` 的自身代码作为输入. 根据上述条件,
  - 如果 `P'` 会停机, 那么它会一直运行下去;
  - 而如果它会一直运行下去, 那么它会停机.
  - 因此, `P'` (及由此可得 `P`) 一开始就不可能存在.
* 正如我之前所说, 一旦你有了图灵的结论,
  哥德尔的结论便作为额外奖励自然蹦了出来.
  为什么?
  - 假设不完备性定理是错的. 也就是说,
    存在一个自洽的, 可计算的证明体系 `F`,
    据此任何关于整数的命题均可以被证明对或错.
  - 那么给定一个计算机程序, 我们就可以简单地在 `F` 中搜索每一个可能的证明,
    直到我们找到一个表明这个程序会停机的证明, 或者找到一个表明它不会停机的证明.
  - 这是可能的, 因为表明一个特定计算机程序会停机的命题,
    终究只是一个关于整数的命题. 但这将给出一个解决停机问题的算法,
    而我们已经知道, 这是不可能的.
  - 因此, `F` 不可能存在.

---

* 唯一可能的结论是, 如果 `F` 是自洽的, 则 `F` 不能够证明自身的自洽性.
  这个结论有时候被称为**哥德尔第二不完备性定理**.
* 第二不完备性定理确认了我们可能早该预料到的结论:
  - __任何自以为能够证明自身自洽性的数学理论根本没有丝毫自洽性可言!__
* 如果我们想要证明一个理论 `F` 是自洽的, 那么我们只能在一个更强大的理论中去证明
  - 一个平凡的例子是 `F + Con(F)`, 即理论 `F` 加上声明 `F` 是自洽的公理.
  - 但我们又如何知道 `F + Con(F)` 本身是自洽的呢?
  - 好吧, 我们只能用一个更强大的理论
    `F + Con(F) + Con(F + Con(F))`
    去证明, ..., 无穷无尽.
  - 事实上, 它甚至超越了无穷, 成为可数序数.
* 再举一个具体的例子. 第二不完备性定理告诉我们,
  与整数有关的流传最广的公理体系 -- 皮亚诺算术, 不能证明自身的自洽性.
* 或者用符号表述: `PA` 不能证明 `Con(PA)`.
  - 如果我们试图去证明 `Con(PA)`, 就需要一个更强大的公理体系,
    比如 `ZF` (集合论的策梅洛-弗兰克尔公理).

---

* 我之前承诺过要解释为什么不完备性定理与完备性定理不矛盾.
  对此, 最简单的方法可能还是举例. 考虑一个`"自暴自弃的理论"`,
  `PA + 非(Con(PA))`, 也就是皮亚诺算术加上一个声明自身不自洽的断言.
  - 我们知道, 如果 `PA` 是自洽的, 那么这个奇怪的理论必定也是自洽的.
    不然的话, `PA` 就可以证明自身的不自洽性,
* 而这是不完备性定理所不允许的.
  而根据完备性定理, `PA + 非(Con(PA))` 必定有一个模型.
  - 但这个模型可能长什么样子?
  - 特别是, 在这个模型中, 如果你只想找到表明 `PA` 是不自洽的证明,
    结果会发生什么?
* 让我来告诉你会发生什么: 公理会告诉你,
  表明 `PA` 是不自洽的证明可被编码为一个正整数.
  - 然后你就会问: "但 `X` 又是什么呢?"
  - 公理会回答: "`X` 就是 `X`."
  - 然后你会问: "作为一个一般的正整数, `X` 究竟是什么?"
* 如此这般下去. 公理会一直编造一些假想数来满足你的要求,
  而通过假设 `PA` 本身是自洽的, 你将永远无法从它们那里推出不自洽.
* 完备性定理的要点在于公理编造的这些假想数的整个无穷集将会构成
  `PA` 的一个模型
  - 并且不是一般的模型 (如一般的正整数)!
* 如果我们坚持要讨论一般的模型,
  那我们就从`完备性定理`的论域切换到了`不完备性定理`的论域.
* 你还记得先前那个思考题吗?
  问题是: 是否存在这样一个定理,
  你只有将`"它可以被证明"`设为一个公理,
  才能证明它?
  - 换句话说, `"相信自己"`在数学上有用吗?
* 现在我们可以回答这个问题了.

---

* 如果一个命题可以通过将`"它可以被证明"`设为一个公理而得到证明,
  那么它也可以通过不假设这样的公理而得到证明.
  这个结论被称为**勒布定理**.

* 还记得之前我们讨论过的选择公理和连续统假设吗?
  - 它们是关于连续统的很自然的命题, 而由于连续统是一个如此良定义的数学实体,
    因此它们必定显然要么为真, 要么为假. 那么如何确定它们的真假呢?
  - 哥德尔在 `1939` 年证明了, 假设选择公理 (`AC`) 或连续统假设 (`CH`) 的真假,
    不会导致任何不自洽性.
  - 换言之, 如果理论 `ZF + AC` 或 `ZF + CH` 不自洽,
    那只能是因为 `ZF` 本身是不自洽的.
* 这里引发了一个显而易见的问题: 我们能否做到假设 `AC` 和 `CH` 都为假,
  并保持自洽性?
* 哥德尔对此想了很久, 但终究没能回答. 最后, 保罗·科恩在 `1963`
  年给出了肯定的回答, 他借助了一种被称为`"力迫法"`的新技术.
  - 为此, 他成为唯一位因集合论和数学基础而获得菲尔兹奖的数学家.
* 因此, 我们现在知道了, 一般的数学公理决定不了选择公理或连续统假设的真假.
  你可以自由选择相信两者都成立, 或两者都不成立, 或一个成立而另一个不成立,
  而不用担心会出现矛盾.
  - 事实上, 直到今天, 数学家对此依然各执一词,
    并给出了许多有趣的支持或反对的论证.

---

* 让我最后用一个可能有点儿出人意料的观察作结:
  `AC` 和 `CH` 相对于 `ZF` 的独立性本身是皮亚诺算术的一个定理.
* 因为哥德尔和科恩的自洽的理论归根结底是一系列摆弄一阶逻辑语句的命题
  - 它们在原则上可以被直接证明, 而无须考虑这些语句旨在描述的超限集.
  - 在实践中, 将这些语句组合起来是极其复杂的, 而科恩也说过,
    仅是尝试从有限组合的角度去考虑这些问题是没有出路的.
    但我们知道在理论上是可以这样做的.
  - 在我看来, 这很好地说明了整件事背后的一个核心哲学问题:
    我们真的是在谈论连续统, 还是只是在谈论那些谈论连续统的符号的有限序列?

## 古复杂性

* 当然, 量子力学得名自一个事实: 在这个理论中, 很多可观测量,
  比如能级, 是离散的, 即`"量子化"`的.
* 而考虑到计算机科学家反对量子计算的原因之一是, 在他们看来,
  这是一个连续的计算模型, 这看上去不无悖论.
* 我对此的观点是, 就像经典概率论,
  量子力学应该被视为某种`"介于"`连续和离散之间的理论.
  - 在这里, 我假设希尔伯特空间或概率空间是有限维的.
* 我的意思是, 尽管存在连续的参数 (分别是概率或概率幅)
  但这些参数不是直接可观察的, 而这起到了`"屏蔽"`作用,
  将我们挡在了选择公理和连续统假设的奇异世界之外.
* 我们不需要一个细致的物理学理论告诉我们,
  诸如概率幅是有理的还是无理的, 概率幅比
  $$ \aleph_{1} $$
  多还是少之类的问题在物理上是没有意义的.
* 这可从以下事实直接推得: 如果我们想要确切知道一个概率幅,
  那么 (即便假设测量没有错误) 我们将需要测量合适的量子态无穷多次!

---

* 不管怎样, 如果给定问题 `B` 的一个谕示,
  问题 `A` 即可由一个图灵机解决,
  那么我们称问题 `A` 图灵可归约 (Turing reducible) 到问题 `B`.
  - 换句话说, "A 不比 B 难":
  - 如果我们有一个假想的设备能够解决 `B`, 那我们也能够解决 `A`.
* 如果两个问题互相图灵可归约, 我们就称两者是图灵等价的
  (Turing equivalent).
* 因此, 比如,
  一个命题能否从集合论公理中得到证明的问题与停机问题就是图灵等价的.

---

* 现在, 图灵度 (Turing degree) 是指对于某个给定问题,
  所有与之图灵等价的问题的集合.
  - 图灵度有什么例子? 其实我们已经见过两个例子了:
  - (1) 可计算问题的集合, 以及
  - (2) 与停机问题图灵等价的问题的集合.
  - 说这两者的图灵度不相等也就是以另一种方式说停机问题不可解.
* 有比这两者更高的图灵度吗? 换句话说, 有什么问题比停机问题更难,
  它即便借助停机问题的谕示也解决不了?
  - 好吧, 考虑下述`"超级停机问题"`:
  - 给定一个拥有停机问题谕示的图灵机, 然后问它是否会停机.
    我们能够证明即便拥有一般停机问题的谕示,
    这个超级停机问题仍然解决不了吗?
  - 是的, 我们可以! 我们只需拿出图灵对于停机问题不可解的原始证明,
    然后`"进行升级"`, 给所有机器都配上一个停机问题的谕示.
    证明的每一步都与原来的一模一样,
    这时我们称这个证明`"相对化"` (relativize) 了.

## P, NP 和它们的小伙伴

* `1967` 年有一个结论, 称为**布卢姆加速定理**,
  它指出, 确实存在一些不会有最快算法的问题.
  不仅如此, 还存在这样一个问题 `P`, 使得对于每一个函数 `f`,
  如果 `P` 有一个 `O(f(n))` 的算法,
  则它还有一个 `O(log f(n))` 的算法!
* 让我们来看看这是如何做到的. 令 `t(n)` 为复杂性上界.
  我们的目标是定义一个从整数到 `{0, 1}` 的函数 `f`,
  使得对于任何整数 `i`, 如果 `f` 可以在 `O(t(n))` 步内算出,
  则它也可以在 `O(t(n - i))` 步内算出. 让 `t` 增长得足够快,
  我们便可以得到一个想要多快就有多快的加速:
  - 比如, 如果设
    $$ t(n) := 2^{n (n - 1)} $$,
    则显然有
    $$ t(n - 1) = O(\log{t(n)}) $$.
* 令
  $$ M_1, M_2, M_3, ... $$
  为图灵机的一个枚举. 然后令
  $$ S_i = \{ M_1, ..., M_i \} $$
  为由前 `i` 个图灵机组成的集合.
* 然后我们这样做: 给定一个整数 `n` 作为输入,
  让 `i` 从 `1` 到 `n` 进行循环.
  在第 `i` 步迭代中, 我们模拟在
  $$ S_i $$
  中且还没有在第 `1` 到第 `i - 1` 步被`"移除"`的每一个图灵机.
  - 如果这些机器在至多 `t(n - i)` 步内都没有停机,
    则令 `f(i)=0`.
  - 否则, 令
    $$ M_j $$
    为第一个在至多 `t(n - i)` 步内停机的图灵机.
  - 然后如果
    $$ M_j $$
    输出 `0`, 我们就定义 `f(i)` 为 `1`; 如果
    $$ M_j $$
    输出 `1`, 我们就定义 `f(i)` 为 `0`.
  - 换句话说, 我们使得
    $$ M_j $$
    不能计算 `f(i)`.
* 我们还`"移除"`了
  $$ M_j $$,
  也就是说,
  $$ M_j $$
  无须在后面的迭代中再被模拟.
  - 这就定义了函数 `f`.

---

* 但如果我们真想取得什么进展的话, 采取更粗放一点儿的观点就会更有用:
  其中, 我们区分`多项式时间`与`指数时间`, 但不区分
  $$ O(n^2) $$
  时间与
  $$ O(n^3) $$
  时间.
  - 这时, 我们认为任何多项式上界都是`"快的"`,
    而任何指数上界都是`"慢的"`.
* 我知道有人会立刻提出异议: 如果一个问题能在多项式时间内解决,
  但这个多项式是
  $$ n^{50000} $$,
  事情会怎样? 或者,
  如果一个问题需要在指数时间内解决, 但这个指数是
  $$ 1.00000001^n $$,
  事情又会怎样?
  - 我的回答比较务实: 如果这样的情况经常在实践中出现,
    那说明我们使用了错误的抽象.
* 但到目前为止, 我们似乎使用的是正确的抽象.
  对于在多项式时间内可解的大问题 (匹配, 线性规划, 质数判定等),
  它们大多数确实存在实用的算法.
* 而对于我们认为需要指数时间解决的大问题 (定理证明, 电路最小化等),
  它们大多数真的没有实用的算法.
  - 因此, 我们的脂肪和肌肉是由有经验事实的骨架支撑的.

---

* `P` 是一个图灵机可在多项式时间内解决的一类问题.
  - 换句话说, `P` 是所有
    $$ TIME(n^k) $$
    的并集, 其中 `k` 取遍所有正整数.
  - 注意, 这里的`"问题"`总是指判定问题:
  - 输入为 `n` 比特字符串, 输出为`"是"`或`"否"`的问题.
* `PSPACE` 是可在多项式空间内解决 (但不限时间) 的一类问题.
  - 换句话说, 它是所有
    $$ SPACE(n^k) $$
    的并集, 其中 `k` 取遍所有正整数.
* `EXP` 是可在指数时间内解决的一类问题.
  - 换句话说, 它是所有
    $$ TIME(2^{n^{k}}) $$
    的并集, 其中 `k` 取遍所有正整数.
* 显然, `P` 包含于 `PSPACE`. 我还要说, `PSPACE` 包含于 `EXP`.
  - **为什么**?
* 对的: 一个拥有
  $$ n^k $$
  比特内存的图灵机在它最终停机或陷入某个无限循环之前,
  至多只能经历
  $$ 2^{n^{k}} $$
  个不同构形.
* 然后, `NP` 是这样一类问题:
  如果其输出为`"是"`, 那么存在一个多项式大小的证明,
  证明你可以在多项式时间内对此加以验证.
  - 在这里, `NP` 指的是非确定型多项式,
    `"Nondeterministic Polynomial"`.
* 我可以说得更技术性一点儿, 但最简单的方法还是举个例子:
  - 比如, 我给你一个一万位的数,
    然后我问你它是否有一个以 `3` 结尾的因子.
  - 确实, 回答这个问题可能需要很长很长的时间.
    但如果你的学生为你找到了这样一个因子,
    那你可以很容易验证它属不属实.
  - 你无须信任你的学生.
* 我会说, `NP` 包含于 `PSPACE`. 为什么?
* 对的: 在多项式空间里, 你可以遍历所有可能的
  $$ n^k $$
  比特证明, 并逐个验证它们.
  - 如果答案是肯定的, 那么其中一个证明是有效的;
  - 而如果答案是否定的, 则不存在有效的证明.
  - 显然, `P` 包含于 `NP`.

---

* 当然, 问题就来了, `P` 是否等于 `NP`?
  - 换句话说, 如果你能够有效地验证一个答案,
    那么你也能够有效地找出一个答案吗?
  - 可能你已经听说过这个问题了.
* 看, 对于这个 `P` 与 `NP` 问题, 我还能说些什么呢?
  - 人们喜欢把它描述为`"很可能是位居理论计算机科学核心的未解决问题"`.
  - 这轻描淡写挺好笑的.
  - 事实上, `P` 与 `NP` 问题是人类提出的最深刻的问题之一.

---

* 我们还可以说, 差不多所有的"难"问题只是同一个"难"问题的不同表现形式.
  也就是说, 如果对于它们中的任何一个问题, 我们找到了一个多项式时间算法,
  那么也就找到了所有其他问题的多项式时间算法.
  - 这是史蒂文·库克 (Stephen Cook), 理查德·卡普 (Richard Karp)
    和列昂尼德·莱温在`20`世纪`70`年代早期创立的
    `NP` 完全性理论所给出的结果.
* 它的思路是这样的: 如果任何 `NP` 问题都可以有效归约到问题 `B`,
  那我们就定义 `B` 为`"NP 难"`的. 这是什么意思?
  - 它的意思是, 如果我们有一个谕示可以立刻解决 `B`,
    则可以在多项式时间内解决任何 `NP` 问题.
* 这样给出的归约概念被称为`库克归约`.
  还有一个弱一点儿的归约概念,
  叫作`卡普归约`.

---

* 库克归约与卡普归约的区别在哪里?
* 在库克归约中, 为了解决问题 `A`, 我们可以多次调用问题 `B` 的谕示.
  我们甚至可以根据情况 (也就是根据之前调用结果的情况) 调用谕示.
  - 卡普归约弱就弱在它不允许我们拥有这些自由.
  - 不过出人意料的是, 我们所知的几乎所有归约都是卡普归约 --
    我们在实践中很少有机会发挥库克归约的全部实力.
* 现在, 如果一个问题既是 `NP` 难的, 又在 `NP` 中,
  则我们就说它是 `NP` 完全的.
  - 换句话说, `NP` 完全问题是 `NP` 中`"最难"`的问题:
  - 它集所有其他 `NP` 问题的难度之大成.

---

* 另一个重要事实是**马尔可夫**不等式
  - 或者说, 以他的名字命名的许多不等式之一:
* 如果 `X ≥ 0` 是一个非负随机变量,
  那么对于所有的 `k`, 都有

$$
P_r \left [ X \geq kE \left [ X \right ] \right ] \leq 1/k
$$

* 为什么? 好吧, 如果 `X` 大于其期望的次数太多,
  则即使 `X` 在剩下的时间里全为零,
  这也仍然不足以把 `X` 拉回到期望.
* 由`马尔可夫不等式`可以马上得到理论计算机科学中**第三**有用的事实,
  即所谓的`切尔诺夫上界`. 切尔诺夫上界是说,
  - 如果你抛 `1000` 次硬币, 然后得到 `900` 次正面朝上,
    那么这枚硬币很有可能有问题.
  - 这是赌场经理在决定是否派打手打断某人的腿时偷偷使用的定理.
* 正式地说, 令 `h` 为你抛一枚没有问题的硬币 `n`
  次得到正面朝上的次数.
  - 一种表述切尔诺夫上界的方法是
  - $$
    P_r \left [ | h - n/2 | \geq a \right ] \leq 2e^{-ca^{2} / n}
    $$
  - 其中, `c` 是一个常数, 你不知道的话, 可以去查一下.
  - 好吧, `c = 2` 就可以.

---

* 很多很多的原因会让你想利用随机性:
  - 为了在密码学中挫败窃听者,
  - 为了在通信协议中避免死锁, 如此等等.
  - 但在复杂性理论中, 使用随机性的常见目的是"错误找平",
    也就是说, 将一个对绝大多数输入奏效的算法,
    变成一个在绝大多数时间里对所有输入奏效的算法.

* 思路是这样的. **费马小定理** (不要与他的大定理相混淆!)
  告诉我们, 如果 `p` 为质数, 则
  $$ x^p = x(mod p) $$
  对于每一个整数 `x` 都成立.
  - 因此, 如果你找到了一个 `x`, 使得
    $$ x^p \neq x(mod p) $$,
    你立马就会知道 `p` 是合数.
  - 即便你仍然对它的除数是什么一无所知.
* 反过来, 我们则希望, 要是你不能找到一个 `x`, 使得
  $$ x^p \neq x(mod p) $$,
  那你将能够非常有信心地说, `p` 是质数.
* 可惜的是, 现实不是如此. 事实证明有些合数 `p`
  会`"伪装"`成质数, 使得对于每个 `x` 都满足
  $$ x^p = x(mod p) $$.
  - 这些`"伪装者"` (称为卡迈克尔数) 的前几个例子是
    `561`, `1105`, `1729`, `2465` 和 `2821`.
* 当然, 如果只有有限个`"伪装者"`, 并且我们知道它们是什么,
  那也是可以的.
  - 但 W.R.奥尔福德, 安德鲁·格兰维尔 和 卡尔·波梅伦斯
    在 `1994` 年证明了, 有无穷多个`"伪装者"`.

---

* 当我们在谈论概率计算时, 我们有可能是在谈论以下**四类复杂性**之一,
  它们由约翰·吉尔在 `1977` 年的一篇论文中定义.
* **PP (概率多项式时间)**. 简单来说, `PP` 是这样一类问题:
  存在一个多项式时间随机算法以大于 `1/2` 的概率接受
  (如果问题的答案为`"是"`), 或以小于 `1/2` 的概率接受
  (如果问题的答案为`"否"`).
  - 换句话说, 我们设想一个图灵机**M**得到一个
    `n` 比特的字符串 `x` 作为输入,
    并且有一个无限量的随机比特源.
  - 如果 `x` 是一个`"是"`输入,
    则至少一半的随机比特设定可以使 `M` 接受;
  - 而如果 `x` 是一个`"否"`输入,
    则至少一半的随机比特设定可以使 `M` 拒绝.
* 此外, `M` 需要在以 `n` 的多项式为上界的某个步数后停机.
* 而且事实上, `PP` 是一个极其巨大的类:
  - 比如, 它显然包含 `NP` 完全问题.
  - 为什么?
  - 好吧, 给定一个具有 `n` 个变量的布尔公式
    $$ \varphi $$,
    你可以做的是立刻以
    $$ 1/2 + 2^{-n} $$
    的概率接受, 不然就随机选择一种赋值,
    当且仅当它使
    $$ \varphi $$
    可满足时接受.
* 这时, 要是存在至少一个
  $$ \varphi $$
  的可满足赋值,
  你总的接受概率将大于 `1/2`, 否则小于 `1/2`.
* 事实上, 复杂性研究者认为, `PP` 严格地比 `NP` 大.
  尽管, 就像通常一样我们不能证明这一点.
  - 基于上述考虑, 吉尔定义了一个更"合理"的 `PP` 的变体.
  - 具体如下.
* **BPP (错误有界的概率多项式时间)**. 它是这样一类判定问题:
  存在一个多项式时间随机算法以大于 `2/3` 的概率接受
  (如果问题的答案为`"是"`), 或以小于 `1/3` 的概率接受
  (如果问题的答案为`"否"`).
  - 换句话说, 给定任何输入, 该算法犯错的概率至多为 `1/3`.
  - `1/3` 这个数的重要性仅仅在于, 它是某个小于 `1/2` 的正的常数.
  - 任何这样的常数都一样好.
  - 为什么?
  - 好吧, 假设给我们一个犯错概率为 `1/3` 的 `BPP` 算法.
    如果我们愿意, 那么我们可以很容易修改这个算法,
    使得其犯错概率至多为 (比如)
    $$ 2^{-100} $$.
  - 我们该怎么做呢?
* 所以这就是 `BPP`: 如果你愿意,
  你可以把它当作由经典宇宙中的计算机能够切实解决的所有问题组成的类.
* **RP (随机多项式时间)**. 正如我刚才所说,
  一个 `BPP` 算法的犯错概率可以很容易变得比小行星撞击计算机的概率都小.
  而这对于绝大多数应用来说已经够好了.
  - 比如, 在医院管理辐射剂量,
    或对数十亿美元的银行交易进行加密, 或控制发射核弹.
  - 但对于证明定理呢?
  - 对于某些应用, 你真的不能冒险.
* 这就引出了 `RP`, 它是这样一类问题:
  存在一个多项式时间随机算法以大于 `1/2` 的概率接受
  (如果问题的答案为`"是"`),
  或者以零概率接受
  (如果问题的答案为`"否"`).
  - 换句话说: 要是算法接受了哪怕一次,
    你就可以确信答案为`"是"`;
  - 而如果算法一直拒绝, 你则可以非常有信心地说
    (但永远无法确信), 答案为`"否"`.
* `RP` 有一个显而易见的`"补"`, 被称为 `coRP`. 它是这样一类问题:
  存在一个多项式时间随机算法以概率 `1` 接受
  (如果问题的答案为`"是"`),
  或者以小于 `1/2` 的概率接受
  (如果问题的答案为`"否"`).
* **ZPP (零错误的概率多项式时间)**. 这个类可被定义为
  `RP` 和 `coRP` 的交集 -- 同时处在这两类中的问题.
  - 等价地, `ZPP` 是这样一类问题:
  - 存在一个多项式时间随机算法, 只要它确实输出了一个答案,
    那么该答案必定是正确的, 但它会在多达一半的时间里输出`"不知道"`.
  - 再一次地, 还是等价地. `ZPP` 是这样一类问题:
    存在一个从不犯错的算法, 但其运行时间的期望为多项式时间.

---

* 在`复杂性理论`中, 事实证明`随机性`与另一个被称为`非一致性`
  (nonuniformity) 的概念有着密切的联系.
  - 尽管我们稍后才会见到这种联系.
* 简单来说, `非一致性`说的是,
  你需要对每个长度为 `n` 的输入选择不同的算法.
  - 为什么你需要这么愚蠢的东西呢?
  - 好吧, 你还记得吗?
  - 我提到过`布卢姆加速定理`.
  - 它说的是, 有可能建构出一些奇怪的问题,
    使得解决它们的最快算法并不存在,
    而只存在一个算法的无穷序列, 对于足够大的输入,
    其中每个算法都比上一个算法的速度更快.
  - 在这种情况下, `非一致性`将允许你在所有算法中进行选择,
    从而获得最佳性能.
  - 换句话说, 给定一个长度为 `n` 的输入,
    你可以简单选择对于该特定长度的输入运行最快的算法!
* 但即便在一个允许`非一致性`的世界里, 复杂性研究者相信,
  对于什么是`"可有效计算"`的问题仍然存在很强的限制.
  - 而当我们想要讨论这些限制时, 需要用到
    理查德·卡普 和 理查德·利普顿 (Richard Lipton)
    在 `1982` 年提出的术语.
  - 卡普和利普顿定义了复杂类 `P/f(n)`,
    也就是带有 `f(n)` 大小的建议的 `P`.
  - 它包括所有借助一个仅取决于输入长度 `n` 的 `f(n)`
    比特`"建议字符串"`
    $$ a_n $$,
    多项式时间内在确定型图灵机上可解的问题.
* 你可以把多项式时间图灵机想象成一位研究生, 而建议字符串
  $$ a_n $$,
  就是他的导师给出的智慧.
  - 像绝大多数导师一样, 这是一位拥有无限智慧, 仁慈且值得信任的导师.
    他一心想帮助学生解决他们各自论文的问题,
* 也就是判定他们各自在
  $$ \{ 0, 1 \}^{n} $$
  中的输入 `x` 会被`接受`还是被`拒绝`.
* 但也像绝大多数导师一样, 他太忙了,
  没时间去搞清楚他的学生在做什么.
  - 因此, 他只是对所有人给出同样的建议
    $$ a_n $$,
    并相信他们能将它应用到他们特定的输入 `x` 上.
* 你能够研究不可信的建议, 事实上, 我研究过.
  我定义过一些基于不可信建议的复杂类, 但在通常定义的建议中,
  我们一般假设它是值得信任的.
* 我们将对 `P/poly` 类尤其感兴趣,
  它包括所有在多项式时间内借助多项式大小的建议可解的问题.
  - 换句话说, `P/poly` 是
    $$ P/n^{k} $$
    取遍所有正整数 `k` 时的并集.

---

* 好吧, 下面是一个简单的**对角化论证**. 事实上,
  我将证明一个更强的结论: 存在不属于
  $$ P / n^{\log{n}} $$
  的问题.
  - 令
    $$ M_1, M_2, M_3, ... $$
    为多项式时间图灵机的一个列表, 并给定一个输入长度 `n`.
    然后我会说, 存在一个布尔函数
  - $$ f: \{ 0, 1 \}^{n} \rightarrow \{ 0, 1 \} $$,
  - 使得即便给定任何
    $$ n^{ \log{n} } $$
    比特的建议字符串, 前 `n` 个机器
    $$ M_1, M_2, M_3, ... $$
    都不可计算.
  - 为什么? 只需要一个计数论证: 一共有
    $$ 2^{2^{n}} $$
    个布尔函数, 但只有 `n` 个图灵机和
    $$ 2^{n^{\log{n}}} $$
    个建议字符串.
  - 因此, 为每个 `n` 选择这样一个函数 `f`,
    然后你就可以让每个图灵机
    $$ M_i $$
    在除了有限多输入长度外, 对所有其他输入长度都不可计算.
  - 事实上, 我们甚至不需要假设
    $$ M_i $$
    在多项式时间内运行.

---

* 即便
  $$ P \neq NP $$,
  你可能还是很想知道 `NP`
  完全问题能否在**概率多项式时间**内解决.
* 换句话说, `NP` 在 `BPP` 中吗? 对此,
  我们已经有一些比较具体的结论.
  - 如果
    $$ NP \subseteq BPP $$,
    则显然有
    $$ NP \subset P/poly $$
  - 因为
    $$ BPP \subset P/poly $$.
* 但根据`卡普-利普顿`定理, 这意味着 `PH` 会坍缩. 因此,
  如果你相信多项式层级是无限多的, 那你也应该相信
  `NP` 完全问题不能经由**随机算法**有效解决.
* 如果非一致性能够模拟随机性, 那它也能够模拟量子性吗?
  - 换句话说,
    $$ BQP \subset P/poly $$
    吗?
* 好吧, 我们不知道, 但我们一般认为这不太可能. 显然,
  在阿德勒曼关于 `BPP` **真包含于** `P/poly` 的证明中,
  如果我们把 `BPP` 换成 `BQP`, 证明就会完全失效.
  - 但这引发了一个有趣的问题:
  - 为什么它会失效?
  - 量子理论与经典概率论之间的关键区别究竟是什么?
  - 它使得证明在一种情况下行得通而在另一种情况下却行不通.

---

* 显而易见, 质数判定问题在 `coNP` 中.
  - 1975 年, 沃恩·普拉特 (W.Pratt) 证明了它在 `NP` 中.
  - 1977 年, 罗伯特·索罗维, 福尔克尔·施特拉森 和
    迈克尔·拉宾 证明了它在 `coRP` 中.
  - 1992 年, 伦纳德·阿德尔曼 和 黄铭德证明了它在 `ZPP` 中.
  - 2002 年, 马尼德拉·阿格拉沃尔, 尼拉杰·卡亚勒 和
    尼廷·萨克塞纳 证明了它在 `P` 中.

## 随机性

* 把一个`随机算法`转化为`确定型算法`的工作称为**去随机化**.
  质数判定问题的历史是这项工作一个令人瞩目的成就.
  - 但与之而来的一个显而易见的问题就是:
  - 每个随机算法都能去随机化吗?
  - 换句话说, `P` 是否等于 `BPP`?
* 再一次地, 答案是我们不知道. 通常情况下,
  如果我们不知道两个复杂性类是否相等,
  则`"默认的猜想"`是它们**不相等**.
  - `P` 和 `BPP` 一直以来也是被这样认为的.
* 在过去几十年里, 如山的证据说服了差不多我们所有人,
  其实 `P = BPP`. 在这里, 我们无法深人回顾这些证据,
  但我只举一个定理, 让你体会一下.
* 定理 (因帕利亚佐-威格德森, 1997):
  假设存在一个问题, 它在指数时间内可解, 但在亚指数时间内,
  即便借助亚指数大小的建议字符串也不可解, 则 `P = BPP`.
* 请注意, 该定理如何将**去随机化**与**非一致性**联系在了一起,
  具体地说, 是与证明某些特定问题对非一致的算法来说是困难的联系在了一起.
  - 其前提显然看上去是合理的.
  - 从我们目前的情况看来, 其结论 (`P = BPP`)
    看上去也是合理的, 但两者看上去又都相互没有关系.
  - 所以这个定理或许可被描述为"如果驴能够嘶叫, 那猪就能够哼哼".

---

* 但简单来说, 一个 `PRG` 就是一个函数,
  它将一个短字符串 (称为**种子**) 作为输入,
  并生成一个长字符串作为输出,
  并且是以这样一种方式:
  - 如果种子是随机的, 则输出也看上去是随机的.
  - 显然, 输出不可能是随机的, 因为它不具有足够的熵:
* 如果种子是 `k` 比特长, 则只能有
  $$ 2^k $$
  个可能的输出串, 而不论那些输出串有多长.
* 不过, 我们追求的是, 只要没有多项式时间算法可以成功将`"真"`随机性与
  `PRG` 的输出区分开来就可以. 当然,
  我们也希望将种子映射到输出的函数是在多项式时间可计算的.
* 早在 `1982` 年, 姚期智就意识到,
  如果你可以构造一个"足够好"的 `PRG`, 你就可以证明 `P = BPP`.
  - 为什么?
* 假设对于任何整数 `k`, 你都有一种方法, 能在多项式时间内将
  $$ O(\log{n}) $$
  比特的种子扩展为一个 `n` 位输出, 并且不存在能在
  $$ n^k $$
  时间内成功将其与真正的随机性输出区分开来的算法.
* 我们还假设你有一个能在
  $$ n^k $$
  时间内运行的 `BPP` 图灵机.
  - 在这种情况下, 你可以简单地遍历所有可能的种子 (只有多项式多个),
    将相应的输出传给 `BPP` 图灵机, 然后输出占多数的答案.
* 该 `BPP` 图灵机接受给定一个伪随机串的概率 `必须`
  与它接受给定一个真正随机串的概率大致相同, 不然的话,
  该图灵机将能够把`伪随机串`与`真随机串`区分开来,
  而这违背了假设!
* 但**非一致性**在这一切中起了什么作用? 这里的要点是,
  除了一个随机 (或伪随机) 字符串, 一个 `BPP`
  图灵机还收到一个输入 `x`.
  - 而我们需要使`去随机化`对每个 `x` 都成立.
* 这意味着, 针对去随机化, 我们必须将 `x`
  看成某位超级智能的攻击者为了挫败 `PRG` 而提供的建议字符串.
  你看, 这就是为什么我们不得不假设存在一个问题,
  它甚至在建议存在的情况下仍然很难:
  - 因为我们需要构造一个 `PRG`.
  - 它甚至在`"攻击者"` `x` 存在的情况下仍然与真随机数发生器无法区分.
* 总结一下: 如果我们能证明某些问题对于**非一致的算法**而言**充分难**,
  则我们将能证明 `P = BPP`.
* 这引出了我要说的 `BPP` 和 `BQP` 的第三个区别:
  - 虽然我们中绝大多数人相信 `P = BPP`,
    但我们中绝大多数人显然不相信 `P = BQP`.
  - 事实上, 我们无法相信这一点.

---

* 思考题`1`: 我们有一枚不均匀硬币, 其头像朝上的概率为 `p`.
  用这枚硬币模拟一枚均匀硬币.
* 答案: 答案是`"冯·诺伊曼技巧"`: 将不均匀硬币抛两次,
  将 `HT` (第一次头像朝上, 第二次字朝上) 定义为头像朝上,
  将 `TH` 定义为字朝上. 如果出现 `HH` 或 `TT`, 则重新尝试.
  - 如此一来, `"头像朝上"`和`"字朝上"`的概率相等, 各为
    `p(1 - p)`.
  - 基于 `HT` 或 `TH` 的发生,
    可见这枚模拟的硬币是均匀的.
* 思考题`2`: `n` 个人围成一个圆圈.
  他们每个人头戴一顶红色或蓝色的帽子, 帽子均匀且独立地随机分配.
  他们每个人都能看到其他人帽子的颜色, 但看不到自己帽子的颜色.
  他们根据自己的所见就红色帽子的数目是`偶数`还是`奇数`进行投票.
  - 是否存在一个策略使得投票结果正确的概率`大于` `1/2`?
* 答案: 每个人按照如下策略决定自己所投的票:
  - 如果所见蓝色帽子的数目比所见红色帽子的多,
    则遵照所见红色帽子数目的奇偶性进行投票.
  - 否则, 依照所见红色帽子数目的相反的奇偶性投票.
    如果红色帽子与蓝色帽子的数目相差至少 `2`,
    则这个策略一定会成功.
  - 否则, 该策略可能会失败. 然而,
    红色帽子与蓝色帽子的数目相差少于 `2` 的概率很小:
    $$ -O(1 / \sqrt{N}) $$.

## 密码学

* 在 `20` 世纪 `40` 年代克劳德·香农证明了,
  信息论意义上的安全密码要求 `发送者` 和 `接收者`
  分享至少与他们想要传递的讯息长度相同的密钥.
  - 就像香农的其他大部分结论, 这个结论现在看来是平凡的.
  - 草创就是有这点好处!
* 他的证明是这样的: 给定密文和密钥, 明文最好能够被唯一地还原.
  换句话说, 对于任何给定的密钥,
  从`明文`到`密文`的映射最好是一个`单射`.
  但这马上意味着, 对于给定一个密文 `c`,
  那些可能产生 `c` 的明文的数目最多只能是密钥的数目.
* 换句话说, 如果可能的密钥比明文数目少,
  那么窃听者就能够排除一些明文 --
  这些明文通过任何密钥都不会加密为 `c`.
  - 因此, 我们的密码系统就不会是**完全安全**的.
  - 而如果我们想要完全的安全性, 那就需要至少跟明文一样多的密钥,
    或者等价地, 密钥需要至少与明文一样多的比特数.

---

* **伪随机数发生器**

* 简单来说, 伪随机数发生器 (`PRG`) 是这样一个函数,
  它以一段简短且真正随机的字符串作为输入,
  然后以一段冗长而看似随机的字符串作为输出.
  - 更正式地, `PRG` 是一个具有以下特性的函数 `f`.
  - (1) `f` 将一个 `n` 比特输入串 (称为`种子`)
    映射到一个 `p(n)` 比特的输出串,
    其中 `p(n)` 是某个比 `n` 大的多项式.
  - (2) `f` 在 `n` 的多项式时间内可计算.
  - (3) 对于每一个多项式时间算法 `A` (称为`攻击者`),
    $$
    |P_{r_{n比特字符串x}}[A 接受 f(x)] - P_{r_{p(n)比特字符串y}}[A 接受 y]|
    $$
    小到可以忽略.
  - 我的意思是, 对于任何多项式 `q`,
    它都要比 `1/q(n)` 下降得更快.
  - 当然, 以`指数速率`下降则更好.
  - 或者用文字描述,
    没有多项式时间的攻击者能够以任何不可忽略的偏差将
    `f` 的输出与一个真正的随机字符串相区分.

---

* **单向函数** (`OWF`) 是 `PRG` 的表兄弟. 直观上看,
  `OWF` 就是一个`容易计算`却`不容易求逆`的函数.
  - 更形式化地说, 如果满足
  - (1) `f` 在 `n` 的多项式时间内可计算;
  - (2) 对于每个多项式时间的攻击者 `A`, `A` 能成功对
    `f` **求逆**的概率
  - $$ Pr_{n 比特字符串 x}[f(A(f(x))) = f(x)] $$
  - 小到可忽略不计, 也就是说, 对于任意的多项式 `q`,
    它都比 `1/q(n)` 小, 那么一个将 `n` 比特映射到
    `p(n)` 比特的函数 `f` 称为**单向函数**.
* 定义中使用的是事件 `f(A(f(x))) = f(x)`, 而不是 `A(f(x)) = x`,
  这是考虑到 `f` 可能有多个**逆**的情况.
  - 所以在这个定义中, 我们考虑的是算法 `A`,
    它可以找到 `f(x)` 的任何一个原像, 而不仅仅是 `x` 本身.
* 我会说, `PRG` 的存在性蕴涵 `OWF` 的存在性.
  - 你能告诉我这是为什么吗?
  - 没错, 因为 `PRG` 就是一个 `OWF`!

---

* 不管怎样, 任何公钥密码系统的核心都是所谓的**陷门单向函数**.
  - 这个函数要求
  - (1) 容易计算;
  - (2) 难以求逆;
  - (3) 容易求逆 -- 如果得到某个秘密的`"陷门"`信息.
* 前两个要求与普通的 `OWF` 一样.
* 第三个要求 (`OWF` 应该具有一个`"陷门"`, 使得求逆变得很容易)
  则是新的.
* 注意比较, 普通的单向函数的存在性蕴涵安全的**私钥**密码系统的存在性,
  而`"陷门"`单向函数的存在性蕴涵安全的**公钥**密码系统的存在性.

## 量子力学

* 有两种教授量子力学的方法. `第一种`方法
  (对于当今的绝大多数物理学家来说, 这是唯一一种)
  是依照重要概念被发现的历史顺序来教授.
  - 这样, 你将从经典力学和电动力学开始,
    并在每个阶段求解大量艰深的微分方程.
    然后, 你会了解到黑体辐射悖论和种种奇怪的实验结果,
    以及它们所引发的物理学大危机.
  - 进而, 你将学到在 `1900` 年至 `1926` 年,
    物理学家为了消除这场危机而做的复杂修补工作.
  - 再接下来, 如果你足够幸运, 在经过数年苦学之后,
    你就会最终接触到核心概念:
    大自然不是由总是非负的概率描述的,
    而是由被称为**概率幅**的数描述的,
    并且**概率幅**可以为`正数`, `负数`, 甚至`复数`.
* `第二种`教授量子力学的方法抛弃了对其发现的细致叙述,
  直接从核心概念开始, 即以某种方式推广概率开始,
  允许使用负号 (以及更一般地, 允许使用`复数`).
  你一旦理解了这个核心, 就可以把物理学添加进去,
  并计算任何你想要计算的原子的光谱.
  - 这里我将会采用第二种方法.
* 那么, **什么是量子力学?** 尽管它由物理学家发现,
  但它并不是一个像电磁学或广义相对论那样的物理学理论.
  - 在通常的"科学层级"中
    (最顶上是生物学, 之下是化学, 再下是物理学, 最底下是数学),
    量子力学应该位于数学与物理学之间.
  - 简单来说, 量子力学是操作系统,
    其他物理学理论作为应用软件在其中运行
    (广义相对论除外, 因为它尚未被成功移植到这个操作系统).
  - 甚至有一个词用来描述将一个物理学理论移植到这个操作系统的过程 -- **量子化**.
* 但是, 如果量子力学不是通常意义上的物理学
  (如果它不关于物质, 能量, 波或粒子), 那它到底关于什么呢?
  - 在我看来, 量子力学关于`信息`, `概率`, `可观测量`,
    以及它们之间的关系.
* 我将主张一个不无争议的观点: 量子力学是当你从概率论出发,
  然后试着推广它, 使得过去称为`"概率"`的东西可以为`负数`时,
  你将不可避免得到的东西.
  - 这样的话, 这个理论本可以被 `19` 世纪的数学家发明,
    而不需要借助任何实验结果.
* 历史不是如此, 但本可以如此. 然而,
  当时的数学家在研究这些数学结构时, 终究没有想出来量子力学,
  直到实验结果把它摆在了他们面前.
  - 这正很好地说明了, 为什么实验在一开始很重要.
* 在通常情况下, 我们需要实验的唯一原因是我们不够聪明.
  而在进行实验之后,
  假如我们确实通过实验了解到了一些值得了解的东西,
  那么我们就会希望明白, 为什么在一开始, 实验本来是不必要的.
  为什么世界以别的方式运作就说不通了. 但我们太笨了,
  无法靠自己把一切想明白!

---

* 我们试图构造的理论需要以某种方式做到符合我们的观测.
  因此, 假设我们有一个被向量 `(α, β)` 描述的比特,
  我们需要搞清楚, 当我们看这个比特时, 我们会看到什么.
* 好吧, 由于它是一个比特, 我们应该会看到 `0` 或 `1`.
  - 更进一步地, 我们看到 `0` 的概率与看到 `1` 的概率之和最好是 `1`.
* 那么从向量 `(α, β)` 出发, 如何能得到两个加起来为 `1` 的数?
  - 很简单: 我们可以令
    $$ α^2 $$
    为输出 `0` 的概率, 令
    $$ β^2 $$
    为输出 `1` 的概率.
* 但在这种情况下, 为什么不忘掉 `α` 和 `β`,
  而直接用概率描述这个比特呢?
  - 嗯, 当我们对这个向量进行操作时, 其中的差别就会体现出来.
* 在概率论中, 如果我们有一个用向量 `(p, 1 - p)` 描述的比特,
  我们就可以通过一个**随机矩阵**
  - 也就是一个由`非负实数`构成,
    每列之和为 `1` 的矩阵表示对这个比特的任意操作.
  - 举个例子, `"比特翻转"`操作,
    它将输出为 `1` 的概率由 `p` 变为 `1 - p`

---

* 你从来不会在经典世界中看到这种干涉,
  这是因为那里的**概率**不能为**负数**.
* 因此, 正负概率幅之间的相消可以被视为所有"量子怪异现象"的源泉,
  将量子力学与经典概率论区分开的关键.
* 真希望当初我第一次听说`"量子"`这个词时,
  就有人告诉我这一点!

## 量子计算

* 在数学上, 我们用一个叫作`密度矩阵`的东西来表示混合态.
  具体是这么做的: 比如, 一个向量有 `N` 个概率幅,
  $$ (a_1, ..., a_n) $$.
* 首先, 你计算这个向量与自身的`外积`, 得到一个 `N × N`
  的矩阵, 其 `(i, j)` 分量是
  $$ a_{i} a_{j} $$.
  - 同样地, 在实数情况下
* 然后, 如果你有一个关于这样一些向量的概率分布,
  那你只需将相应矩阵进行线性组合即可.
* 举例来说, 如果一个向量有 `p` 的概率,
  另一个向量有 `1 - p` 的概率,
  那么密度矩阵为 `p` `乘以` 第一个矩阵,
  `加上` `1 - p` 乘以另一个矩阵.
* 通过先应用一个`酉变换`, 然后看这个态 (或者用行话说, 测量它),
  密度矩阵编码了所有可从量子态的某种概率分布中得到的信息.
* 这暗含了, 如果两个概率分布给出了相同的密度矩阵,
  则这些分布在经验上是不可区分的, 换句话说,
  是处于`相同混合态`的.
* 举个例子, 假设你有 `1/2` 概率得到态
  $$ 1 / \sqrt{2}(| 0 \rangle + | 1 \rangle) $$,
  并有 `1/2` 概率得到态
  $$ 1 / \sqrt{2}(| 0 \rangle - | 1 \rangle) $$,
  那么描述你的这些知识的密度矩阵是

$$
\frac{1}{2}

\begin{pmatrix}
  1/2 & 1/2 \\
  1/2 & 1/2
\end{pmatrix}

+

\frac{1}{2}

\begin{pmatrix}
  1/2 & -1/2 \\
  -1/2 & 1/2
\end{pmatrix}

=

\begin{pmatrix}
  1/2 & 0 \\
  0 & 1/2
\end{pmatrix}

$$

* 因此, 你无法通过任何测量将这个混合态与另一个有 `1/2` 概率为
  $$ | 0 \rangle $$
  和 `1/2` 概率为
  $$ | 1 \rangle $$
  的混合态区分开来.

---

* 在这个让人满怀忧虑的, 迷人的, 但最后或许没有意义的辩论中,
  与其选择偏袒其中一方, 我更愿意拿一个没有争议的发现来结束这一章.
  - 本内特等人的下界告诉我们, 就算量子力学支持平行宇宙的存在性,
    也一定不会是以大多数人认为的方式支持!
* 正如我们已经看到的那样, 量子计算机并非一个可以"并行地尝试所有可能性",
  然后立马找到正解的器件. 如果我们非要用平行宇宙的眼光看世界,
  那这些宇宙还得去"合作"
  - 不光是这样, 还得相互融合来得到一个能以较大概率得到正确答案的干涉图案.

## 退相干和隐变量

* **退相干**

* 对这些困难的标准回应是叫作**退相干**的强有力的概念.
  退相千试图解释为什么我们在日常生活中没有注意到这些"量子怪事"
  - 为什么我们的经验世界是一个或多或少的经典世界.
  - 从退相干的角度看,
    确实有可能没有电子通过哪个狭缝的任何客观事实,
    但确实有关于你今天早上吃了什么早餐的客观事实:
    这两种情况是不一样的!
* 基本的想法是, 只要量子状态所编码的信息`"泄露"`到外部世界,
  这个态局域地看就会像是经典状态.
  - 换句话说, 对于一个局域的观察者而言,
    一个经典的比特和一个不可救药地与宇宙的其他部分相纠缠的量子比特没有任何区别.

* **容错定理**大致是说, 如果每个量子位,
  每个门操作的`退相干`速率低于一个常数阈值,
  那么在原则上有可能以比错误发生更快的速度纠正它们,
  并因此可以执行任意长的量子计算.

* 现在, 如果我们认为宇宙总处于纯态, 那么"宇宙的熵"刚开始为零,
  并将一直保持为零! 另外, 宇宙的熵并不是我们真正关心的,
  我们关心的是某个区域的熵. 我们先前看到过,
  原本孤立的物理系统由于与外界的相互作用,
  往往倾向于从纯态演化为混合态, 因此它们的熵会上升.
  - 从退相干的角度来看, 这就是**第二定律**在起作用.
* 另一种理解退相干和第二定律之间关系的方式是对整个多重宇宙的"上帝鸟瞰".
  一般来讲, **波函数**的不同分支可以相互干涉, 分裂融合成纠缠的灌木模样.

---

* 因此, 如果`退相干`的故事还是让你彻夜难眠,
  那么这个"量子大集市"还能提供些什么呢?
  - 好了, 现在轮到那些`隐变量`研究者兜售他们的产品了.
* 隐变量理论的想法很简单.
  如果我们认为量子力学描述的是平行宇宙这片涌动的广袤海洋,
  它不断地分岔, 合并, 相互抵消,
  那么我们现在要在这片海洋上追踪一艘小船.
* 我们认为这艘船的位置代表了给定时间点上`"真正的""实在的"`宇宙状态,
  而海洋则是一片`"潜在场"` (field of potentialities),
  四处猛烈冲击着这艘船.
  - 出于历史原因, 该船的位置被称为**隐变量**.
  - 尽管在某种意义上, 它是这种解释下唯一不被隐藏的部分.
* 现在, 我们的目标是为这艘船制定一套演化规则, 使得在任何时间,
  船可能的所在位置的概率分布恰好是标准量子力学预测的
  $$ |\psi|^2 $$
  分布.
* 通过构造, 隐变量理论在实验上就跟标准量子力学没有什么区别了.
  因此, 问题或许不会是它们是`"真的"`故事还是`"假的"`故事,
  唯一的问题是它们是`"好的"`故事还是`"坏的"`故事.

## 证明

* 我之前讲了讲**随机证明**, 即有不确定性因素的证明.
  我们也可以推广证明的概念, 让它包括`零知识证明`
  (zero-knowledge proofs).
  - 对于所问的命题,
    这种证明让看到它的人除了得知命题为真以外,
    学不到任何东西.
* 直观上, 这听起来是不可能的, 但我会用一个例子来说明.
  - 假设我们有两个图. 如果它们是**同构**的, 这会很容易证明.
  - 但是, 如果它们不是同构的, 而你又是一个无所不知的精灵,
    你该怎么向别人证明?
* 这很简单: 让你试图说服的那个人挑选两图中的一个,
  并随机重排, 然后传给你结果.
  - 接着, 那个人问: "我挑的哪个图?"
  - 如果图不是同构的, 那么你应该能回答正确.
  - 否则, 你就只能有 `1/2` 的概率回答正确.
  - 这样的话, 如果重复测试少数次, 你几乎必然会犯错.
* 这就是**交互式证明系统** (interactive proof system) 的一个例子.
  我们做什么假设了吗?
  - 我们假设你不知道验证者从哪个图开始,
    你也无法通过访问其大脑状态来搞清楚.
  - 或者, 就像理论计算机科学家会说的那样,
    我们假设你不能访问验证者的`"私有随机比特"`.
* 更有趣的是, 验证者在无须学习任何东西的情况下就能确信图不是同构的!
  - 特别是, 验证者变得相信一个命题,
    却不能因此说服别人相信同样的命题.
* 验证者除了被证明的东西的真实性以外, 学不到任何东西,
  而拥有这一属性的证明就被称为**零知识证明**.
  - 是啊, 你必须做更多的工作来定义`"学不到任何东西"`对验证者来说意味着什么.
  - 基本上, 它意味着, 如果验证者已经相信了这个命题,
    他就可以自己将整个协议模拟出来, 而不需要证明者的任何帮助.
* 在一定的计算假设下 (即`单向函数`存在), 可以表明:
  - __对每个 NP 完全问题而言, 都存在零知识证明.__
  - 这是戈德赖希 (Goldreich), 米卡利 (Micali)
    和威格德森在 `1986` 年的一个惊人发现.

## 学习

* 因此, 基于密码假设, 我们可以证明, 一般来说,
  `"找到一个假设来解释你所看到的数据"`这类问题可能是困难的.
  - 把这一结果稍作调整, 我们可以说,
    如果总可以有效地发现一个与你的测量结果一致的量子态,
    那么在量子攻击下, 就不会有`单向函数`是安全的.
  - 这句话的意思是, 我们似乎必须放弃从广义上解决这些学习问题的希望,
    而不得不仅仅处理一些特殊情况.
  - 在经典情况下, 我们可以有效地学习一些特殊的概念类,
    比如恒定深度的电路或奇偶函数.

## 交互式证明, 电路下界及其他

* 炸弹来了: 在`"真实"`的, 非相对化的世界里,
  我们如何证明一个公式是不可满足的?
  - 我们必须以某种方式利用该公式的结构.
  - 这里要利用已经明确给定的布尔公式,
    而不只是某个抽象的布尔函数.
  - 具体该怎么做?
* 假设这是一个 `3SAT` 问题, 由于 `3SAT` 是 `NP` 完全问题,
  因此该假设不失一般性.
  - 这里有一堆 `(n个)` 子句, 我们想要确认没有办法满足所有的子句.
* 现在我们要做的是把这个公式映射到`有限域`上的多项式,
  这一招叫作`算术化` (arithmetization).
  - 基本上, 我们要把这个逻辑问题转化为代数问题,
    这样我们就会有更多手段来处理问题.
  - 具体方法是, 我们把一个 `3SAT` 实例重写为次数为 `3` 的多项式,
    即 `1` 减去 `1` 分别减这 `3` 个赋值的乘积,
    即子句 `(x OR y OR z)` 变为
    `1 - (1 - x)(1 - y)(1 - z)`
* 请注意, 只要 `x`, `y` 和 `z` 只能取 `0` 和 `1`
  (对应`"假"`和`"真"`),
  该多项式就完全等同于我们在开始时使用的逻辑表达式.
  - 但现在, 我们能做的是重新诠释这一多项式,
    把它放到更大的域上.
* 我们选择某个足够大的质数 `N`, 然后把该多项式放在
  $$ GF_N $$
  上 (有 `N` 个元素的域).
  - 记该多项式为
    $$ P(x_1, ..., x_n) $$.

---

* 提一个简单的问题: 假设有两个次数为 `d` 的多项式
  $$ P_1 $$
  和
  $$ P_2 $$,
  它们可以在多少个点上相等?
  - 假设它们不等
* 先考虑它们的差
  $$ P_1 - P_2 $$,
  由于这也是次数最高为 `d` 的多项式,
  由代数基本定理可知, 它至多有 `d` 个不同的根;
  - 假设它不恒为 `0`
* 因此, 两个不等的多项式最多可以在 `d` 个地方相等,
  其中 `d` 是多项式的次数. 这意味着,
  如果这些多项式定义在大小为 `N` 的域上,
  我们在这个域里选择一个随机的点,
  就能得到两个多项式在该点上相等的可能性的上界.
  - 至多为 `d/N`
* 回到刚才的协议, 我们假设了 `d` 比 `N` 小得多, 于是,
  $$ Q_1 $$
  和
  $$ Q'_1 $$
  在该域中一些随机元素上相等的概率要比 `1` 小得多.
  所以, 当我们随机选出
  $$ r_1 $$
  时,
  $$ Q_1(r_1) = Q'_1(r_1) $$
  的概率最多为 `d/N`.
  - 仅在非常不走运的时候, 我们才会选出让它们相等的
    $$ r_1 $$,
    所以我们可以继续下去, 并假设
    $$ Q_1(r_1) \neq Q'_1(r_1) $$.
* 不难想象, 证明者现在已经稍稍汗颜了.
  他试图说服我们相信他的谎言, 但也许他仍然可以搞定一切.
  但接下来, 我们要随机选一个
  $$ r_2 $$.
  - 再一次, 他可以圆谎的概率将最多是 `d/N`. 每次迭代都一样.
  - 所以, 他可以圆下所有谎言的概率最多为 `n(d/N)`.
  - 我们可以选择足够大的 `N`, 这样一来, 这一概率会比 `1` 小得多.
* 为什么不在正整数的集合上执行这个协议?
  因为我们没有产生随机正整数的方法, 而我们还得做到这一点.
  - 因此, 我们只能随便挑一个非常大的`有限域`.
* 因此, 该协议告诉了我们
  $$ coNP \subseteq IP $$.
  - 事实上, 它给了我们更强的结论.
  - 经过一番标准论证, 我们知道 `IP` 再疯狂也大不过 `PSPACE`.
  - 你可以证明, 你能用`交互式协议`做的任何事情都可以在 `PSPACE` 中模拟.
  - 我们可以让 `IP` 更大吗?

---

* 在 `1990` 年证明的一个非常重要的结果 --
  户田定理 (Toda's theorem) 认为,
  $$ P^{\sharp P} $$
  包含整个多项式层级 `PH`.
  - 如果你直观上感觉, 一个计数的谕示好像不该如此明显地强大,
    那么, 好吧, 它本来就不该是明显的!
* `户田定理`震惊了所有人.
  - 遗憾的是, 我没时间在本书中讨论`户田定理`的证明.
  - 但在后文中, 我还会时不时用到该定理.
* 无论如何, 就复杂度类而言, 我们先前的讨论意味着
  $$ P^{\sharp P} \subseteq IP $$:
  - 在一个`交互式`协议中,
    梅林可以让亚瑟相信任何 `#P` 问题的解, 乃至任何
    $$ P^{\sharp P} $$
    问题 (因为亚瑟可以用梅林来代替 `#P` 谕示).
  - 根据`户田定理`, 这意味着 `IP` 包含 `PH`.

## 时间旅行

* 让我们来谈谈更有趣的一种时间旅行吧, 回到过去的那种.
  如果你读过科幻小说, 那么你可能已经听说过`"封闭类时曲线"`
  (closed timelike curve, CTC) 的概念了:
* 如果在这种时空区域中**局域地**看时间,
  那么时间似乎总在完美地按照物理学定律稳步推进;
  然而, 如果**全局地**看时间,
  你就会发现时间具有**环**的**拓扑结构**.
* 这样一来, 在前往足够远的未来时, 你会与现在重逢.
  可以说, 这基本上就是在以更加天马行空,
  更加爱因斯坦的方式来说"回到过去的时间旅行".

---

* 顺便一提, 这里还有一个有趣的元问题:
  `物理学家们为什么很难提出一个关于引力的量子理论?`
  - 通常给出的技术性答案是, 与 (比如) 麦克斯韦方程组不同,
    广义相对论是不可**重正化**的.
  - 但我觉得还有一个更简单的答案,
    它对像我这样的愚蠢的门外汉来说要好理解得多.
* 问题的真正核心在于广义相对论是关于时空本身的理论,
  所以, 一个关于引力的量子理论将不得不涉及时空的叠加和波动.
  你期望这样的理论去回答的事情之一就是 `CTC` 能否存在.
  因此, 量子引力至少得像判定 `CTC` 是否可能这类问题一样难.
  - 从这个意义上说, 量子引力看上去是`"CTC 难"`的!
* 甚至我都看得出来, 这根本不可能是一个能简单解决的问题.
  即使 `CTC` 的确是不可能的, 除非能出现一些影响深远的新洞察,
  否则它们也不会被证明是不可能的.
  - 当然, 这仅仅是一个普遍问题的实例:
  - 没有人能真正清楚地知道用量子力学的方式对待时空本身是什么意思.
* 在我的研究领域中, 我们从来不会问一个物理客体存在与否;
  我们会假设它存在, 然后看看用它可以做什么样的计算.
  因此, 从现在开始, 我们将假设 `CTC` 存在.
  - 这对计算复杂性来说有什么后果呢?
  - 令人惊讶的是, 我能够给出一个明确而具体的答案.
* 所以, 你会如何利用一个 `CTC` 来加快计算呢?
  首先, 让我们考虑一个天真的想法: 计算出答案,
  然后在你的计算机开始计算之前把答案及时发回来.
  - 从我的角度来看, 这种"算法"即便按它自己的方式考虑都是不可行的.
  - 即使有古怪如时间旅行这样的东西,
    我们也可以明确地排除某些想法, 这真不错!

---

* 对, 输出的分布应该与输入的分布一样.
  我们应该加人多伊奇的`"因果一致性"` (causal consistency) 的要求:
  - `CTC` 内发生的计算必须将输入的概率分布映射到它自身.
  - 在确定型物理学中, 我们知道这种一致性并非总能实现.
  - 这只是陈述祖父悖论的另一种方式.
* 但只要我们用概率理论, 那么, 有一个基本事实就是,
  每一个马尔可夫链至少会有一个平稳分布.
  - 在祖父悖论这种情况下, 唯一的解决方法是,
    你以 `1/2` 的概率出生, 而一旦你出生了,
    就回到过去杀了自己的祖父;
  - 这样一来, 你回到过去杀你祖父的概率是 `1/2`,
    因此你出生的概率也是 `1/2`.
  - 一切都是一致的, 不存在悖论.

---

* 有趣的是, 多伊奇的观点是, `CTC` 必须`不能`解决困难的计算问题.
  因为如果它们可以, 那就会违反多伊奇所谓的"进化原理",
  即`"知识只能通过进化过程出现"`的原则
  - 或用计算机科学的话来说,
    `NP` 完全问题和与之类似的问题不应该"就像被施了魔法那样被解决".
* 因此多伊奇会说, 不管最终的物理学定律是什么, 它一定会接受这些"愚蠢"的不动点,
  从而让大自然不必通过解决 `PSPACE` 完全问题来保持 `CTC` 的一致性.
* 就个人而言, 我觉得这是一种奇怪的论证方式. 如果存在 `CTC`,
  很明显, 它们会迫使我们重新审视自己关于`空间`, `时间`,
  `因果关系`以及其他事物的理解.
  - 究竟是什么让多伊奇如此确信,
    进化原理能够在这样的剧变中得以生存?
  - 要知道, 还有那么多看上去很明显的直觉, 最后难以幸存!
* 与此相反, 为什么不简单地猜想是 `CTC` 不存在?
  这样就可以坚持进化原理和其他许多东西了!
  这个猜想似乎跟我们所知道的一切都可以完美兼容.

## 宇宙学和复杂度

* 我将从"纽约时报模式"的宇宙论开始
  - 这是你一直能在科普文章上读到的东西
* 这种宇宙论称, 一切都取决于`宇宙中物质的密度`.
  参数 `Ω` 表示宇宙的物质密度, 如果它是大于 `1` 的,
  那么宇宙就是`封闭的`.
  - 也就是说, 宇宙的物质密度足够高,
    以至于在大爆炸 (Big Bang) 之后必须有一个大挤压 (Big Crunch).
  - 此外, 如果 `Ω > 1`, 那么时空会具有**球形**的几何 (正曲率).
* 如果 `Ω = 1`, 那么时空的几何就是**平坦**的,
  而且也不会有大挤压.
* 而如果 `Ω < 1`, 那么宇宙就是开放的,
  并具有**双曲**几何.
  - 该观点认为, 一共就有这**三种**情况.

---

* 然而, 这只是对宇宙进行`"球 - 平坦 - 双曲"`的简单三分法的一个错误所在.
  另一个错误是, 宇宙的**几何**与**拓扑**结构是两个相互独立的问题.
* 仅仅假设宇宙平坦, 并不意味着它就是无限的.
  如果宇宙有一个恒定的正曲率,
  那么这将意味着它是有限的.
  - 想想地球吧, 一旦知道它有恒正的曲率, 你就会认为它是圆的.
* 我的意思是说, 是的, 它能弯曲到你看不到的无穷远处.
  但假设地球的曲率是均匀的, 从数学上来讲,
  它就必须得弯曲成一个球体或某个其他更复杂的有限形状.
* 然而, 如果空间是平坦的, 那么这并没有说明它是有限的,
  还是无限的.
  - 这就好比在一个视频游戏里, 当游戏人物离开屏幕的一端时,
    他会在另一端再次出现.
* 这跟几何上的平坦完全相容, 但会对应到一个封闭的拓扑结构上.
  于是很不幸, `"宇宙是有限的, 还是无限的?"`
  - 这个问题的答案, **我们并不知道**.

---

* 学生: 所以, 如果时间始于某个有限点, 那么时间就是有限的.
  但是, 相对论告诉我们, 空间和时间实际上没有什么区别, 不是吗?
* 斯科特: 不, 它并没有给出你所说的结论. 它告诉我们,
  时间和空间是以一种非平凡的方式相互关联的, 但是,
  时间和空间有着不同的**度规符号**.
* 顺便一提, 这是我的一颗"眼中行". 其实有一个物理学家曾问过我,
  既然"相对论告诉我们空间和时间是相同的",
  那么 `P` 怎么就和 `PSPACE` 不同呢? 嗯, 问题在于,
  **时间的度规符号是负的**. 这与下述事实相关:
* 你可以在空间中前后自由地行走, 但对于时间来说,
  你只能往前走. **CTC** 的关键在于,
  它允许你回到过去, 并且作为后果,
  时间和空间作为计算资源真的将变得等价.
  - 但如果对于时间来说, 你只能朝一个方向前行,
    那么它与空间就是不一样的.
* 学生: 那么在空间里, 我们是否可以通过走足够远来回到原点呢?
* 斯科特: 就算你的胳膊足够长, 你能不能把它从面前伸出去,
  但还能打到你自己的后脑勺呢? 正如我之前说过的, 答案是:
  我们不知道.
* 学生: 至少对于质量传播来说, 我觉得人们相信空间是有限的,
  因为有大爆炸.
* 斯科特: 这是一个关于**大爆炸的误解**.
  大爆炸**不是**发生在空间中一点的事件, 大爆炸是创建时空本身的事件.
  这里有一个标准的类比:
  - 星系是气球上的一些小斑点, 当气球膨胀时, 这些点并不是都抢着远离对方,
    而只是气球变得越来越大.
  - 如果时空是开放的, 那么比起一堆物质充塞其中, 更有可能的情况是,
    实际上在大爆炸的那一刻, 就已经有了无限多的物质.
    随着时间的推移, 无限宇宙被拉伸, 但在时间轴上的任意一点上,
    它仍然会无限地继续下去.
  - 看一看**局域视界**, 我们会看到那些东西在迅速地互相远离,
    但这只是因为我们不能跨过视界, 看看在它之外有什么东西.
  - 所以, 大爆炸**不是**发生在一定时间和地点的某种爆发,
    它是整个时空流形的开始.
* 学生: 可是, 质量和能量不是不能比光速传播得更快吗?

---

* 所以, 这就是物理学家们描述宇宙常数的方式.
  但我会这样描述它:
  - 它仅是可以在一个计算中使用的**最大比特数的倒数**!
  - 更确切地说:
  - $$ 最大比特数 = \frac{3 \pi}{\wedge} $$
* 用`普朗克`单位, 宇宙常数大约是
  $$ 10^{-121} $$,
  所以我们发现
  $$ 10^{122} $$
  大概是在物理世界中能被用于计算的最大比特数.
  - 我们是怎么得到宇宙常数的这种解释的呢?

* 学生: 宇宙常数的定义是什么?
* 斯科特: **真空能量**. 再说一次, 这是物理学概念.
  人们不会去定义东西, 而是去观测它们.
  - 物理学家实际上并不知道什么是真空能量, 只是知道它就在那里.
  - 它是真空的能量, 并有很多不同的可能来源.
* 学生: 这是一个平均吗?
* 斯科特: 嗯, 没错, 但它似乎非常接近常数
  - 无论人们在哪里测量它, 并且, 它似乎也不怎么受时间影响.
    与 `"它在各处都相同"` 这一假设存在偏差的结果, 还没出现过.
  - 可以这样想: 在真空中, 总有`粒子-反粒子`对的形成和湮灭.
    真空是一个极其复杂的东西! 因此,
    它应该有非零能量这一点也许并不奇怪.
  - 事实上, 量子场论的难题不是解释为什么有一个宇宙常数,
    而是解释为什么该常数不比现在的值大
    $$ 10^{120} $$
    倍!
  - 一个`"天真"`的量子场论论证将预测:
    整个宇宙应该会在一瞬间爆炸.

---

* **全息界**的概念指出, 在任何时空区域内, 能够放入该区域的熵值
  - 或者, 直到一个小常数, 能在其中存储的比特数至多等于以
    `普朗克单位` 计算的 `该区域表面积除以 4`.
  - 惊人之处在于, 你可以存储的比特数不会随体积增长而增长,
    而是随表面积增长而增长.
  - 我可以展示一下推导过程, 更确切地说, 是物理学家们认为的推导过程.

* 学生: 这一推导有没有告诉你, 为什么是表面积除以 `4`,
  而不是 `3` 之类的数?
* 斯科特: **弦论**研究者相信自己找到了一种解释.
  这是他们的一大成功! 他们喜欢用这个解释在其他量子引力方法面前逞威风.
  对于研究**圈量子引力**的人来说, 这一常数推出来是有误的,
  他们必须通过伊米尔齐参数 (Immirzi parameter) 来手动修正.
  - 补充笔记: 自 `2006` 年以来, **圈量子引力**阵营中
    有人声称解决了这个问题.
