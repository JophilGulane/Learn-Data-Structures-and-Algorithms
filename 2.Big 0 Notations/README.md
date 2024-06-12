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

