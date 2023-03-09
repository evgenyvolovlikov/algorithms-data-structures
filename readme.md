## Two Sum (Easy)

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
## Solution:

```
const arrayOfNums = [2,7,11,15];
const arrayOfNumsV2 = [3,2,4];
const arrayOfNumsV3 = [3,3];

const twoSum = (nums, target) => {
  for(let i = 0; i < nums.length; i++){
    const numberToFind = target - nums[i];
    for(let j = i + 1; j < nums.length; j++) {
      if(numberToFind === nums[j]) {
        return [i, j];
      }
    }
  }
  return null;
}

twoSum(arrayOfNums, 9);
twoSum(arrayOfNumsV2, 6);
twoSum(arrayOfNumsV3, 6);
```

## Solution 2 
```
const arrayOfNums = [2,7,11,15]; target = 9
const arrayOfNumsV2 = [3,2,4]; target = 6
const arrayOfNumsV3 = [3,3]; target = 6

const twoSum = (nums, target) => {
  const objMap = {};
  for(let i = 0; i < nums.length; i++) {
    const currentMapValue = objMap[nums[i]];
    if(currentMapValue >=0) {
      return [currentMapValue, i];
    } else {
      const numberToFind = target - nums[i];
      objMap[numberToFind] = i;
    }
  }
  return null;
}

twoSum(arrayOfNums, 9);
twoSum(arrayOfNumsV2, 6);
twoSum(arrayOfNumsV3, 6);
```
