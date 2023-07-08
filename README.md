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

