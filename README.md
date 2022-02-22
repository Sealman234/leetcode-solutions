# LeetCode Solutions

## Table of contents

* [169. Majority Element](#169-majority-element)
* [136. Single Number](#136-single-number)
* [283. Move Zeroes](#283-move-zeroes)

## 169. Majority Element

:memo: Nested functions, [Array.prototype.findIndex()](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex)

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

:memo: [Array.prototype.sort()](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

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

  const sortedNums = nums.sort((a, b) => a - b);
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

## 283. Move Zeroes

```javascript
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var moveZeroes = function (nums) {
  let pointer = 0;
  for (let i = 0; i < nums.length; i++) {
    if (nums[i] !== 0) {
      nums[pointer] = nums[i];
      nums[i] = i === pointer ? nums[i] : 0;
      pointer++;
    }
  }
};
```
