LeetCode Solutions – Java
📌 Overview

This repository contains 7 LeetCode problem solutions implemented in Java. The problems cover important Data Structures and Algorithm concepts including Arrays, Hashing, Matrix Traversal, Dynamic Programming, Backtracking, Recursion, and Trie-based searching.

| No. | LeetCode | Problem                                  | Difficulty | Main Topic                |
| --- | -------: | ---------------------------------------- | ---------- | ------------------------- |
| 01  |      414 | Third Maximum Number                     | Easy       | Arrays                    |
| 02  |      448 | Find All Numbers Disappeared in an Array | Easy       | Arrays / Hashing          |
| 03  |       74 | Search a 2D Matrix                       | Medium     | Binary Search / Matrix    |
| 04  |       64 | Minimum Path Sum                         | Medium     | Dynamic Programming       |
| 05  |       79 | Word Search                              | Medium     | Backtracking / DFS        |
| 06  |      140 | Word Break II                            | Hard       | DP / Backtracking         |
| 07  |      212 | Word Search II                           | Hard       | Trie / DFS / Backtracking |

1️⃣ LeetCode 414 – Third Maximum Number
📄 File
Solution-01-414.java
🔗 Problem

Third Maximum Number

🧩 Difficulty

Easy

📚 Concepts Used
Arrays
Iteration
Duplicate handling
Tracking maximum values
📝 Problem Description

Given an integer array, return the third distinct maximum number in the array.

If the third maximum does not exist, return the maximum number.

Example
Input:
[3, 2, 1]

Output:
1

Another example:

Input:
[1, 2]

Output:
2

Because there are only two distinct numbers.

💡 Approach

Maintain the largest three distinct values:

First Maximum
Second Maximum
Third Maximum

While traversing the array:

Ignore duplicate values.
If the current number is greater than the first maximum, shift the values.
Otherwise, update the second maximum if required.
Update the third maximum accordingly.
If a third distinct maximum exists, return it.
Otherwise, return the first maximum.
⏱️ Complexity
Time Complexity: O(n)
Space Complexity: O(1)
2️⃣ LeetCode 448 – Find All Numbers Disappeared in an Array
📄 File
Solution-02-448.java
🔗 Problem

Find All Numbers Disappeared in an Array

🧩 Difficulty

Easy

📚 Concepts Used
Arrays
Index marking
In-place modification
Array traversal
📝 Problem Description

Given an array containing numbers from:

1 to n

some numbers appear once or twice, while some numbers are missing.

Return all numbers that do not appear in the array.

Example
Input:
[4,3,2,7,8,2,3,1]

Output:
[5,6]
💡 Approach

The value x can be mapped to index:

x - 1

For every value in the array:

Find its corresponding index.
Mark that index as visited.
After processing all elements, indexes that remain unmarked represent missing numbers.

This approach avoids using an additional HashSet.

⏱️ Complexity
Time Complexity: O(n)
Space Complexity: O(1)

The returned list is not counted as extra auxiliary space.

3️⃣ LeetCode 74 – Search a 2D Matrix
📄 File
Solution-03-74.java
🔗 Problem

Search a 2D Matrix

🧩 Difficulty

Medium

📚 Concepts Used
Matrix
Binary Search
Divide and Conquer
Index conversion
📝 Problem Description

Given a matrix where:

Each row is sorted in ascending order.
The first element of each row is greater than the last element of the previous row.

Determine whether a target value exists in the matrix.

Example
Input:

1  3  5  7
10 11 16 20
23 30 34 60

Target = 3

Output:
true
💡 Approach

The complete matrix can be treated as a sorted one-dimensional array.

For a matrix with:

rows × columns

we use binary search.

For a one-dimensional index:

mid

convert it into matrix coordinates:

row = mid / columns
column = mid % columns

Then compare the matrix value with the target.

⏱️ Complexity
Time Complexity: O(log(m × n))
Space Complexity: O(1)
4️⃣ LeetCode 64 – Minimum Path Sum
📄 File
Solution-04-64.java
🔗 Problem

Minimum Path Sum

🧩 Difficulty

Medium

📚 Concepts Used
Dynamic Programming
2D Arrays
Matrix traversal
Optimization
📝 Problem Description

Given a grid containing non-negative integers, find a path from the top-left corner to the bottom-right corner.

You can move only:

Right
Down

The objective is to find the minimum possible sum of the path.

Example
Input:

1  3  1
1  5  1
4  2  1

Output:
7

Path:

1 → 3 → 1 → 1 → 1

Sum:

7
💡 Approach

Use Dynamic Programming.

For every cell:

dp[i][j]

represents the minimum path sum required to reach that cell.

For an internal cell:

dp[i][j] =
grid[i][j] + min(dp[i-1][j], dp[i][j-1])

Each cell can be reached from either:

The cell above
The cell to the left
⏱️ Complexity
Time Complexity: O(m × n)
Space Complexity: O(m × n)

The space can also be optimized to O(n).

5️⃣ LeetCode 79 – Word Search
📄 File
Solution-05-79.java
🔗 Problem

Word Search

🧩 Difficulty

Medium

📚 Concepts Used
Backtracking
Depth-First Search
Recursion
Matrix traversal
Visited cells
📝 Problem Description

Given a 2D character board and a word, determine whether the word exists in the grid.

The word can be constructed from letters of sequentially adjacent cells.

