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
const arrayOfNums = [2,7,11,15];
const arrayOfNumsV2 = [3,2,4];
const arrayOfNumsV3 = [3,3];

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