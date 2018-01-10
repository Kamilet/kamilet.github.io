---
layout: posten
title: "python:sMartix-A lightweight module for Matrix"
date: 2018-01-06 23:53:47 +0800
lang: en
nav: post
category: python
tags: [python, module]
---

* content
{:toc}


A lightweight module for handling Matrix.
Built For Real Number.
Plural actually available, but complete test haven't done...
All items should be numbers or letters in matrix.
Please use Numpy for more complex situation!
<!-- more -->
Instruction: [sMartix](https://github.com/Kamilet/Simple-Matrix-python)

# Simple-Matrix-python
A lightweight module for simple Matrix operation. Simple and easy to use.  
轻量级的简单矩阵处理模块，使用起来比较方便。  

+ English Documentation [Jump](#english-documentation)
+ 简体中文使用指南 [转到](#简体中文使用指南)

---

# English Documentation

Thanks for checking this module.  
It's my first one. Hopefully it's useful for you.  
**1 Class** and **20 functions** are in this module,  
which will help you with basic opreations on Matrixs.  

>Please remember: All numbers of rows and columns start from ZERO.
>So a matrix 'A' with m rows and n columns,
>the last item should be 'A\[m-1\]\[n-1\]'.

Here are introductions for all functions:  

## Index

+ Matrix Building
    + **Generator:** [sm_gen()](#generator)
    + Complementor: [sm_cons()](#complementor)
+ Single Matrix Basic Opreation
    + **Deep copy**: [sm_copy()](#deep-copy)
    + Legality check: [sm_check()](#legality-check)
    + Number check: [sm_numcheck()](#number-check)
    + Convert to numbers: [sm_number()](#convert-to-numbers)
    + Convert to strings: [sm_str()](#convert-to-strings)
    + **Negative all elements**: [sm_negative()](#negative-all-elements)
    + Absolute value: [sm_abs()](#absolute-value)
+ Single Matrix Operation
    + **Matrix transpose**: [sm_trans()](#matrix-transpose)
    + Matrix conjugate: [sm_conj()](#matrix-conjugate)
    + Matrix conjugate transpose: [sm_con_trans()](#matrix-conjugate-transpose)
    + **Determinant**: [sm_det()](#determinant)
    + **Inverse Matrix** : [sm_inverse()](#inverse-Matrix)
    + **Algebraic Remainder**: [sm_alge()](#algebraic-Remainder)
+ Class Smartix()
    + OO Legality check: [Smatrix()](#oo-legality-check)
    + Clean Matrix: [Smatrix().clean()](#clean-matrix)
    + OO Legality check: [Smatrix().check()](#oo-legality-check-1)
    + OO Number check: [Smatrix().numcheck()](#oo-number-check)
    + **Print by rows**: [Smatrix().view()](#print-by-rows)
    + OO Negative all elements: [Smatrix().negative()](#oo-Negative-all-elements)
    + **Rotate**: [: [Smatrix().rotate()](#rotate)
    + Transpose: [Smatrix().trans()](#transpose)
    + Conjugate: [Smatrix().conj()](#conjugate)
    + Conjugate transpose: [Smatrix().con_trans()](#conjugate-transpose)
    + OO Determinant: [Smatrix().det()](#oo-determinant)
    + Inverse: [Smatrix().inverse()](#inverse)
    + **Find a segment of a certain length in the matrix (Gomoku system)**: [Smatrix().find()](#find-a-segment-of-a-certain-length-in-the-matrix)
    + **Matrix trace**: [Smatrix()trace()](#matrix-trace)
+ Multiple Matrix Operation
    + **Sum All**: [sm_sum()](#sum-all)
    + Subtraction: [sm_minus()](#subtraction)
    + **Multiplication with matrixs and numbers**: [sm_multis()](#multiplication-with-matrixs-and-numbers)
    + Multiply: [sm_multi_mm()](#multiply)
    + Multiply with number: [sm_multi_mn()](#multiply-with-number)

***

## Matrix Building

#### Generator
```python
def sm_gen(row: int = 1, colume: int = 1, items=0, unit=False, eye=False):
```
+ row - Number of row, for A(m\*n) you need set to m
+ colume - Number of colume, for A(m\*n) you need set to n
+ items - For filling
+ unit
    + True - Generate a unit matrix: row\*row
+ eye
    + True - Ditto
Return a new matrix(list).

#### Complementor
```python
def sm_cons(matrix, items=0, echo=0):
```
+ matrix - A matrix need to be complement. For example:\[\[1,2\],\[1\]\]
+ items - For filling
+ echo
    + True - Tell you are running complementor
Return a new matrix(list).

***

## Single Matrix Basic Opreation

#### Deep copy
```python
def sm_copy(matrix):
```
Deep copy, just use it whenever you need change original matrix.  
Return a new matrix(list).

#### Legality check
```python
def sm_check(matrix):
```
Check if every rows are in same length.  
If True, return a tuple as (row, column), you can use as bool.  

#### Number check
```python
def sm_numcheck(matrix):
```
Check if all items are numbers. Run a sm_check() automatically.   
Return True or false.  

#### Convert to numbers
```python
def sm_number(matrix, force=False):
```
+ force
    + True - Letters and '' will be 0
Return a new matrix(list).

#### Convert to strings
```python
def sm_str(matrix):
```
Return a new matrix(list).

#### Negative all elements
```python
def sm_negative(matrix):
```
Return a new matrix(list).

#### Absolute value
```python
def sm_abs(matrix):
```
Return a new matrix(list).

***

## Single Matrix Operation

#### Matrix transpose
```python
def sm_trans(matrix):
```
Exchange lines and columns.  
Return a new matrix(list).

#### Matrix conjugate
```python
def sm_conj(matrix):
```
Return a new matrix(list).

#### Matrix conjugate transpose
```python
def sm_con_trans(matrix):
```
Return a new matrix(list).

#### Determinant
```python
def sm_det(matrix, force=False):
```
+ force
    + True - opreat even low != column
    + False - only opreat when low == column
Return a number.

#### Inverse Matrix
```python
def sm_inverse(matrix):
```
Return a new matrix(list).

#### Algebraic Remainder
```python
def sm_alge(matrix, row:int , colume:int):
```
+ row - the row should be ignored
+ colume - the colume should be ignored
Return a number.

***

## Class Smartix()

#### OO Legality check 
```python
class Smatrix:
def __init__(self, matrix, allnumber=False):
```
+ allnumber
    + True - run sm_numcheck()
    + False - only sm_check()

#### Clean Matrix
```python
def clean(self, items=0, echo=False):
```
+ items - clean with this
+ echo
    + True - tell you it's cleaned
Return a new matrix(list).

#### OO Legality check 1
```python
def check(self):
```
Same function as sm_check().

#### OO Number check
```python
def numcheck(self):
```
Same function as sm_numbercheck().

#### Print by rows
```python
def view(self):
```
Just pring, no return.

#### OO Negative all elements
```python
def negative(self):
```
Same function as sm_negative().

#### Rotate
```python
def rotate(self, method='exchange', step: int=1, force=False):
```
+ method
    + exchange - Exchange rows and columns
    + ex | transpose | tr - Ditto
    + clockwise - Rotate in clockwise direction
    + clock - Ditto
    + mirrorrow - mirror in horizontal direction
    + mr | mh | mirror - Ditto
    + mirrorcolume - mirror in vertical direction
    + mc | mv - Ditto
+ step - How many times to run
+ force
    + True - If unsuccessful, an error will be asserted
Return a new matrix(list).

#### Transpose
```python
def trans(self):
```
Same function as sm_trans().

#### Conjugate
```python
def conj(self):
```
Same function as sm_conj().

#### Conjugate transpose
```python
def con_trans(self):
```
Same function as sm_con_trans().

#### OO Determinant
```python
def det(self):
```
Same function as sm_det().

#### Inverse
```python
def inverse(self):
```
Same function as sm_inverse().

#### Find a segment of a certain length in the matrix
```python
def find(self, string:str='', length=2, direct='all', echo=False):
```
Try to fin a segment that repeats, such as \['4','4','4'\] in any direction!
+ string - The single string, can be a number
+ length - How many times repeats
+ direct
    + all - All direction
    + a - Ditto
    + row - Only search in rows - Priority: 0 (hightest)
    + r - Ditto
    + colume - Only search in columes - Priority: 1
    + c - Ditto
    + rowcolume - Only search in rows and columes
    + rc | cr - Ditto
    + oblique - Only search in oblique direction
        + the \\ - Priority: 2
        + the / - Priority: 3 (lowest)
    + o - Ditto
+ echo
    + False - Return True if find one
    + True - Return (row, column) as the start point of first match

You should know a game called Gobang,  
this function can be used to determine the outcome.  
Of course, Othello is also ok.

#### Matrix trace
```python
def trace(self):
```
Return a number.

***

## Multiple Matrix Operation

#### Sum All
```python
def sm_sum(\*matrixs, force=False):
```
+ matrixs - can be two or more matrixs
+ force
    + True - Set '' or SPACE to 0
Error occurs with violated algorithm.  
Return a new matrix(list).

#### Subtraction
```python
def sm_minus(matrix_1, matrix_2, force=False):
```
+ matrixs_1 - first matrix
+ matrixs_2 - second matrix
+ force
    + True - Set '' or SPACE to 0
Error occurs with violated algorithm.  
Return a new matrix(list).

#### Multiplication with matrixs and numbers
```python
def sm_multis(\*matrixs_or_numbers, force=False):
```
+ matrixs - can be two or more matrixs and numbers
+ force
    + True - Set '' or SPACE to 0
Error occurs with violated algorithm.  
Return a new matrix(list, even only one number).

#### Multiply
```python
def sm_multi_mm(matrix_1, matrix_2):
```
+ matrixs_1 - first matrix
+ matrixs_2 - second matrix
Error occurs with violated algorithm. Use sm_number() if you need.  
Return a new matrix(list, even only one number).

#### Multiply with number
```python
def sm_multi_mn(matrix, number):
```
+ matrixs_1 - first matrix
+ matrixs_2 - anumber
Use sm_number() if you need.  
Return a new matrix(list).

***
{% highlight ruby lineno %}
'''
A lightweight module for handling Matrix.
Built For Real Number.
Plural actually available, but complete test haven't done...
All items should be numbers or letters in matrix.
Please use Numpy for more complex situation!
'''

# ########################## Instruction ################################
# put it in your floder and use like this:
# from sMartix import *
# then you can use it! simple :)

# ########################## Information ################################
# get new version: https://github.com/Kamilet/learning-coding/tree/master/simple-program/sMartix/sMartix.py
# bug report: http://coding.kamilet.cn/2018/01/06/sMartix
# email: hi@kmailet.cn

__author__ = 'Kamilet <hi@kamilet.cn>'
__version__ = '0.8a'  # lastchanged: 2018-01-06
__all__ = ['sm_gen', 'sm_cons', 'sm_copy', 'Smatrix', 'sm_numcheck',
           'sm_check', 'sm_negative', 'sm_abs', 'sm_number', 'sm_str',
           'sm_trans', 'sm_conj', 'sm_con_trans', 'sm_det', 'sm_inverse',
           'sm_alge', 'sm_sum', 'sm_minus', 'sm_multis',
           'sm_multi_mm', 'sm_multi_mn']

# ##########################################################
# 目标是写出一个包含各种函数的py文件，进行简单的实数矩阵运算。
# 命名为sMartix，是Simple matrix的意思，简单处理简单矩阵。
# 计划开始于  |  Kamilet 2018-01-05  |  coding.kamilet.cn

# ##########################################################
# 个人很讨厌矩阵，这也是为什么我打算写一个矩阵的拓展自己用。
# 仅处理二维矩阵的基本运算，并附带检查和生成矩阵的功能。
# 起码要包括高数常用的功能，并希望包括查询功能（五子棋）。
# 只对元素为单个数字的矩阵进行处理，复杂的为什么不用Numpy？
# 已经加入复数，测试中

# -------------------------------------------------------
# Handle with single matrix
# -------------------------------------------------------


def sm_gen(row: int = 1, colume: int = 1, items=0, unit=False, eye=False):
    '''Generate a matrix with row and colume,
    items can be numbers or string (can't calculate)
    set unit=True or eye=True to generate a unit matrix with row: sm_gen(row, eye=True)'''
    # 生成一个矩阵，可以设置行列以及默认填充的元素
    # 默认1行，1列，填充数字0
    # 设置unit为True会生成单位矩阵，根据row
    if unit or eye:
        matrix = sm_gen(row, row, items=0)
        for i in range(row):
            matrix[i][i] = 1
    else:
        matrix = [None] * row
        for _r in range(row):
            matrix[_r] = [items] * colume
    return matrix


def sm_cons(matrix, items=0, echo=0):
    '''Construct a matrix, for example:
    if matrix is [[1,2],[1]], would return [[1,2],[1,items]]
    the first row and colume must exist
    and any item like '' will be items'''
    # 建设一个矩阵，填充任何列数不足第一行列数的行
    # 空元素会被填充成items
    if echo:
        print('Your matrix will be full filled by:', items)
    _row = len(matrix)
    _colume = len(matrix[0])
    new_matrix = sm_gen(_row, _colume, items)
    for _r in range(0, _row):
        for _c in range(0, _colume):
            try:
                new_matrix[_r][_c] == matrix[_r][_c]
            except:
                pass
    return new_matrix


def sm_copy(matrix):
    '''perform a deep copy for matrix'''
    # 深度拷贝！
    # 建议所有涉及矩阵直接整块赋值的情况都使用copy！
    # 拓展这个模块时，请确保所有的new_matrix都通过gen或copy生成！
    _row = len(matrix)
    _colume = len(matrix[0])
    new_matrix = sm_gen(_row, _colume)
    for _r in range(_row):
        for _c in range(_colume):
            new_matrix[_r][_c] = matrix[_r][_c]
    return new_matrix


def sm_numcheck(matrix):
    '''Check is matrix is legal.
    And all items must be number.'''
    # 检查一个矩阵是否合法，并检查是否所有都是数字
    if not sm_check(matrix):
        return False
    _colume = len(matrix[0])
    for items in matrix:
        for _c in range(_colume):
            try:
                _temp = eval(str(items[_c]))
            except NameError:
                return False
            except TypeError:  # new for plural, wrong input will cause Eror
                pass
    return True


def sm_check(matrix):
    '''Check if the row and colume >=1
    Check if all row has same length'''
    # 检查矩阵是否合法，返回行列数，否则返回False
    # 此处不检查是否是数字
    try:
        _row = len(matrix)
        _colume = len(matrix[0])
        if _colume:
            for items in matrix:
                if len(items) != _colume:
                    return False
            return _row, _colume
        else:
            return False
    except IndexError:
        return False


def sm_negative(matrix):
    '''Set every numbers to -(number)'''
    # 给所有数加一个负号
    if sm_numcheck(matrix):
        new_matrix = sm_copy(matrix)
        new_matrix = sm_number(new_matrix)
        for _r in range(len(new_matrix)):
            for _c in range((len(new_matrix[0]))):
                new_matrix[_r][_c] *= -1
        return new_matrix
    else:
        assert False, 'Error: Your matrix is not all numbers'


def sm_abs(matrix):
    '''set every numbers to abs(number)'''
    # 将所有数据绝对值化
    if sm_numcheck(matrix):
        new_matrix = sm_copy(matrix)
        new_matrix = sm_number(new_matrix)
        for _r in range(len(new_matrix)):
            for _c in range((len(new_matrix[0]))):
                new_matrix[_r][_c] = abs(new_matrix[_r][_c])
        return new_matrix
    else:
        assert False, 'Error: Your matrix is not all numbers'


def sm_number(matrix, force=False):
    '''set every numbers to numbertype
    set force=True will replace letters and '' with 0'''
    # 将所有数据数值化
    # 将force设置为True将使得所有非字母转化为0
    new_matrix = sm_copy(matrix)
    for _r in range(len(new_matrix)):
        for _c in range((len(new_matrix[0]))):
            try:
                new_matrix[_r][_c] = eval(str(new_matrix[_r][_c]))
            except NameError:
                assert force, 'Error: Your matrix is not all numbers!\n\
You can try to use force=True for argument in function like:sm_number(matrix, force).'
                new_matrix[_r][_c] = 0
            except TypeError:  # new for plural, wrong input will cause Eror
                pass
    return new_matrix


def sm_str(matrix):
    '''set every items to string type'''
    # 将所有数据字符化
    new_matrix = sm_copy(matrix)
    for _r in range(len(new_matrix)):
        for _c in range((len(new_matrix[0]))):
            new_matrix[_r][_c] = str(new_matrix[_r][_c])
    return new_matrix


def sm_trans(matrix):
    '''Transpose'''
    # 单独的转置函数
    _row, _colume = sm_check(matrix)
    new_matrix = sm_gen(_colume,_row)
    for _r in range(_row):
        for _c in range(_colume):
            new_matrix[_c][_r] = matrix[_r][_c]
    return new_matrix


def sm_conj(matrix):
    '''Conjugation'''
    # 复数矩阵的共轭
    _row, _colume = sm_check(matrix)
    new_matrix = sm_gen(_row, _colume)
    for _r in range(_row):
        for _c in range(_colume):
            if matrix[_r][_c].imag != 0:
                new_matrix[_r][_c] = matrix[_r][_c].real - matrix[_r][_c].imag * 1j
            else:
                new_matrix[_r][_c] = matrix[_r][_c].real
    return new_matrix


def sm_con_trans(matrix):
    '''Conjugation transpose'''
    # 复数的共轭转置
    _row, _colume = sm_check(matrix)
    new_matrix = sm_gen(_colume,_row)
    for _r in range(_row):
        for _c in range(_colume):
            if matrix[_r][_c].imag != 0:
                new_matrix[_c][_r] = matrix[_r][_c].real - matrix[_r][_c].imag * 1j
            else:
                new_matrix[_c][_r] = matrix[_r][_c].real
    return new_matrix


def sm_det(matrix, force=False):
    '''Determinant, return a number
    set force=True to calculate even row != column'''
    # 行列式运算，返回数值
    _row, _colume = sm_check(matrix)
    new_matrix = sm_number(sm_copy(matrix))
    _det = 0
    if not (force or _row == _colume) or not sm_numcheck(matrix):
        assert False, 'Error: Your matrix is illegal for Det(A)'
    if _row == 2:
        _det = matrix[1][1] * matrix[0][0] - matrix[0][1] * matrix[1][0]
        return _det
    for _r in range(_colume):
        _temp1 = 1
        _temp2 = 1
        for _c in range(_row):
            _temp1 *= new_matrix[_c][(_r+_c)%_colume]
            _temp2 *= new_matrix[_c][(_r-_c)%_colume]
        _det = _det + _temp1 - _temp2
    return _det


def sm_inverse(matrix):
    '''Inverse matrix'''
    # 求逆矩阵
    _row, _colume = sm_check(matrix)
    if _row != _colume or not sm_numcheck(matrix):
        assert False, 'Error: Your matrix is illegal for Inverse(A)'
    _det = sm_det(matrix)
    if _det == 0:
        assert False, 'Error: Your matrix is illegal for Inverse(A)'
    new_matrix = sm_gen(_row, _colume)
    for _r in range(_row):
        for _c in range(_colume):
            new_matrix[_c][_r] = sm_alge(matrix, _r, _c) / _det
    return new_matrix


def sm_alge(matrix, row:int , colume:int):
    '''algebraic cofactor'''
    # 代数余子式
    _row, _colume = sm_check(matrix)
    new_matrix = sm_gen(_row-1, _colume-1)
    _rownum = list(range(_row))
    _columenum = list(range(_colume))
    del _rownum[row]
    del _columenum[colume]
    for _r in range(_row-1):
        for _c in range(_colume-1):
            new_matrix[_r][_c] = matrix[_rownum[_r]][_columenum[_c]]
    return sm_det(new_matrix) * (-1) ** (row+colume)


class Smatrix:
    '''handdel a single matrix'''
    # 用于对单一矩阵进行处理

    def __init__(self, matrix, allnumber=False):
        '''an error check will run automaticlly'''
        self.matrix = matrix
        _check = sm_check(matrix)
        if _check:
            self.colume = _check[1]  # len(matrix)
            self.row = _check[0]  # len(matrix[0])
        else:
            assert False, 'Error: Your matrix is illegal'
        if allnumber and not sm_numcheck(matrix):
            assert False, 'Error: Your matrix is illegal'

    def clean(self, items=0, echo=False):
        '''clear a matrix with 0 as defult'''
        # 默认情况下，用0填充整个矩阵
        if echo:
            print('Your items in matrix has been replaced with:', items)
        return sm_gen(self.row, self.colume, items)

    def check(self):
        '''Check if the row and colume >=1
        Check if all row has same length'''
        # 检查矩阵是否合法，返回行列数，否则返回False
        # 此处不检查是否是数字
        return sm_check(self.matrix)

    def numcheck(self):
        '''Check is matrix is legal.
        And all items must be number.'''
        # 检查一个矩阵是否合法，并检查是否所有都是数字
        return sm_numcheck(self.matrix)

    def view(self):
        '''view the matrix'''
        # 将矩阵按照行列打印出来
        for item in self.matrix:
            print(item)

    def negative(self):
        '''Set every numbers to -(number)'''
        # 给所有数加一个负号
        return sm_negative(self.matrix)

    def rotate(self, method='exchange', step: int=1, force=False):
        '''rotate a matrix, set strp to act serveral tiems, set method to:
        - transpose:(or exchange | or ex | or tr) exchange rows and columes
        - clockwise:(or clock) rotate it in clockwise
        - mirrorrow:(or mr | or mh | or mirror) mirror in horizontal direction
        - mirrorcolume:(or mc | or mv) mirror in vertical
        set force=True will assert Error when no opreation happened'''
        # 矩阵的旋转翻转操作：
        # ex - 横纵交换，clock - 顺时针旋转， mh-水平翻转， mv - 垂直翻转
        new_matrix = sm_copy(self.matrix)
        if method in ['transpose', 'exchange', 'ex', 'tr']:
            step %= 2
            while step:
                step -= 1
                new_matrix = sm_gen(self.colume, self.row, '')
                # _row and _colume here for new_matrix
                for _row in range(self.colume):
                    for _colume in range(self.row):
                        new_matrix[_row][_colume] = self.matrix[_colume][_row]
        elif method == 'clockwise' or method == 'clock':
            step %= 4
            while step:
                step -= 1
                o_colume = len(new_matrix[0])
                o_row = len(new_matrix)
                o_matrix = new_matrix
                new_matrix = sm_gen(o_colume, o_row, '')
                for _row in range(o_colume):
                    for _colume in range(o_row):
                        new_matrix[_row][_colume] = o_matrix[
                            o_row - _colume - 1][_row]
        elif method in ['mirrorrow', 'mr', 'mh', 'mirror']:
            step %= 2
            while step:
                step -= 1
                for _row in range(self.row):
                    new_matrix[_row] = new_matrix[_row][::-1]
        elif method in ['mirrorcolume', 'mc', 'mv']:
            step %= 2
            while step:
                step -= 1
                for line in range(0, self.row // 2):
                    new_matrix[line], new_matrix[self.row - line - 1] =\
                        new_matrix[self.row - line - 1], new_matrix[line]
        elif force:
            assert False, 'Error: rotate(method={}, step={})'.format(
                method, step)
        return new_matrix

    def trans(self):
        '''transpose, same as rotate(matrix, transpose)'''
        # 单独的转置
        return sm_trans(self.matrix)

    def conj(self):
        '''Conjugation'''
        # 共轭
        return sm_conj(self.matrix)

    def con_trans(self):
        '''Conjugation transpose, transpose for plural'''
        # 共轭转置
        return sm_con_trans(self.matrix)

    def det(self):
        '''Determinant'''
        # 行列式运算
        return sm_det(self.matrix)

    def inverse(self):
        '''Inverse matrix'''
        # 求逆矩阵
        return sm_inverse(self.matrix)

    def find(self, string:str='', length=2, direct='all', echo=False):
        '''scan the matrix and find a cut with given length.
        set string to:
        - any string: scan for it
        - '': scan for a cut in that length
        set direct to:
        - all:(as defult, or a) scan in every direction
        - row:(or r) only scan in row
        - colume:(or c) only scan in colume
        - rowcolume:(or cr, or rc) scan in row and colume
        - oblique:(or o) scan in oblique
        set echo to:
        - False:(as defult) will return True is exist
        - True: will return the first match as [row1,colume1]
                means the match start at [row1,colume1]
        about priority:
        from hight to low : row - colume - oblique(\) - oblique(/)
        from [0,0] to [m-1,n-1]
        '''
        # 扫描系统，寻找长度匹配的切片，即“五子棋”系统
        # direct可以设置扫描方向：
        # all - 全局扫描；r - 只扫行内；c - 只扫列内；rc - 只扫行列；o - 只扫斜向
        # echo可以设置返回值：
        # False - 返回是否存在这样的切片；True - 返回匹配到第一个切片的起点
        # 检查优先级：行、列、左上到右下、右上到左下
        # 返还优先级：左到右，上到下
        # --
        # 不加这么多参数可以大大提高循环的效率的…
        # 比如行、列、斜和反斜可以共用第一个循环，行和列可以共用第二个循环
        string = str(string)
        _row = len(self.matrix)
        _colume = len(self.matrix[0])
        new_matrix = sm_str(self.matrix)
        if (_row < length and direct in ['all','a','row','r','oblique','o','rc','cr'])\
           or (_colume < length and direct in ['all','a','colume','c','oblique','o','rc','cr']):
            assert False, 'Length of cut cannot longer than length of scan area!'
        if direct in ['all','a','row','r','rc','cr']:
            # scan in row
            # 纯行扫描
            for _r in range(_row):
                for _scan in range(_colume - length + 1):
                    if string != '' and string != new_matrix[_r][_scan]:
                        continue
                    for _i in range(1, length):
                        flag = True
                        if new_matrix[_r][_scan:_scan+length][_i] != new_matrix[_r][_scan]:
                            flag = False
                            break
                    if flag:
                        if echo:
                            return _r,_scan
                        else:
                            return True
        if direct in ['all','a','colume','c','rc','cr']:
            # scan in colume
            # 纯列扫描
            for _r in range(_row - length + 1):
                for _scan in range(_colume):
                    if string != '' and string != new_matrix[_r][_scan]:
                        continue
                    for _i in range(1, length):
                        flag = True
                        if new_matrix[_r + _i][_scan] != new_matrix[_r - 1][_scan]:
                            flag = False
                            break
                    if flag:
                        if echo:
                            return _r,_scan
                        else:
                            return True
        if direct in ['all', 'a', 'oblique', 'o']:
            # scan in oblique
            # 斜向扫描
            # direction \ first
            for _r in range(_row - length +1):
                for _c in range(_colume - length + 1):
                    if string != '' and string != new_matrix[_r][_c]:
                        continue
                    for _i in range(1, length):
                        flag = True
                        if new_matrix[_r + _i][_c + _i] != new_matrix[_r][_c]:
                            flag = False
                            break
                    if flag:
                        if echo:
                            return _r,_c
                        else:
                            return True
            # direction / second
            # sure can put \ and / in same cycle, but too hard to read
            # especially when we need check flag and echo
            for _r in range(_row - length +1):
                for _c in range(length - 1, _colume):
                    if string != '' and string != new_matrix[_r][_c]:
                        continue
                    for _i in range(1, length):
                        flag = True
                        if new_matrix[_r + _i][_c - _i] != new_matrix[_r][_c]:
                            flag = False
                            break
                    if flag:
                        if echo:
                            return _r,_c
                        else:
                            return True
        return False

    def trace(self):
        '''return the trace, only for square matrix'''
        # 返回矩阵的迹，只对方阵有效
        _trace = 0
        sm_numcheck(self.matrix)
        for _cr in range(len(self.matrix)):
            trace += self.matrix[_cr][_cr]
        return trace

# -------------------------------------------------------
# Handle with multiple matrixs
# -------------------------------------------------------


def sm_sum(*matrixs, force=False):
    ''' sum all given matrixs
    set force=True to ignore '' and letters
    use sm_negative() to minus anyone'''
    # 矩阵求和，设置force为True可以强制字母和空字符被作为0求和
    _row = len(matrixs[0])
    _colume = len(matrixs[0][0])
    new_matrix = sm_number(matrixs[0], force)
    for _item in matrixs[1:]:
        if len(_item) != _row or len(_item[0]) != _colume:
            assert False, 'Cannot sum matrixs with different numbers of rows or columes!'
        _item = sm_number(_item, force)
        for _r in range(_row):
            for _c in range(_colume):
                new_matrix[_r][_c] += _item[_r][_c]
    return new_matrix


def sm_minus(matrix_1, matrix_2, force=False):
    '''minus two matrixs, matrix_1 - matrix_2'''
    # 两个矩阵相减，前减后
    return sm_copy(sm_sum(matrix_1, sm_negative(matrix_2), force=force))


def sm_multis(*matrixs_or_numbers, force=False):
    '''multiplication for matrixs and numbers'''
    # 矩阵的乘法或数乘
    matrixs = []
    numbers = 1
    for _item in matrixs_or_numbers:
        if type(_item) is list or type(_item) is tuple:
            if force:
                matrixs.append(sm_number(_item))
            elif sm_numcheck(_item):
                matrixs.append(_item)
            else:
                assert False, 'Your matrix is illegal for multiplication!'
        elif type(_item) is int or type(_item) is float or type(_item) is complex:
            # changed for plural
            numbers *= _item
        else: assert False, 'Type of arguments must be list or int or float or complex!'
    new_matrix = sm_copy(matrixs[0])
    for _i in range(1, len(matrixs)):
        new_matrix = sm_multi_mm(new_matrix, matrixs[_i])
    return sm_multi_mn(new_matrix, numbers)


def sm_multi_mm(matrix_1, matrix_2):
    '''multiplication for only 2 matrixs'''
    # 两个矩阵相乘
    _length = len(matrix_1[0])
    if _length != len(matrix_2):
        assert False, 'Your matrix is illegal for multiplication!'
    new_matrix = sm_gen(len(matrix_1), len(matrix_2[0]))
    for new_row in range(len(matrix_1)):
        for new_column in range(len(matrix_2[0])):
            for _n in range(_length):
                new_matrix[new_row][new_column] +=\
                matrix_1[new_row][_n] * matrix_2[_n][new_column]
    return new_matrix


def sm_multi_mn(matrix, number):
    '''multiplication for one matrix and one number'''
    # 矩阵和数字相乘
    new_matrix = sm_copy(matrix)
    for _item in new_matrix:
        for _i in range(len(_item)):
            _item[_i] *= number
    return new_matrix
{% endhighlight %}