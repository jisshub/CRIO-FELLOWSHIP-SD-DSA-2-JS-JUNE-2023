# DSA 2 B2 JULY 2023

[SESSION-3](#session-3)

[Two Pointer Approach](#two-pointer-approach)

# SESSION 1

# SESSION 3

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

https://chat.openai.com/share/11c1993d-11e3-4030-8951-8ee65222ef9f

