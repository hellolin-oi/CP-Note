---
comments: true
---

# 平衡树

前置知识 [BST](./bst.md)。

平衡树就是一棵满足每个结点左子树右子树高度差不超过 $1$ 的 BST。

## FHQ Treap（无旋 Treap）

Treap = Tree + heap。

Tree 当然就是 BST，而 Heap 的意思是堆，也就是每一个结点都有优先级 $p_i$。一般来说这是个建树的时候搞的随机数。

一个结点的优先级必须比他的儿子小（或者相等，但概率很小）。

FHQ Treap 的两大特点就是分裂和合并。

### 分裂

给一个 $x$，分裂两棵 Treap，满足第一棵所有结点值小于等于 $x$，第二棵都大于等于 $x$：

- 从根节点开始；
- 若子树根节点值大于 $x$，那么将根和右子树归到第一棵，递归左子树；
- 同样若根节点值小于等于 $x$，那么将根和左子树归到第二棵，递归右子树。

### 合并

给两棵 Treap，满足第一棵所有结点值小于等于第二棵，合并过程：

- 从两棵树的根节点开始，设两树根节点分别为 $a$ 和 $b$；
- 若 $p_a<p_b$，$a$ 成为新树的根，递归 $a$ 的右子树以及 $b$ 的整棵树；
- 若 $p_a\ge p_b$，$b$ 成为新数的根，递归 $a$ 的整棵树以及 $b$ 的左子树。

### 插入

先以 $x$ 分裂，再合并第一棵树、$x$、第二棵树。

### 删除

以 $x$ 和 $x-1$ 分裂，之后合并第一棵树、第二棵左子树、第二棵右子树、第三棵树。

### 查询排名

二分。

