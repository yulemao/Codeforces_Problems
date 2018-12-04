# DP

### Codeforces 1032E The Unbearable Lightness of Weights

**(Rating 2300)**

[http://codeforces.com/problemset/problem/1032/E](http://codeforces.com/problemset/problem/1032/E)

题目大意为给你 $n$ 个砝码，你知道所有的砝码的重量各是多少，你能询问一次是否存在 $K$ 个砝码重量为 $w$。问能确定所有的砝码重量各是多少的最大的 $k$ 是多少。

使用动态规划，定义 $f[i][j][k]$ 为已经访问到重量为 $i$ ，有 $j$ 个砝码，总重量为 $k$ 有多少种情况，背包即可。答案即为同样重量的 $k$ 个砝码只有 $1$ 种组合方法的 $k$ 。注意如果只有两种砝码，则全部都可以被识别出来，因为剩下的也都知道是啥了。