Allowed directions:

Up
Down
Left
Right

A cell cannot be used more than once in the same path.

Example
Board:

A B C E
S F C S
A D E E

Word:
ABCCED

Output:
true
💡 Approach

Use DFS with Backtracking.

For every cell:

Check whether it matches the current character.
Mark the cell as visited.
Explore four directions.
If the complete word is found, return true.
Otherwise, restore the cell and backtrack.

The backtracking step allows the same board to be explored through different possible paths.

⏱️ Complexity

Approximately:

Time Complexity: O(m × n × 4^L)
Space Complexity: O(L)

Where:

m = number of rows
n = number of columns
L = length of the word
6️⃣ LeetCode 140 – Word Break II
📄 File
Solution-06-140.java
🔗 Problem

Word Break II

🧩 Difficulty

Hard

📚 Concepts Used
Dynamic Programming
Backtracking
Recursion
Memoization
String manipulation
📝 Problem Description

Given a string s and a dictionary of words, return all possible sentences that can be formed by inserting spaces between valid dictionary words.

Example
Input:

s = "catsanddog"

wordDict = ["cat","cats","and","sand","dog"]

Output:

[
 "cats and dog",
 "cat sand dog"
]
💡 Approach

Use DFS + Memoization.

Start from an index in the string and try every possible substring.

For each substring:

Check whether it exists in the dictionary.
Recursively solve the remaining suffix.
Combine the current word with the generated sentences.
Store the result for the current index.

Memoization avoids solving the same suffix repeatedly.

Example Concept

For:

catsanddog

Possible divisions include:

cat | sand | dog
cats | and | dog

These are then converted into complete sentences.

⏱️ Complexity

The problem can have a large number of valid sentences, so complexity depends on the number and length of possible combinations.

A useful characterization is:

Time Complexity: Exponential in the worst case
Space Complexity: O(n) recursion depth + stored results

Memoization significantly reduces repeated computation.

7️⃣ LeetCode 212 – Word Search II
📄 File
Solution-07-212.java
🔗 Problem

Word Search II

🧩 Difficulty

Hard

📚 Concepts Used
Trie
DFS
Backtracking
Recursion
Matrix traversal
Prefix searching
📝 Problem Description

Given a 2D character board and a list of words, find all words that can be constructed from the board.

Words must be formed using adjacent cells:

Up
Down
Left
Right

A cell cannot be used more than once while constructing a single word.

Example
Board:

o a a n
e t a e
i h k r
i f l v

Words:

["oath","pea","eat","rain"]

Output:

["eat","oath"]
💡 Approach

A simple DFS for every word can be inefficient.

Instead, construct a Trie containing all dictionary words.

The Trie allows us to:

Start from every board cell.
Follow only prefixes that exist in the dictionary.
Stop searching immediately when a prefix is invalid.
Add a word when a complete Trie word is reached.
Continue DFS to discover additional words.
Why Trie?

Suppose the dictionary contains:

cat
car
card
care

After reading:

ca

the Trie can determine that multiple valid words continue from the same prefix.

This avoids repeatedly searching the board independently for every word.

⏱️ Complexity

The exact complexity depends on:

Board size
Number of words
Word lengths
Trie structure

The Trie significantly reduces unnecessary DFS exploration by pruning invalid prefixes.

🧠 Concepts Covered

This collection provides practice in several important DSA topics.

Arrays

Problems:

414
448

Skills:

Array traversal
Duplicate handling
Index manipulation
In-place processing
Binary Search

Problem:

74

Skills:

Searching sorted data
Matrix indexing
Divide-and-conquer logic
Dynamic Programming

Problems:

64
140

Skills:

State definition
Recurrence relations
Memoization
Reusing previously calculated results
Backtracking

Problems:

79
140
212

Skills:

Recursion
Exploring multiple possibilities
Choosing and undoing choices
State restoration
DFS

Problems:

79
212

Skills:

Grid traversal
Recursive searching
Four-direction movement
Visited-cell management
Trie

Problem:

212

Skills:

Prefix searching
Efficient dictionary lookup
Combining Trie with DFS
Search pruning
📊 Difficulty Distribution
Easy:
414
448

Medium:
74
64
79

Hard:
140
212

Total:

7 Problems
2 Easy
3 Medium
2 Hard
🗂️ File Structure
LeetCode-Solutions/
│
├── Solution-01-414.java
├── Solution-02-448.java
├── Solution-03-74.java
├── Solution-04-64.java
├── Solution-05-79.java
├── Solution-06-140.java
├── Solution-07-212.java
│
└── README.md
🧪 Testing Strategy

Each solution should be tested using:

1. Normal Case

Test the expected/common input.

2. Boundary Case

Test:

Empty or minimum-size input where permitted
Single element
Small matrix
Minimum word length
Minimum dictionary size
3. Duplicate Case

Important for:

414
448
4. No-Solution Case

Important for:

79
140
212
5. Large Input

Used to check whether the algorithm performs efficiently.

🎯 Learning Objectives

By completing these seven problems, the following skills are practiced:

Understanding array manipulation
Handling duplicate values
Applying binary search
Solving grid-based problems
Designing dynamic programming states
Implementing recursion
Understanding backtracking
Using memoization
Building and using a Trie
Combining Trie with DFS
Improving search efficiency through pruning
Analyzing time and space complexity
