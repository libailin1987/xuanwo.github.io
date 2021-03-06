title: CodeVS 1012 最大公约数和最小公倍数问题
date: 2014-11-1 10:17:25
tags: [ACM, CodeVS, C, 数论]
categories: Exercise
toc: true
---
# 题目	
源地址：http://codevs.cn/problem/1012/

# 理解
自然是水题= =。只要用一个循环就可以搞定，最大公约数用gcd，最小公倍数就是i*j/gcd(i,j)，没有什么问题。
不过这个题意不是很清晰，是否为同一组数字的判断并没有讲到。实际上，`3 60`和`60 3`是两组数组。这个理解上的问题，导致我的结果一直都是标准答案的一半，折腾了一会儿。
除此之外，这个简单的思路还有很多可以优化的地方，比如在判断了gcd是否等于x之后，后面判断最小公倍数只要使用i*j/x就可以了；还有，一开始令i=x之后，后面每一次都递增x就可以保证i与j始终为x的约束，但注意，还是要用gcd来判断最大公约数是不是x；过题之后找了一下题解，发现有人提出，循环的最大值是sqrt(y)，稍微想了想，确实如此，这个优化也能省下很多循环。

<!-- more -->

# 代码
```
#include <cstdio>
#include <cstdlib>
#include <cstring>
#include <cmath>
#include <ctime>
#include <iostream>
#include <algorithm>
#include <string>
#include <vector>
#include <deque>
#include <list>
#include <set>
#include <map>
#include <stack>
#include <queue>
#include <numeric>
#include <iomanip>
#include <bitset>
#include <sstream>
#include <fstream>
#define debug "output for debug\n"
#define pi (acos(-1.0))
#define eps (1e-8)
#define inf (1<<28)
#define ll long long int
using namespace std;

int x,y;
int ans=0,flag=0;

int gcd(int a,int b)
{
    return b==0?a:gcd(b,a%b);
}

int main(int argc, char const *argv[])
{
    while(~scanf("%d%d", &x,&y))
    {
        if(x>y) swap(x,y);
        ans=0;
        for(int i=x; i<=y; i+=x)
        {
            for(int j=i; j<=y; j+=x)
            {
                if(i*j/x==y&&gcd(i,j)==x)
                {
                    ans++;
                }
            }
        }
        printf("%d\n", ans<<1);
    }
    return 0;
}
```

# 更新日志
- 2014年11月1日 已AC。