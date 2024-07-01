---
layout: post
title: Merge Sort
date: 2024-06-25 00:01:00
description: An application of divide-and-conquer algorithm
tags: sort-algorithms divide-and-conquer
categories: algorithms
pseudocode: true
---

Merge sort is a highly efficient, comparision-based sorting algorithm that follows the divide-and-conquer paradigm. It's one of the most commonly used sorting algorithms due to its stable performance and predicatable time complexity.

The core idea behind merge sort is to divide the unsorted list into smaller sublists, each containing zero or element (which are inherently sorted). These sublists are then recursively merged back together in a manner that ensures thte merged list is sorted. This process continues until the entire list is sorted. 

Merge sort achieves this in three main steps:

- **Divide**: The unsorted list is divided recursively into two halves until sublists of only one element remain.

- **Conquer**: Sublists are recursively merged to produce new sorted sublists until there is only one sublist remaining. This step ensures that the elements are sorted during each merge operation.

- **Combine**: The final step merges the two sorted sublists generated in the conquer step into a single sorted list.

```pseudocode
% This mergesort algorithm is extracted from Chapter 2, Introduction to Algorithms (3rd edition)
\begin{algorithm}
\caption{Mergesort}
\begin{algorithmic}
\PROCEDURE{Mergesort}{$$A, p, r$$}
    \IF{$$p < r$$}
        \STATE $$q = \lfloor(p + r)\rfloor /2$$
        \STATE \CALL{Mergesort}{$$A, p, q$$}
        \STATE \CALL{Mergesort}{$$A, q + 1, r$$}
        \STATE \CALL{Merge}{$$A, p, q, r$$}
    \ENDIF
\ENDPROCEDURE
\PROCEDURE{Merge}{$$A, p, q, r$$}
    \STATE $$n1 = q - p + 1$$
    \STATE $$n2 = r - q$$
    \STATE Let $$L[1..n1 + 1]$$ and $$R[1.. n2+1]$$ be new arrays
    \FOR{$$i = 1 \TO n1$$}
        \STATE $$L[i] = A[p + i - 1]$$
    \ENDFOR
    \FOR{$$j = 1 to n2$$}
        \STATE $$R[j] = A[q + j]$$
    \ENDFOR
    \STATE $$L[n1 + 1] = \INFTY$$
    \STATE $$R[n2 + 1] = \INFTY$$
    \STATE $$i = 1$$
    \STATE $$j = 1$$
    \FOR{$$k = p \TO r$$}
        \IF{$$L[i] <= R[j]$$}
            \STATE $$A[k] = L[i]$$
            \STATE $$i = i + 1$$
        \ELSE{$$A[k] = R[j]$$}
            \STATE $$j = j + 1$$
        \ENDIF
    \ENDFOR
\ENDPROCEDURE
\end{algorithmic}
\end{algorithm}
```

Key characteristics of merge sort include:

- Stable Sorting: Merge sort preserves the order of equal elements, making it stable.
- Predictable Performance: It has a consistent O(n log n) time complexity for all cases (worst-case, average-case, and best-case), where n is the number of elements in the list.
- Space Efficiency: While merge sort requires additional space proportional to the size of the input for temporary arrays during the merging process, its space complexity is O(n), making it suitable for large datasets.