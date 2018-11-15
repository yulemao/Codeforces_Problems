Kv# Graphs

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