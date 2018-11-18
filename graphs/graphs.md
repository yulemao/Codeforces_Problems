# Graphs

### Codeforces 1070A Find a Number

**(Rating 2200)**

[http://codeforces.com/problemset/problem/1070/A](http://codeforces.com/problemset/problem/1070/A)

题目大意为需要你找到一个能被 $d$ 整除且各位数字之和为 $s$ 的最小的数。

定义点 $(x, y)$ 为数字总和为 $x$，对 $d$ 取模得 $y$，从点 $(x, y)$ 向点 
$(x + i, (y * 10 + i) \space mod \space d)$ 建边 $(0 \leq i \leq 9)$。则从 $(0, 0)$ 到 $(s, 0)$ 的最短路径即为答案。使用SPFA或其他最短路算法即可解决。

### Codeforces 1045C Hyperspace Highways

**(Rating 2500)**

[http://codeforces.com/problemset/problem/1045/C](http://codeforces.com/problemset/problem/1045/C)

题目大意为给你一个 $N$ 个点 $M$ 条边的无向图， $Q$ 次询问两点之间距离，保证任何一个简单环（每个点只经过一次）上所有的点互相有边相连。

如果要通过一个子完全图，则需要通过两个点，因此可以使用 $BFS$ 对所有点进行分层建树，则每个子完全图被分为两部分，一个单独的点和其余所有的点连边，则求树上两点间距离时通过子完全图的部分距离计算出来的结果和图上结果相同。对于可能在子完全图内的边，只有两点的 $LCA$ 和两个子节点之间可能是子节点之间有边，判断是否有边相连即可。

### Codeforces 1076D Edge Deletion

**(Rating 1800)**

[http://codeforces.com/problemset/problem/1076/D](http://codeforces.com/problemset/problem/1076/D)

题目大意为给你 $n$ 个点 $m$ 条边的带边权无向图，设每个点到 $1$ 的最短距离为 $d_i$ ，你需要将边删到小于等于 $k$ 个，最大化删除后的图中 $d_i$ 和原图一样的点数

使用最短路算法生成一个最短路树，删除叶子节点使得边数小于 $k$ 即可

### Codeforces 1051F The Shortest Statement

**(Rating 2300)**

[http://codeforces.com/problemset/problem/1051/F](http://codeforces.com/problemset/problem/1051/F)

题目大意为给你 $n$ 个点 $m$ 条边的无向带边权图，$q$ 次询问，求 $x$ 到 $y$ 的最短路，保证 $m - n \leq 20$

对于整个图来说，只有不到 $20$ 个点不在图的一个生成树上。因此对于最短路为树上路径的询问，直接使用树上最短距离例如倍增等算法解决即可。对于其他的路径，一定是最少经过一条不在树上的边，预处理不在树上的边的各个端点到其他所有点的最短路，枚举经过的点即可。

### Codeforces 1042F Leaf Sets

**(Rating 2400)**

[http://codeforces.com/problemset/problem/1042/F](http://codeforces.com/problemset/problem/1042/F)

题目大意为给你一个 $n$ 个节点的树，问你把所有的叶子节点最少分成几个集合，可以使得每个集合中的任意两个叶子节点在树上距离小于 $k$

选取任意一个非叶子节点进行 $DFS$ ，记录每个点中离得最远的叶子节点位置，如果最大的两个加和大于 $k$ ，剪掉就可以了。

### Codeforces 1038E Maximum Matching

**(Rating 2400)**

[http://codeforces.com/problemset/problem/1038/E](http://codeforces.com/problemset/problem/1038/E)

题目大意为给你 $n$ 个块，每个块儿两侧有颜色，中间有权值，每个块儿可以随意反转，但只有相同的颜色才能接到一起。问构造出来权值和最大的串的权值为多少。

#### 题解一

采用 $Floyd$ 的思想，设 $F[l][r][x][y]$ 为区间 $[l, r]$ ，左右颜色分别为 $x$ 和 $y$ 的权值最大值，枚举合并区间的点和颜色，合并即可。

$$f[l][r][x][y] = max(f[l][r][x][y], f[l][i][x][a] + f[i + 1][r][a][y]);$$

$$f[l][r][x][y] = max(f[l][r][x][y], f[i + 1][r][x][a] + f[l][i][a][y]);$$

#### 题解二

Create a graph with $4$ nodes $1−4$

representing the colors. Then the value of a block serves as an edge between the two colors of that block.

Then the question reduces to finding an euler tour in the graph with the maximum sum of edges traveled. An euler tour may not exist with all the given edges, so the question is: Which edges do we remove?

One can note that there are $16$ types of edges. (Edges connecting $1$ to $1$ , $1$ to $2$ and so on). There may be multiple edges of a specific type, however atmost $1$ of it will be removed to form a valid euler tour. This is because if we have $2x+y$ edges between node $A$ and node $B$ where $0 \leq y \leq 1$, we can simply loop back and forth between $A$ and $B$ $x$ times to end up at the node we started from.

Since there are only $16$ types of edges, we can use bitmask to iterate over all the possibilities, and checking whether an euler tour exists in the graph with the marked edges removed (if there are multiple edges between node $A$ and node $B$

, we remove only one edge, the one with the least value).

Refer to author's solution/any AC codes to see implementation details.

Overall Complexity: $O(2 ^ {16} \times n)$

Bonus: Can you solve this question in $O(n ^ 2)$
? How about $O(n)$?

### Codeforces 1029E Tree with Small Distances

**(Rating 2200)**

[http://codeforces.com/problemset/problem/1029/E](http://codeforces.com/problemset/problem/1029/E)

题目大意为给你一棵根节点为 $1$ 的树，问你最少连多少条边，使得所有点与 $1$ 的最短距离小于 $2$

直接贪心，从下往上走对于每个点，若它有一个儿子与 $1$ 节点的距离大于 $2$ ,那么它就需要和 $1$ 连边，否则不连即可。