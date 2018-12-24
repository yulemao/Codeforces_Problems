# Data Structure

### Codeforces 1087F Rock-Paper-Scissors Champion

**(Rating 2700)**

[http://codeforces.com/contest/1087/problem/F](http://codeforces.com/contest/1087/problem/F)

题目大意为有 $n$ 个人参加石头剪刀布大赛，每个人从比赛开始到结尾都只会出同一个手势。你可以随意安排相邻的两个人进行对战，输掉的人将被淘汰。如果两个人出的手势相同，则用抛硬币决定胜负。最后一个剩下的人将会成为冠军。假设你可以控制赛程和抛出硬币的结果，$q$ 次询问，每次单点修改一个位置上的人的手势，问有多少个人可以获得冠军。

先来考虑第 $i$ 个人能否是冠军，那么一定有 $[1, i - 1]$ 和 $[i + 1, n]$ 中都存在一种合并方法使得合并出来的手势不克制这个人。假如在某一个区间中存在克制这个人的手势，那么只要存在被这个人的手势克制的手势存在才可以保证合并出来的区间不存在克制第 $i$ 个人的手势。

现在来考虑全局，那么对于任意一种手势，只需要找到另外两个手势的出现的最大位置和最小位置，分情况讨论，找到一个可以使得这个手势保留下来的区间，查询区间内有多少个该种手势即可。

对于修改操作，使用线段树来维护区间个数，最大位置和最小位置即可