# DSA 2 B2 JULY 2023

https://chat.openai.com/share/11c1993d-11e3-4030-8951-8ee65222ef9f


[SESSION-3](#session-3)

[Two Pointer Approach](#two-pointer-approach)

# SESSION 1

# SESSION 3

[Two Pointer Approach](#two-pointer-approach)

# SESSION 4

[Prefix Sum](#prefix-sum)

[Suffix Sum](#suffix-sum)

[Kadanes Algorithm](#kadanes-algorithm)

# SESSION 5

[Sliding Window Concept](#sliding-window-concept)

# SESSION 6

[Bubble Sort](#bubble-sort)


## Two Pointer Approach

In 2 pointer approach, 2-pointers point to specific indices or specific positions in the array.

Certainly! The two-pointer approach is a popular technique used in algorithmic problem-solving to efficiently solve certain types of problems. It involves using two pointers that move through the data structure in different directions or at different speeds to solve the problem more efficiently. Let's understand this concept with some simple examples.

### Example 1: Finding a Pair with a Given Sum

Let's say you have an array of integers, and you need to find if there exists a pair of numbers in the array that adds up to a given sum.

1. Start by initializing two pointers, let's call them 'left' and 'right,' to the first and last elements of the array, respectively.
   - 'left' points to the first element of the array.
   - 'right' points to the last element of the array.

2. Compare the sum of the elements pointed by 'left' and 'right' with the given target sum.
   - If the sum equals the target, you have found a pair that adds up to the given sum, so return true.
   - If the sum is greater than the target, move the 'right' pointer one step to the left.
   - If the sum is smaller than the target, move the 'left' pointer one step to the right.

3. Repeat step 2 until you find a pair or the 'left' pointer becomes greater than or equal to the 'right' pointer.
   - If the 'left' pointer becomes greater than or equal to the 'right' pointer, it means there is no pair that adds up to the given sum, so return false.

Here's an implementation in Python:

```python
def findPair(arr, target):
    arr.sort()  # Sort the array in ascending order
    left = 0
    right = len(arr) - 1

    while left < right:
        current_sum = arr[left] + arr[right]
        if current_sum == target:
            return True
        elif current_sum < target:
            left += 1
        else:
            right -= 1

    return False
```

### Example 2: Finding a Triplet with a Given Sum

Let's extend the previous example and consider that you need to find if there exists a triplet of numbers in the array that adds up to a given sum.

1. Start by initializing a pointer, let's call it 'i,' to the first element of the array.

2. For each 'i' from 0 to n-3 (where n is the size of the array):
   - Initialize two pointers, 'left' and 'right,' to the next element and the last element of the array, respectively.
   - Compare the sum of the elements pointed by 'i', 'left', and 'right' with the given target sum.
     - If the sum equals the target, you have found a triplet that adds up to the given sum, so return true.
     - If the sum is greater than the target, decrement the 'right' pointer.
     - If the sum is smaller than the target, increment the 'left' pointer.

3. Repeat step 2 until 'i' reaches n-3.
   - If you don't find any triplet that adds up to the given sum, return false.

Here's an implementation in Python:

```python
def findTriplet(arr, target):
    arr.sort()  # Sort the array in ascending order
    n = len(arr)

    for i in range(n - 2):
        left = i + 1
        right = n - 1

        while left < right:
            current_sum = arr[i] + arr[left] + arr[right]
            if current_sum == target:
                return True
            elif current_sum < target:
                left += 1
            else:
                right -= 1

    return False
```

### Example 1: Finding a Pair with a Given Sum

```python
def findPair(arr, target):
    arr.sort()  # Sort the array in ascending order
    left = 0
    right = len(arr) - 1

    while left < right:
        current_sum = arr[left] + arr[right]  # Calculate the sum of elements pointed by 'left' and 'right'
        if current_sum == target:  # If the sum equals the target, we found a pair
            return True
        elif current_sum < target:  # If the sum is smaller, move the 'left' pointer to the right
            left += 1
        else:  # If the sum is greater, move the 'right' pointer to the left
            right -= 1

    return False  # If no pair is found, return False
```

### Example 2: Finding a Triplet with a Given Sum

```python
def findTriplet(arr, target):
    arr.sort()  # Sort the array in ascending order
    n = len(arr)

    for i in range(n - 2):  # Loop through the array from the first element to the third-to-last element
        left = i + 1  # Initialize 'left' pointer to the next element after 'i'
        right = n - 1  # Initialize 'right' pointer to the last element of the array

        while left < right:  # Repeat until 'left' becomes greater than or equal to 'right'
            current_sum = arr[i] + arr[left] + arr[right]  # Calculate the sum of elements pointed by 'i', 'left', and 'right'
            if current_sum == target:  # If the sum equals the target, we found a triplet
                return True
            elif current_sum < target:  # If the sum is smaller, move the 'left' pointer to the right
                left += 1
            else:  # If the sum is greater, move the 'right' pointer to the left
                right -= 1

    return False  # If no triplet is found, return False
```

In both examples, the two-pointer approach is implemented as follows:

1. The input array is sorted in ascending order to facilitate the two-pointer technique.

2. Two pointers, 'left' and 'right,' are initialized to different positions in the array. In the first example, 'left' starts from the beginning, and 'right' starts from the end. In the second example, an additional pointer 'i' is used to iterate through the array, and 'left' and 'right' are initialized accordingly.

3. The two pointers move towards each other by adjusting their positions based on certain conditions.

   - If the sum of the elements pointed by the two pointers is equal to the target sum, we have found the desired pair/triplet, and we can return true.

   - If the sum is less than the target, we move the 'left' pointer one step to the right, as increasing its value will result in a larger sum.

   - If the sum is greater than the target, we move the 'right' pointer one step to the left, as decreasing its value will result in a smaller sum.

4. We repeat the process until the pointers meet (in the case of the first example) or until the 'i' pointer reaches the third-to-last element (in the case of the second example).

5. If no pair/triplet is found, we return false.

The two-pointer approach leverages the sorted nature of the array and exploits the fact that moving the pointers in certain directions allows us to avoid unnecessary computations, leading to more efficient solutions for specific problem types.

### Question:

Explain two pointer approach using below array and target sum ?
Array: [2, 4, 5, 8, 9]
Target Sum: 13

### Solution:

Sure! Let's apply the two-pointer approach to the given array and target sum.

Array: [2, 4, 5, 8, 9]
Target Sum: 13

1. Start by initializing two pointers, 'left' and 'right,' to the first and last elements of the array, respectively.
   - 'left' points to 2.
   - 'right' points to 9.

2. Calculate the sum of the elements pointed by 'left' and 'right':
   - Current Sum: 2 + 9 = 11

3. Compare the current sum with the target sum (13):
   - The current sum (11) is less than the target sum (13).

4. Since the current sum is less than the target sum, we need to increase the sum. To achieve that, we move the 'left' pointer one step to the right.
   - 'left' now points to 4.

5. Calculate the new sum of the elements pointed by 'left' and 'right':
   - Current Sum: 4 + 9 = 13

6. Compare the current sum with the target sum (13):
   - The current sum (13) equals the target sum (13).

7. We have found a pair (4, 9) that adds up to the target sum (13). Therefore, we can return true.

In this example, the two-pointer approach allowed us to find a pair in the array that adds up to the given target sum efficiently. The pointers started from different ends of the array and moved towards each other until the sum matched the target or the pointers met. By utilizing the fact that the array was sorted, we were able to minimize the number of comparisons and optimize the solution.

### Time Complexity

The time complexity of the two-pointer approach for finding a pair with a given sum in an unsorted array is O(n^2).

In the scenario where the array is unsorted, we cannot utilize the two-pointer approach optimally. Instead, we would need to compare each element with every other element to find the pair that adds up to the target sum.

Here's a step-by-step breakdown of the approach for an unsorted array:

1. Start with the first element and compare it with all other elements in the array.
2. Move to the second element and compare it with the remaining elements.
3. Repeat this process for each element in the array, comparing it with the remaining elements.
4. If at any point we find a pair that adds up to the target sum, we can return true.

This approach requires nested loops, resulting in a time complexity of O(n^2), where n is the size of the array. The first loop iterates n times, and for each iteration, the second loop iterates n-1 times on average.

It's important to note that the two-pointer approach is most efficient when the array is sorted, as it allows us to optimize the search by moving the pointers strategically. When the array is unsorted, alternative approaches such as hashing or using a set can provide more efficient solutions with a time complexity of O(n).

## Prefix Sum

- Any array having integers.
- Prefix sum is the cumulative sum of the array.
Eg: arr = [10, 4, 50, 6, 60, 7]

Prefix sum at index 0 is that same element meaning prefix  sum at 
- index 0 is 10, arr[0] = 10
- index 1 is 14, arr[0] + arr[1] = 14
- index 2 is 64, arr[0] + arr[1] + arr[2] = 64


We can create a prefix sum array for given array

prefifxSumArr = [10, 14, 64, 70, 130, 137]
                    or
              = 
              [arr[0], arr[0]+arr[1], arr[0]+arr[1]+arr[2],               arr[0]+arr[1]+arr[2]+arr[3], arr[0]+arr[1]+arr[2]+arr[3]+arr[4]]

Certainly! The prefix sum concept is a useful technique in algorithmic problem-solving. It involves calculating prefix sums for an array to efficiently answer queries about subarray sums. Let's understand this concept with some simple examples.

Example 1: Finding the Subarray Sum

Suppose you have an array of integers, and you need to find the sum of elements in a given subarray from index 'start' to index 'end.'

1. Start by initializing a prefix sum array, 'prefix,' with the same size as the input array, filled with zeros.
   - 'prefix' will store the cumulative sums up to each index in the original array.

2. Calculate the prefix sum for the original array by iterating through it:
   - For each index 'i' from 0 to n-1 (where n is the size of the array):
     - If 'i' is 0, set prefix[0] = arr[0].
     - Otherwise, set prefix[i] = prefix[i-1] + arr[i].
     - By doing this, each element in the prefix sum array represents the sum of all elements from index 0 up to that particular index in the original array.

3. To find the sum of the subarray from 'start' to 'end':
   - If 'start' is 0, the sum is simply prefix[end].
   - Otherwise, the sum is prefix[end] - prefix[start-1].
     - Subtracting prefix[start-1] cancels out the sum of elements before the 'start' index, leaving only the sum of the desired subarray.

Here's an implementation in Python:

```python
def subarraySum(arr, start, end):
    n = len(arr)
    prefix = [0] * n

    prefix[0] = arr[0]
    for i in range(1, n):
        prefix[i] = prefix[i-1] + arr[i]

    if start == 0:
        return prefix[end]
    else:
        return prefix[end] - prefix[start-1]
```

Example 2: Finding the Count of Subarrays with a Given Sum

Let's extend the previous example and consider that you need to find the count of subarrays in the array that adds up to a given sum.

1. Initialize a prefix sum variable, 'prefix_sum,' to zero.
   - 'prefix_sum' will keep track of the cumulative sum up to the current index.

2. Initialize a dictionary, 'sum_count,' to store the count of prefix sums encountered so far.
   - Initialize it with one entry: {0: 1}, since a prefix sum of zero is encountered before starting the traversal.

3. Iterate through the array:
   - For each index 'i' from 0 to n-1 (where n is the size of the array):
     - Update the 'prefix_sum' by adding the current element arr[i].
     - Check if 'prefix_sum' - target_sum exists in the 'sum_count' dictionary.
       - If it does, increment the count by 'sum_count[prefix_sum - target_sum]'.
     - Increment the count of 'prefix_sum' in 'sum_count' by one.

4. After traversing the entire array, the 'sum_count' dictionary will contain the count of subarrays with the target sum.

Here's an implementation in Python:

```python
def countSubarraysWithSum(arr, target_sum):
    prefix_sum = 0
    sum_count = {0: 1}
    count = 0

    for num in arr:
        prefix_sum += num
        if prefix_sum - target_sum in sum_count:
            count += sum_count[prefix_sum - target_sum]
        sum_count[prefix_sum] = sum_count.get(prefix_sum, 0) + 1

    return count
```

### Example 1:

Let's understand the prefix sum approach using the given array:

Array: [10, 4, 50, 6, 60, 7]

1. Initialize a prefix sum array, 'prefix,' with the same size as the input array, filled with zeros.

   - prefix = [0, 0, 0, 0, 0, 0]

2. Calculate the prefix sum for the original array by iterating through it:

   - For each index 'i' from 0 to n-1 (where n is the size of the array):

     - If 'i' is 0, set prefix[0] = arr[0].

       - prefix = [10, 0, 0, 0, 0, 0]

     - Otherwise, set prefix[i] = prefix[i-1] + arr[i].

       - prefix = [10, 14, 64, 70, 130, 137]

     - By doing this, each element in the prefix sum array represents the sum of all elements from index 0 up to that particular index in the original array.

3. Now, the prefix sum array is ready, and we can utilize it to efficiently answer queries about subarray sums.

   - For example, if we want to find the sum of elements in the subarray from index 1 to index 4:

     - The sum is given by prefix[4] - prefix[0].

       - sum = prefix[4] - prefix[0] = 130 - 10 = 120

     - By subtracting prefix[0] from prefix[4], we cancel out the sum of elements before index 1, leaving only the sum of the desired subarray.

The prefix sum approach allows us to preprocess the array and calculate cumulative sums efficiently. This precomputation enables us to answer subarray sum queries in constant time complexity, regardless of the size of the subarray.              

### Example 2:

Sure! Let's understand the prefix sum concept using the given array:

Array: [10, 20, 10, 5, 15]

1. Initialize a prefix sum array, 'prefix,' with the same size as the input array, filled with zeros.

   - prefix = [0, 0, 0, 0, 0]

2. Calculate the prefix sum for the original array by iterating through it:

   - For each index 'i' from 0 to n-1 (where n is the size of the array):

     - If 'i' is 0, set prefix[0] = arr[0].

       - prefix = [10, 0, 0, 0, 0]

     - Otherwise, set prefix[i] = prefix[i-1] + arr[i].

       - prefix = [10, 30, 40, 45, 60]

     - By doing this, each element in the prefix sum array represents the sum of all elements from index 0 up to that particular index in the original array.

3. Now, the prefix sum array is ready, and we can utilize it to answer various subarray sum queries efficiently.

   - For example, if we want to find the sum of elements in the subarray from index 1 to index 3:

     - The sum is given by prefix[3] - prefix[0].

       - sum = prefix[3] - prefix[0] = 45 - 10 = 35

     - By subtracting prefix[0] from prefix[3], we cancel out the sum of elements before index 1, leaving only the sum of the desired subarray.

   - Similarly, if we want to find the sum of elements in the subarray from index 2 to index 4:

     - The sum is given by prefix[4] - prefix[1].

       - sum = prefix[4] - prefix[1] = 60 - 30 = 30

     - By subtracting prefix[1] from prefix[4], we cancel out the sum of elements before index 2, leaving only the sum of the desired subarray.

The prefix sum concept allows us to calculate cumulative sums efficiently and provides a way to answer subarray sum queries in constant time complexity. By precomputing the prefix sum array, we can eliminate the need for repetitive sum calculations and solve various subarray sum problems more efficiently.

<!-- time: 23:00 -->

## Suffix Sum

- Opposite of Prefix Sum.

- In the suffix sum concept, we calculate the cumulative sums starting from the end of the array instead of the beginning. The idea is to store the sums of elements from each index to the end of the array. This allows us to efficiently answer queries about subarray sums that end at a specific index.

Let's understand the suffix sum concept using the given array:

Array: [10, 20, 10, 5, 15]

Certainly! Let's go through the array step by step to understand how the suffix sum is calculated:

Array: [10, 20, 10, 5, 15]

1. Initialize a suffix sum array, 'suffix,' with the same size as the input array, filled with zeros.

   - suffix = [0, 0, 0, 0, 0]

2. Calculate the suffix sum for the original array by iterating through it in reverse:

   - Start from the last index (index 4 in this case) and move towards the beginning.

   - For each index 'i' from 4 to 0:

     - The suffix sum at the last index is equal to the element at that index itself.

       - suffix[4] = arr[4] = 15

     - Now, let's calculate the suffix sum for index 3:
       - suffix[3] = arr[3] + suffix[4]

       - suffix[3] = 5 + 15 = 20

       - The suffix sum at index 3 is the sum of the current element (5) and the suffix sum at the next index (15).

     - Moving to index 2:
       - suffix[2] = arr[2] + suffix[3]

       - suffix[2] = 10 + 20 = 30

       - The suffix sum at index 2 is the sum of the current element (10) and the suffix sum at the next index (20).

     - Continuing to index 1:
       - suffix[1] = arr[1] + suffix[2]

       - suffix[1] = 20 + 30 = 50

       - The suffix sum at index 1 is the sum of the current element (20) and the suffix sum at the next index (30).

     - Finally, at index 0:
       - suffix[0] = arr[0] + suffix[1]

       - suffix[0] = 10 + 50 = 60

       - The suffix sum at index 0 is the sum of the current element (10) and the suffix sum at the next index (50).

3. Now, the suffix sum array is ready, and we have calculated the cumulative sums starting from the end of the array.

   - suffix = [60, 50, 30, 20, 15]

   - Each element in the suffix sum array represents the sum of all elements from that index up to the last index in the original array.


## Finding Suffix Sum for Another Array

Certainly! Let's consider another example to understand the concept of suffix sum on an array:

Array: [5, 2, 6, 1, 9]

1. Initialize a suffix sum array, 'suffix,' with the same size as the input array, filled with zeros.

   - suffix = [0, 0, 0, 0, 0]

2. Calculate the suffix sum for the original array by iterating through it in reverse:

   - Start from the last index (index 4 in this case) and move towards the beginning.

   - For each index 'i' from 4 to 0:

     - The suffix sum at the last index is equal to the element at that index itself.

       - suffix[4] = arr[4] = 9

     - Now, let's calculate the suffix sum for index 3:
       - suffix[3] = arr[3] + suffix[4]

       - suffix[3] = 1 + 9 = 10

       - The suffix sum at index 3 is the sum of the current element (1) and the suffix sum at the next index (9).

     - Moving to index 2:
       - suffix[2] = arr[2] + suffix[3]

       - suffix[2] = 6 + 10 = 16

       - The suffix sum at index 2 is the sum of the current element (6) and the suffix sum at the next index (10).

     - Continuing to index 1:
       - suffix[1] = arr[1] + suffix[2]

       - suffix[1] = 2 + 16 = 18

       - The suffix sum at index 1 is the sum of the current element (2) and the suffix sum at the next index (16).

     - Finally, at index 0:
       - suffix[0] = arr[0] + suffix[1]

       - suffix[0] = 5 + 18 = 23

       - The suffix sum at index 0 is the sum of the current element (5) and the suffix sum at the next index (18).

3. Now, the suffix sum array is ready, and we have calculated the cumulative sums starting from the end of the array.

   - suffix = [23, 18, 16, 10, 9]

   - Each element in the suffix sum array represents the sum of all elements from that index up to the last index in the original array.

## Kadanes Algorithm

Certainly! Let's go through the steps of Kadane's algorithm again, using the example [−2, 1, −3, 4, −1, 2, 1, −5, 4]:

Step 1: Initialize 'max_sum' and 'current_sum' as -2 (the first element of the array).

   - max_sum = -2
   - current_sum = -2

Step 2: Iterate through the array, starting from the second element.

   - For each element 'num' from the second element to the end of the array:
   
     Iteration 1: Element 1 (Index 1)
     
     - Compare the current element (1) with the sum of the current element and 'current_sum'.
       - current_sum = max(1, 1 + (-2)) = max(1, -1) = 1 (choose the current element)
     
     - Update the maximum sum by taking the maximum of 'max_sum' and 'current_sum'.
       - max_sum = max(-2, 1) = 1 (update 'max_sum' with the current maximum sum encountered)

     Iteration 2: Element -3 (Index 2)

     - Compare the current element (-3) with the sum of the current element and 'current_sum'.
       - current_sum = max(-3, -3 + 1) = max(-3, -2) = -2 (choose the sum of the current element and 'current_sum')

     - Update the maximum sum by taking the maximum of 'max_sum' and 'current_sum'.
       - max_sum = max(1, -2) = 1 (no change to 'max_sum')

     Iteration 3: Element 4 (Index 3)

     - Compare the current element (4) with the sum of the current element and 'current_sum'.
       - current_sum = max(4, 4 + (-2)) = max(4, 2) = 4 (choose the current element)

     - Update the maximum sum by taking the maximum of 'max_sum' and 'current_sum'.
       - max_sum = max(1, 4) = 4 (update 'max_sum' with the current maximum sum encountered)

     ...and so on, continuing these steps for each element of the array.

Step 3: After completing the iteration, 'max_sum' will hold the maximum subarray sum.

   - In our example, the maximum subarray sum is 6, which occurs in the subarray [4, -1, 2, 1].

The workflow of Kadane's algorithm involves iterating through the array and comparing the current element with the sum of the current element and the previous 'current_sum'. By choosing the maximum of the two, we update 'current_sum' and keep track of the maximum subarray sum encountered so far in 'max_sum'.

## SESSION 5

### Sliding Window Concept

Certainly! I'll explain the sliding window approach step by step using simple terms. The sliding window technique is used to efficiently process subarrays or substrings of a given array or string. Let's go through it:

Given an array, let's say: [3, 1, 7, 2, 5, 8, 4]

1. Initialize two pointers, 'start' and 'end,' to the first element of the array.

   - start = 0 (index of the first element)
   - end = 0

2. Initialize a variable, 'window_sum,' to the value of the first element in the array.

   - window_sum = 3 (the first element)

3. Iterate through the array, moving the 'end' pointer to the right.

   - For each step, update 'window_sum' by adding the element at the 'end' pointer.

     - For example, when 'end' is at index 1:
       - window_sum += 1 (add the element at index 1 to 'window_sum')

   - Check if the current window satisfies the desired condition or if it needs adjustment.

     - If the current window satisfies the condition, update the result or perform any necessary operations.
     - If the current window does not satisfy the condition, move the 'start' pointer to the right, adjusting the window.

4. Repeat the iteration until the 'end' pointer reaches the end of the array.

5. After the iteration, the result or desired output is available based on the operations performed during the iteration.

Now, let's work through an example using the array [3, 1, 7, 2, 5, 8, 4] and the condition of finding the maximum sum of a subarray of length 3.

1. Initialize 'start' and 'end' as 0, and 'window_sum' as the value of the first element.

   - start = 0
   - end = 0
   - window_sum = 3

2. Move the 'end' pointer to the right and update 'window_sum'.

   - When 'end' is at index 1:
     - window_sum += 1, so window_sum becomes 4

3. Check if the current window satisfies the desired condition (subarray length = 3).

   - Since the length of the current window is not yet 3, we continue to the next step.

4. Repeat steps 2 and 3, moving the 'end' pointer and updating 'window_sum'.

   - When 'end' is at index 2:
     - window_sum += 7, so window_sum becomes 11

   - When 'end' is at index 3:
     - window_sum += 2, so window_sum becomes 13

   - When 'end' is at index 4:
     - Since the length of the current window is now 3, we can perform the desired operation (in this case, finding the maximum sum of the subarray).

     - We can store or update the maximum sum, perform calculations, or any other operation required based on the current window.

5. Move the 'start' pointer to the right to adjust the window.

   - When 'start' is moved to index 1:
     - Subtract the element at the 'start' index from 'window_sum'.

   - Repeat steps 2-4 until the 'end' pointer reaches the end of the array.

By sliding the window and adjusting the 'start' and 'end' pointers, we efficiently process subarrays or substrings of the given array or string. The specific operations or conditions inside the window can vary depending on the problem requirements.

# SESSION 6

## SORTING

Sorting Types

   1. Comparison Sort (Bubble Sort)
   2. Count Sort (Radix Sort, Count Sort)

### Inplace Sort 

  Sort the elements in the given array itself.

  [2, 1, 3] -> [1, 2, 3]

  We just rearrange the elements in increasing order.

  Eg: Bubble Sort, Insertion Sort and Selection Sort (Iterative Strategy)

### Not In Place Sort

  We make use of another array to sort the elements.

  Eg: Merge Sort and Quick Sort (Recursive Strategy)


## Bubble Sort

Certainly! Bubble sort is a simple and intuitive sorting algorithm commonly used in algorithmic problem-solving. It repeatedly swaps adjacent elements if they are in the wrong order until the entire array is sorted. Let's understand the bubble sort algorithm with an example.

Example: Sorting an Array using Bubble Sort

Consider the following array:

Array: [5, 3, 8, 2, 1]

1. Start by comparing the first and second elements. If the second element is smaller, swap them.

   - Compare 5 and 3: Since 3 is smaller, swap them.
     - Array after the swap: [3, 5, 8, 2, 1]

2. Move to the next pair (second and third elements) and compare them. If the second element is smaller, swap them.

   - Compare 5 and 8: Since they are in the correct order, no swap is needed.
     - Array remains: [3, 5, 8, 2, 1]

3. Continue this process, comparing adjacent elements and swapping if necessary, until the end of the array.

   - Compare 8 and 2: Swap them.
     - Array after the swap: [3, 5, 2, 8, 1]

   - Compare 8 and 1: Swap them.
     - Array after the swap: [3, 5, 2, 1, 8]

4. After the first iteration, the largest element (8) is in its correct position at the end of the array.

5. Repeat the process for the remaining unsorted portion of the array (excluding the last element).

   - Compare 3 and 5: Since they are in the correct order, no swap is needed.
     - Array remains: [3, 5, 2, 1, 8]

   - Compare 5 and 2: Swap them.
     - Array after the swap: [3, 2, 5, 1, 8]

   - Compare 5 and 1: Swap them.
     - Array after the swap: [3, 2, 1, 5, 8]

6. Repeat the process until the entire array is sorted.

  - Compare 3 and 2: Swap them.
    - Array after the swap: [2, 3, 1, 5, 8]


  - Compare 3 and 1: Swap them.
    - Array after the swap: [2, 1, 3, 5, 8]


  - Compare 3 and 5: Since they are in the correct order, no swap is needed.
    - Array remains: [2, 1, 3, 5, 8]


  - Compare 5 and 8: Since they are in the correct order, no swap is needed.
    - Array remains: [2, 1, 3, 5, 8]

7. Compare 2 and 1: Swap them.
  - Array after the swap: [1, 2, 3, 5, 8]

- No more swaps are needed since the array is now sorted.

The final sorted array is: [1, 2, 3, 5, 8].

The bubble sort algorithm repeatedly traverses the array and compares adjacent elements. It swaps them if they are in the wrong order, pushing the larger elements towards the end of the array. This process is repeated until the entire array is sorted.

It's worth noting that bubble sort has a time complexity of O(n^2) in the worst and average cases, where n is the size of the array. Additionally, it is an in-place sorting algorithm, meaning it sorts the elements within the original array without requiring additional memory. However, bubble sort is not considered efficient for large datasets and is mostly used for educational purposes or when dealing with small arrays.

### Insertion Sort



Certainly! Insertion sort is a simple and efficient sorting algorithm commonly used in algorithmic problem-solving. It works by dividing the array into two parts: a sorted subarray and an unsorted subarray. The algorithm iterates through the unsorted subarray, selecting one element at a time and inserting it into its correct position in the sorted subarray. Let's understand the insertion sort algorithm with an example.

Example: Sorting an Array using Insertion Sort

Consider the following array:

Array: [5, 3, 8, 2, 1]

1. Start with the second element (index 1) and assume it is in the correct position within the sorted subarray.

2. Compare the selected element with the elements in the sorted subarray (to its left) and insert it into the correct position.

   - Compare 3 with 5: Since 3 is smaller, shift 5 to the right.
     - Array after the shift: [3, 5, 8, 2, 1]

3. The selected element (3) is now in its correct position within the sorted subarray.

4. Repeat steps 2 and 3 for the remaining unsorted subarray.

   - Select the third element (index 2) and compare it with the elements in the sorted subarray.

   - Compare 8 with 5: Since 8 is larger, leave it in its current position.

   - The selected element (8) is already in its correct position within the sorted subarray.

   - Array remains: [3, 5, 8, 2, 1]

5. Select the fourth element (index 3) and compare it with the elements in the sorted subarray.

   - Compare 2 with 8: Since 2 is smaller, shift 8 to the right.
     - Array after the shift: [3, 5, 2, 8, 1]

   - Compare 2 with 5: Since 2 is smaller, shift 5 to the right.
     - Array after the shift: [3, 2, 5, 8, 1]

   - Compare 2 with 3: Since 2 is smaller, shift 3 to the right.
     - Array after the shift: [2, 3, 5, 8, 1]

6. The selected element (2) is now in its correct position within the sorted subarray.

7. Repeat steps 2 and 3 for the remaining unsorted subarray.

   - Select the fifth element (index 4) and compare it with the elements in the sorted subarray.

   - Compare 1 with 8: Since 1 is smaller, shift 8 to the right.
     - Array after the shift: [2, 3, 5, 1, 8]

   - Compare 1 with 5: Since 1 is smaller, shift 5 to the right.
     - Array after the shift: [2, 3, 1, 5, 8]

   - Compare 1 with 3: Since 1 is smaller, shift 3 to the right.
     - Array after the shift: [2, 1, 3, 5, 8]

   - Compare 1 with 2: Since 1 is smaller, shift 2 to the right.
     - Array after the shift: [1, 2, 3, 5, 8]

8. The selected element (1) is now in its correct position within the sorted subarray.

9. No more unsorted elements remain, and the array is now sorted.

The final sorted array is: [1, 2, 3, 5, 8].

The insertion sort algorithm works by iteratively selecting an element from the unsorted subarray and inserting it into its correct position within the sorted subarray. This process continues until all elements are in their correct positions. Insertion sort is efficient for small datasets or partially sorted datasets but can be less efficient for large datasets. It has a time complexity of O(n^2) in the worst case, where n is the size of the array. However, it has a best-case time complexity of O(n) when the array is already sorted or nearly sorted.
  
### Selection Sort
