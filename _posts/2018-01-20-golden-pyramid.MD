---
layout: postcn
title: "python:数字金字塔，这是动归吗？(CheckIO)"
date: 2018-01-20 10:52:29 +0800
lang: cn
nav: post
category: python
tags: [number]
---

* content
{:toc}


经典的数字金字塔问题，以及解法。  
Checkio说这道题锻炼动归。  
然而这是动归？  
<!-- more -->
### 问题描述
这似乎是个经典问题：  
有一个数字组成的金字塔，第一层有1个数字，向下每一层都会多一个数字，用列表或元组等存储。  
下金字塔的过程中，只能向半格下，或向右半格下。表现为index就是要么index不变，要么index+1。  
假设每到一个数字，就加上这个数字，那么从塔顶到底的路线里，哪一个路线的最终数字是最大的？  

### 解法思路
1. 看倒数第二行，某个数，下方有倒数第一行的2个数，将较大的那个加上来。
2. 按照1处理完倒数第二行的没个数，得到新的倒数第二行。
3. 按照1来处理倒数第三行，注意下方变成了新的倒数第二行。
4. 按照上述处理到第一行。
5. 最新的第一行的第一个（也是唯一一个）数，就是最大值。

### 问题
解法似乎并没有用到动态规划，但没想到递归的解决方法。  
上述解法实际是倒推法，也就是从结尾推向头，因为向下的分支会增加，不容易判断，但是向上的话则是减少的，就比较容易。


{% highlight ruby lineno %}
'''
金字塔路线
'''

def count_gold(pyramid):
    '''最大的下金字塔路线'''
    hight = len(pyramid)
    row_replace = list(pyramid[-1])
    row_now = [0]*hight
    for i in range(hight-2, -1, -1):
        for k in range(len(pyramid[i])):
            row_now[k] = pyramid[i][k] + max(row_replace[k], row_replace[k+1])
        row_replace = row_now[:]
    return row_replace[0]


assert count_gold((
    (1,),
    (2, 3),
    (3, 3, 1),
    (3, 1, 5, 4),
    (3, 1, 3, 1, 3),
    (2, 2, 2, 2, 2, 2),
    (5, 6, 4, 5, 6, 4, 3))) == 23

assert count_gold((
    (1,),
    (2, 1),
    (1, 2, 1),
    (1, 2, 1, 1),
    (1, 2, 1, 1, 1),
    (1, 2, 1, 1, 1, 1),
    (1, 2, 1, 1, 1, 1, 9))) == 15

assert count_gold((
    (9,),
    (2, 2),
    (3, 3, 3),
    (4, 4, 4, 4))) == 18
{% endhighlight %}

### 读题错误产生的错误解法
判断下面的两个数，选择一个可以走的路线……  
姑且留下来了，最为黑历史。

{% highlight ruby lineno %}
'''    gold = pyramid[0][0]
    k = 0
    p_o = pyramid[0][0]
    for i in range(1,len(pyramid)):
        p_one = pyramid[i][k]
        p_two = pyramid[i][k+1]
        if p_o == p_two:
            gold += p_two
            k += 1
            print(p_two,k)
        elif p_o == p_one:
            gold += p_one
            print(p_two,k,'er')
        elif p_one > p_two:
            gold += p_one
            p_o = p_one
            print(p_one,k)
        else:
            gold += p_two
            k += 1
            p_o = p_two
            print(p_two,k,'si')
    print(gold)
    '''
{% endhighlight %}
