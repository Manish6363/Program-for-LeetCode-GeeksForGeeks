\## Problem: 

You are given an array nums consisting of positive integers. Return the total frequencies of elements in nums such that those elements all have the maximum frequency. 

The frequency of an element is the number of occurrences of that element in the array.



link: https://leetcode.com/problems/count-elements-with-maximum-frequency/





\# Intuition

Count how many times each number appears → find the highest frequency → add all frequencies equal to that highest frequency.

The problem does NOT ask for the element(s) — it asks for the total count of elements that appear maximum times.



\*\*So logically:\*\*

1\. Every element appears some number of times.

2\. Among these counts, one count will be the maximum frequency.

3\. There might be multiple elements having this same maximum frequency.

4\. We must add up all those frequencies.



\# Approach-1: Using Frequency Array

Since nums\[i] is between 1 and 100, we use an array of size 101 to store frequency.



\#### Time complexity: \*\*O(n)\*\*

\#### Space complexity: \*\*O(1)\*\*





\## Java Code

```java \[]

class Solution {

&nbsp;   public int maxFrequencyElements(int\[] nums) {

&nbsp;       int\[] freq = new int\[101];

&nbsp;       for (int num : nums) {

&nbsp;           freq\[num]++;

&nbsp;       }

&nbsp;       int max = 0;

&nbsp;       for (int f : freq) {

&nbsp;           max = Math.max(max, f);

&nbsp;       }

&nbsp;       int result = 0;

&nbsp;       for (int f : freq) {

&nbsp;           if (f == max) {

&nbsp;               result += f;

&nbsp;           }

&nbsp;       }

&nbsp;       return result;

&nbsp;   }

}

```



\# Approach-2: Using HashMap

Use HashMap to store element → frequency.



\#### Time complexity: \*\*O(n)\*\*

\#### Space complexity: \*\*O(n)\*\*





\## Java Code

```java \[]

import java.util.\*;

class Solution {

&nbsp;   public int maxFrequencyElements(int\[] nums) {

&nbsp;       Map<Integer, Integer> map = new HashMap<>();

&nbsp;       for (int num : nums) {

&nbsp;           map.put(num, map.getOrDefault(num, 0) + 1);

&nbsp;       }

&nbsp;       int max = 0;

&nbsp;       for (int freq : map.values()) {

&nbsp;           max = Math.max(max, freq);

&nbsp;       }

&nbsp;       int sum = 0;

&nbsp;       for (int freq : map.values()) {

&nbsp;           if (freq == max) {

&nbsp;               sum += freq;

&nbsp;           }

&nbsp;       }

&nbsp;       return sum;

&nbsp;   }

}

```





\## Cpp / C++ Code

```Cpp \[]

class Solution {

public:

&nbsp;   int maxFrequencyElements(vector<int>\& nums) {

&nbsp;       int freq\[101] = {0};

&nbsp;       for (int num : nums) {

&nbsp;           freq\[num]++;

&nbsp;       }

&nbsp;       int maxFreq = 0;

&nbsp;       for (int i = 0; i <= 100; i++) {

&nbsp;           maxFreq = max(maxFreq, freq\[i]);

&nbsp;       }

&nbsp;       int result = 0;

&nbsp;       for (int i = 0; i <= 100; i++) {

&nbsp;           if (freq\[i] == maxFreq) {

&nbsp;               result += freq\[i];

&nbsp;           }

&nbsp;       }

&nbsp;       return result;

&nbsp;   }

};

```



\## JavaScript Code

```javascript \[]

var maxFrequencyElements = function(nums) {

&nbsp;   let freq = new Array(101).fill(0);

&nbsp;   for (let num of nums) {

&nbsp;       freq\[num]++;

&nbsp;   }

&nbsp;   let maxFreq = 0;

&nbsp;   for (let f of freq) {

&nbsp;       maxFreq = Math.max(maxFreq, f);

&nbsp;   }

&nbsp;   let result = 0;

&nbsp;   for (let f of freq) {

&nbsp;       if (f === maxFreq) {

&nbsp;           result += f;

&nbsp;       }

&nbsp;   }

&nbsp;   return result;

};

```















