---
layout: postcn
title: "python:杯子量水问题，思路和通用解(CheckIO)"
date: 2018-01-31 00:09:27 +0800
lang: cn
nav: post
category: python
tags: [algorithm]
---

* content
{:toc}


有两个杯子a,b，容量是已知的，但是不相同。  
现在需要称量x容量的水。  
如何进行操作？  
<!-- more -->

## 问题内允许的操作

1. 从外部接满a或b
2. 将a或b倒掉
3. 将a倒入b或将b倒入a，直到倒空或倒满

## 思路

问题看似复杂，其实分歧点只有1个，即最开始填满哪个杯子。  
后续所有的状态，都有对应的唯一许可的操作。  
上面的两条是根据每种状况操作导致的后果来推论的，如果不按照这样的规则，会导致操作上的循环或毁灭之前的操作，这显然是我们不希望的。  
下面给出了例子：

#### 先倒满b时，可行的操作

+ 在b满的时候，将b倒入a
+ 在a满的时候，将a倒掉
+ 在b空的时候，接满b
+ 在a空的时候，将b倒入a

结论：b→a，→b，a→

#### 先倒满b时，不可行的操作

+ 将a倒入b - 保证b满唯一的可能性就是接水
+ 将b倒掉 - b满唯一的可能性就是接水，所以刚接完水是不可能倒掉的
+ 给a接水 - a的水源只能来自b

结论：a→b，→a，b→

#### 先倒满b时，结论

上述已经包含了所有可能的操作。因此可以总结下面的点。  
在你看的时候，思考以下为什么？  

+ 一开始倒满的杯子，里面的水永远不会被倒掉
+ 一开始空的杯子，永远不会接水
+ 只会出现一开始满的杯子向一开始空的杯子倒水

#### 先倒满a时

同b

## 思考问题

如何判断先倒满哪个会产生最优结果？

{% highlight ruby lineno %}
'''
倒水问题
0代表水池
1代表试管1
2代表试管2
求测量出x大小的水的每一步骤
'''


def checkio(cup_a, cup_b, need):

    # sort
    _ori = '0'
    if cup_a > cup_b:
        _big = '1'
        _sma = '2'
        cup_a, cup_b = cup_b, cup_a
    else:
        _big = '2'
        _sma = '1'

    # handle
    # 大优先思路：ab必有1空或1满
    # a永不入b
    # 水源永不填满a
    # b永远不会倒掉
    cup_a_water = 0
    cup_b_water = cup_b
    steps_b = [_ori+_big]
    while cup_a_water != need and cup_b_water != need:
        if not cup_b_water:
            # b空必满
            cup_b_water = cup_b
            steps_b.append(_ori+_big)
        elif not cup_a_water:
            # a空必b入
            cup_a_water = min(cup_a, cup_b_water)
            cup_b_water = max(cup_b_water - cup_a, 0)
            steps_b.append(_big+_sma)
        elif cup_b_water == cup_b:
            # b满必入a
            cup_b_water -= (cup_a - cup_a_water)
            cup_a_water = cup_a
            steps_b.append(_big+_sma)
        elif cup_a_water == cup_a:
            # a满必倒
            cup_a_water = 0
            steps_b.append(_sma+_ori)
        else:
            # ..
            print('error')
            break
    # 小优先思路，同上
    cup_a_water = cup_a
    cup_b_water = 0
    steps_s = [_ori+_sma]
    while cup_a_water != need and cup_b_water != need:
        if not cup_a_water:
            # a空必满
            cup_a_water = cup_a
            steps_s.append(_ori+_sma)
        elif not cup_b_water:
            # b空必a入
            cup_b_water = cup_a_water
            cup_a_water = 0
            steps_s.append(_sma+_big)
        elif cup_a_water == cup_a:
            # a满必入b
            cup_a_water = max(cup_a_water - cup_b + cup_b_water, 0)
            cup_b_water = min(cup_b, cup_b_water + cup_a)
            steps_s.append(_sma+_big)
        elif cup_b_water == cup_b:
            # b满必倒
            cup_b_water = 0
            steps_s.append(_big+_ori)
        else:
            # ..
            print('error')
            break
    if len(steps_b) > len(steps_s):
        return steps_s
    else:
        return steps_b


checkio(5, 7, 6) == ['02', '21', '10', '21',
                     '02', '21', '10', '21', '02', '21']
checkio(3, 4, 1) == ["02", "21"]
checkio(8, 5, 2)  # 02,21,02,21
checkio(2, 1, 1)

{% endhighlight %}