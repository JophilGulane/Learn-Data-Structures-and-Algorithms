# Big O Notation Guide

Big O Notation is a mathematical notation used to describe the performance or complexity of an algorithm. It gives an upper bound on the time or space complexity of an algorithm, allowing for the comparison of the efficiency of different algorithms.

## Table of Contents

1. [Introduction](#introduction)
2. [Why Big O Notation?](#why-big-o-notation)
3. [Big O Notation Basics](#big-o-notation-basics)
   - [Constant Time - O(1)](#constant-time---o1)
   - [Logarithmic Time - O(log n)](#logarithmic-time---olog-n)
   - [Linear Time - O(n)](#linear-time---on)
   - [Linearithmic Time - O(n log n)](#linearithmic-time---on-log-n)
   - [Quadratic Time - O(n^2)](#quadratic-time---on2)
   - [Cubic Time - O(n^3)](#cubic-time---on3)
   - [Exponential Time - O(2^n)](#exponential-time---o2n)
   - [Factorial Time - O(n!)](#factorial-time---on)
4. [Common Misconceptions](#common-misconceptions)
5. [Analyzing Algorithms](#analyzing-algorithms)
   - [Worst-case Analysis](#worst-case-analysis)
   - [Best-case Analysis](#best-case-analysis)
   - [Average-case Analysis](#average-case-analysis)
6. [Space Complexity](#space-complexity)
7. [Examples](#examples)
8. [Additional Resources](#additional-resources)

## Introduction

Big O Notation provides a high-level understanding of an algorithm's efficiency by describing how its runtime or space requirements grow as the input size grows. This guide will cover the basics of Big O Notation, different types of complexities, and how to analyze them.

## Why Big O Notation?

- **Predict Performance**: Helps predict how an algorithm will perform as the input size increases.
- **Compare Algorithms**: Allows comparison of different algorithms based on their efficiency.
- **Optimize Code**: Guides developers in optimizing code for better performance.

## Big O Notation Basics

### Constant Time - O(1)

An algorithm runs in constant time if
its execution time does not change regardless of the input size.

```python
def get_first_element(array):
    return array[0]
```
### Logarithmic Time - O(log n)

An algorithm runs in logarithmic time if its execution time increases logarithmically as the input size increases.

```python
def binary_search(arr, target):
    low, high = 0, len(arr) - 1
    while low <= high:
        mid = (low + high) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            low = mid + 1
        else:
            high = mid - 1
    return -1
```
### Linear Time - O(n)
An algorithm runs in linear time if its execution time increases linearly with the input size.

```python
def linear_search(arr, target):
    for i in range(len(arr)):
        if arr[i] == target:
            return i
    return -1
```
### Linearithmic Time - O(n log n)
An algorithm runs in linearithmic time if its execution time increases in proportion to 𝑛 log 𝑛.

```python
def merge_sort(arr):
    if len(arr) > 1:
        mid = len(arr) // 2
        L = arr[:mid]
        R = arr[mid:]

        merge_sort(L)
        merge_sort(R)

        i = j = k = 0
        while i < len(L) and j < len(R):
            if L[i] < R[j]:
                arr[k] = L[i]
                i += 1
            else:
                arr[k] = R[j]
                j += 1
            k += 1

        while i < len(L):
            arr[k] = L[i]
            i += 1
            k += 1

        while j < len(R):
            arr[k] = R[j]
            j += 1
            k += 1
```

### Quadratic Time - O(n^2)
An algorithm runs in quadratic time if its execution time is proportional to the square of the input size.

```python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(0, n-i-1):
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]
```

### Cubic Time - O(n^3)
An algorithm runs in cubic time if its execution time is proportional to the cube of the input size.

``` python
def three_sum(arr):
    n = len(arr)
    for i in range(n):
        for j in range(i+1, n):
            for k in range(j+1, n):
                if arr[i] + arr[j] + arr[k] == 0:
                    print(arr[i], arr[j], arr[k])
```

### Exponential Time - O(2^n)
An algorithm runs in exponential time if its execution time doubles with each additional input element.

```python
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)
```

### Factorial Time - O(n!)
An algorithm runs in factorial time if its execution time is proportional to the factorial of the input size.

```python
def permutations(string):
    if len(string) == 1:
        return [string]
    perms = []
    for i, char in enumerate(string):
        for perm in permutations(string[:i] + string[i+1:]):
            perms.append(char + perm)
    return perms
```
### Common Misconceptions
- Big O is not about exact timings: It describes the growth rate, not the actual time.
- Big O is about the upper bound: It provides the worst-case scenario.
- Big O ignores constants and lower-order terms: Focuses on the most significant term as input size grows.
### Algorithms
Worst-case Analysis
Describes the maximum amount of time an algorithm can take.

Best-case Analysis
Describes the minimum amount of time an algorithm can take.

Average-case Analysis
Describes the expected amount of time an algorithm can take, averaged over all possible inputs.

Space Complexity
Space complexity describes the amount of memory an algorithm uses relative to the input size.

O(1): Constant space.
O(n): Linear space.
O(n^2): Quadratic space.
Examples
