# Searching Algorithms Guide

Searching algorithms are fundamental techniques in computer science used to find specific elements within data structures. This guide will cover various searching algorithms, their properties, implementations, and applications.

## Table of Contents

1. [Introduction](#introduction)
2. [Types of Searching Algorithms](#types-of-searching-algorithms)
   - [Linear Search](#linear-search)
   - [Binary Search](#binary-search)
   - [Jump Search](#jump-search)
   - [Interpolation Search](#interpolation-search)
   - [Exponential Search](#exponential-search)
   - [Fibonacci Search](#fibonacci-search)
3. [Comparing Searching Algorithms](#comparing-searching-algorithms)
4. [Applications of Searching Algorithms](#applications-of-searching-algorithms)
5. [Performance Analysis](#performance-analysis)
6. [Getting Started](#getting-started)
7. [Additional Resources](#additional-resources)

## Introduction

Searching algorithms are designed to retrieve information stored within a data structure. The efficiency of these algorithms can significantly impact the performance of software applications, especially when dealing with large datasets. This guide will introduce you to various searching algorithms, their implementations, and use cases.

## Types of Searching Algorithms

### Linear Search

Linear search is the simplest search algorithm. It checks each element in the list sequentially until the desired element is found or the list ends.

**Properties**:
- **Time Complexity**: O(n)
- **Space Complexity**: O(1)

**Implementation**:
```python
def linear_search(arr, target):
    for i in range(len(arr)):
        if arr[i] == target:
            return i
    return -1
```

### Binary Search
Binary search is an efficient algorithm for finding an item from a sorted list of items. It works by repeatedly dividing the search interval in half.

**Properties:**

- Time Complexity: O(log n)
- Space Complexity: O(1)
**Implementation:**

``` python
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
### Jump Search
Jump search is a searching algorithm for ordered lists. It works by jumping ahead by fixed steps and then performing a linear search within the block.

**Properties:**

- Time Complexity: O(√n)
- Space Complexity: O(1)
**Implementation:**

``` python
import math

def jump_search(arr, target):
    n = len(arr)
    step = int(math.sqrt(n))
    prev = 0

    while arr[min(step, n)-1] < target:
        prev = step
        step += int(math.sqrt(n))
        if prev >= n:
            return -1

    for i in range(prev, min(step, n)):
        if arr[i] == target:
            return i
    return -1
```
### Interpolation Search
Interpolation search is an improved variant of binary search for uniformly distributed data. It tries to estimate the position of the target value within the search space.

**Properties:**

- Time Complexity: O(log log n) [best case], O(n) [worst case]
- Space Complexity: O(1)
**Implementation:**

``` python
def interpolation_search(arr, target):
    low, high = 0, len(arr) - 1

    while low <= high and arr[low] <= target <= arr[high]:
        if low == high:
            if arr[low] == target:
                return low
            return -1

        pos = low + ((target - arr[low]) * (high - low) // (arr[high] - arr[low]))

        if arr[pos] == target:
            return pos
        elif arr[pos] < target:
            low = pos + 1
        else:
            high = pos - 1
    return -1
```
### Exponential Search
Exponential search is particularly useful for unbounded or infinite lists. It works by increasing the range exponentially and then performing a binary search within the found range.

**Properties:**

- Time Complexity: O(log n)
- Space Complexity: O(1)
**Implementation:**

``` python
def exponential_search(arr, target):
    if arr[0] == target:
        return 0

    n = len(arr)
    i = 1
    while i < n and arr[i] <= target:
        i *= 2

    return binary_search(arr[:min(i, n)], target)

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
### Fibonacci Search
Fibonacci search is a comparison-based technique that uses Fibonacci numbers to search an element in a sorted array.

**Properties:**

- Time Complexity: O(log n)
- Space Complexity: O(1)
**Implementation:**

``` python
def fibonacci_search(arr, target):
    n = len(arr)
    fibMMm2 = 0
    fibMMm1 = 1
    fibM = fibMMm2 + fibMMm1

    while (fibM < n):
        fibMMm2 = fibMMm1
        fibMMm1 = fibM
        fibM = fibMMm2 + fibMMm1

    offset = -1

    while (fibM > 1):
        i = min(offset + fibMMm2, n-1)

        if (arr[i] < target):
            fibM = fibMMm1
            fibMMm1 = fibMMm2
            fibMMm2 = fibM - fibMMm1
            offset = i
        elif (arr[i] > target):
            fibM = fibMMm2
            fibMMm1 = fibMMm1 - fibMMm2
            fibMMm2 = fibM - fibMMm1
        else:
            return i

    if(fibMMm1 and arr[offset+1] == target):
        return offset+1

    return -1
```
