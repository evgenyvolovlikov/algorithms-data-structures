## 1 Two Sum (Easy)

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

### Example 1:
```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```
### Example 2:
```
Input: nums = [3,2,4], target = 6
Output: [1,2]
```
### Example 3:
```
Input: nums = [3,3], target = 6
Output: [0,1]
```
### Solution:
```
const arrayOfNums = [2,7,11,15]
const arrayOfNumsV2 = [3,2,4]
const arrayOfNumsV3 = [3,3]

const twoSum = (nums, target) => {
  for(let i = 0; i < nums.length; i++){
    const numberToFind = target - nums[i]
    for(let j = i + 1; j < nums.length; j++) {
      if(numberToFind === nums[j]) {
        return [i, j]
      }
    }
  }
  return null
}

twoSum(arrayOfNums, 9)
twoSum(arrayOfNumsV2, 6)
twoSum(arrayOfNumsV3, 6)
```
## Solution 2 
```
const arrayOfNums = [2,7,11,15]; target = 9
const arrayOfNumsV2 = [3,2,4]; target = 6
const arrayOfNumsV3 = [3,3]; target = 6

const twoSum = (nums, target) => {
  const objMap = {}
  for(let i = 0; i < nums.length; i++) {
    const currentMapValue = objMap[nums[i]]
    if(currentMapValue >=0) {
      return [currentMapValue, i]
    } else {
      const numberToFind = target - nums[i]
      objMap[numberToFind] = i
    }
  }
  return null
}

twoSum(arrayOfNums, 9)
twoSum(arrayOfNumsV2, 6)
twoSum(arrayOfNumsV3, 6)
```

## 2 Anagram (Easy)
Write a function that event return true or false if it is anagram
### Example:
```
Input: "Я в мире — сирота.", "Я в мире — сирота."
Output: true
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```
## Solution 1
```
const anagram = (w1, w2) => {
  return w1.split("").sort().join("") === w2.splite("").sort().join("")
}

anagram("Я в мире — сирота.", "Я в мире — сирота.")
```
## 2.1 Anagram (Easy)
Create a function that makes up an array of strings and get an array as an output, as in the example below.

Input: const input = [
 "БОДРЯЧОК",
 "ДОБРЯЧОК",
 "КАНИСТРА",
 "СТАРИКАН",
 "СТАРИНКА",
 "ВСЕПРОЩЕНИЕ",
 "ПРОСВЕЩЕНИЕ",
 "javascript",
 "java",
]

Output: [
  ['БОДРЯЧОК', 'ДОБРЯЧОК']
  ['КАНИСТРА', 'СТАРИКАН', 'СТАРИНКА']
  ['ВСЕПРОЩЕНИЕ', 'ПРОСВЕЩЕНИЕ']
  ['javascript']
  ['java']
]

### Solution 1
```
const anagram = (input) => {
  const objMap = {}
  for(let i = 0; i < input.length; i++) {
    const key = input[i].split("").sort().join("")
    if(objMap[key]) {
      objMap[key].push(input[i])
    } else {
      objMap[key] = [input[i]]
    }
  }

  return Object.values(objMap)
}
```

## 3 Counter (Easy)
First write a function that adds up the arguments
### Example 1:
Input: 1,'2',3
Output: 123

### Example 2:
Input: 1,2,'3'
Output: 33

### Solution 1
```
const sum = (...args) => args.reduce((acc, val) => acc + val, 0) 
sum(1, '2', '3')
sum(1, 2, '3')
```

## 4 Move Zeroes (Easy)
Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.

### Example 1:

Input: nums = [0,1,0,3,12]
Output: [1,3,12,0,0]
Example 2:

Input: nums = [0]
Output: [0]

### Solution 1
```
const moveZeroes = (input) => {
  const array = [];
  const arrayOfZeroes = [];
  for(value of input) {
    if(value === 0) {
      arrayOfZeroes.push(value)
    } else {
      array.push(value)
    }
  }
  return [...array, ...arrayOfZeroes]
}

moveZeroes([0,1,0,3,12])
```

### Solution 2
```
const moveZeroes = (input) => {
  const zeroes = [];
  input = input.filter((val) => val !== 0 ? true : zeroes.push(val) && false);
  return input.concat(zeroes);
}

moveZeroes([0,1,0,3,12])
```

** Additional: Note that you must do this in-place without making a copy of the array.
### Solution 3
```
const moveZeroes = (input) => input.sort((a, b) => !a - !b);
moveZeroes([0,1,0,3,12])
```

### Solution 4
```
const moveZeroes = (input) => {
  let zeroCount = []

  for(let i = 0; i < input.length; i++){
    if(input[i] !== 0){
      input[zeroCount++] = input[i]
    }
  }

  for(let i = zeroCount; i < input.length; i++){
    input[i] = 0
  }

  return input
}

moveZeroes([0,1,0,3,12])
```
## 5 Contains Duplicates
Given an integer array nums, return true if any value appears at least twice in the array, and return false if every element is distinct.
### Example 1:
Input: nums = [1,2,3,1]
Output: true
### Example 2:
Input: nums = [1,2,3,4]
Output: false
### Example 3:
Input: nums = [1,1,1,3,3,4,3,2,4,2]
Output: true

### Solution 1
```
const containsDuplicate = function(input){
  for(let i = 0; i < input.length; i++){
    const value = input[i]

    for(let j = i + 1; j < input.length; j++){
      if(value === input[j]) {
        return true
      }
    }
  }
  return false
}

containsDuplicate([1,2,3,1])
containsDuplicate([1,2,3,4])
containsDuplicate([1,1,1,3,3,4,3,2,4,2])
```
### Solution 2
```
const containsDuplicate = (input) => {
  const uniqueMap = new Set(input)

  if(uniqueMap.size !== input.length) {
    return true
  } else {
    return false
  }
} 

containsDuplicate([1,2,3,1])
containsDuplicate([1,2,3,4])
containsDuplicate([1,1,1,3,3,4,3,2,4,2])
```
### Solution 3
```
const containsDuplicate = input => {
  let objMap = {}
    
  for(let i = 0; i < input.length; i++) {
    const currentMapValue = input[i]
    if(!objMap[currentMapValue]) {
      objMap[currentMapValue] = true
    } else if (objMap[currentMapValue]) {
      return true
    }
  }
  return false
}

containsDuplicate([1,2,3,1])
containsDuplicate([1,2,3,4])
containsDuplicate([1,1,1,3,3,4,3,2,4,2])
```
## 6 Palindrom (Easy)
A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string s, return true if it is a palindrome, or false otherwise.

### Example 1:

Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.
### Example 2:

Input: s = "race a car"
Output: false
Explanation: "raceacar" is not a palindrome.
### Example 3:

Input: s = " "
Output: true
Explanation: s is an empty string "" after removing non-alphanumeric characters.
Since an empty string reads the same forward and backward, it is a palindrome

<!-- TODO: добавить несколько решений задачи -->
### Solution 1
```
const isPalindrome = str => {
  const rmvSymStr = str.toLowerCase().replace(/[^A-Za-z0-9]/g, "")
  const reversedStr = rmvSymStr.split('').reverse().join('')

  return rmvSymStr === reversedStr
}

isPalindrome('A man, a plan, a canal: Panama')
```