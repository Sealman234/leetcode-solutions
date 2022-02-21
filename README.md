# LeetCode Solutions

## Table of contents

* [169. Majority Element](#169-majority-element)
* [136. Single Number](#136-single-number)

## 169. Majority Element

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var majorityElement = function (nums) {
  // helper
  const countInArray = (array, target) => {
    let count = 0;
    for (let i = 0; i <= array.length; i++) {
      if (array[i] === target) count += 1;
    }
    return count;
  };

  let used = [];
  for (let i = 0; i <= nums.length; i++) {
    if (used.findIndex((el) => el === nums[i]) === -1) {
      used.push(nums[i]);
      if (countInArray(nums, nums[i]) > nums.length / 2) return nums[i];
    }
  }
};
```

## 136. Single Number

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function (nums) {
  const countInArray = (array, target) => {
    let count = 0;
    for (let i = 0; i < array.length; i++) {
      if (array[i] === target) count += 1;
    }
    return count;
  };

  const sortedNums = nums.sort();
  let lastNum = null;
  for (let i = 0; i < sortedNums.length; i++) {
    if (lastNum !== sortedNums[i]) {
      lastNum = sortedNums[i];
      if (countInArray(sortedNums, sortedNums[i]) % 2 > 0) {
        return sortedNums[i];
      }
    }
  }
};
```
