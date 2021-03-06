# LeetCode Solutions

## Table of contents

* [169. Majority Element](#169-majority-element)
* [136. Single Number](#136-single-number)
* [283. Move Zeroes](#283-move-zeroes)
* [217. Contains Duplicate](#217-contains-duplicate)
* [268. Missing Number](#268-missing-number)
* [350. Intersection of Two Arrays II](#350-intersection-of-two-arrays-ii)
* [121. Best Time to Buy and Sell Stock](#121-best-time-to-buy-and-sell-stock)

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

:memo: Two pointer

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
      nums[i] = pointer === i ? nums[i] : 0;
      pointer++;
    }
  }
};
```

## 217. Contains Duplicate

```javascript
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var containsDuplicate = function (nums) {
  let isDuplicated = false;
  const sortedNums = nums.sort((a, b) => a - b);
  for (let i = 0; i < sortedNums.length; i++) {
    if (sortedNums[i] === sortedNums[i + 1]) {
      isDuplicated = true;
      return isDuplicated;
    }
  }
  return isDuplicated;
};
```

## 268. Missing Number

:memo: ??????????????? n ??????????????????Sn=(a1+an)*n/2

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var missingNumber = function (nums) {
  const wrongAmount = nums.reduce((a, b) => a + b);
  const correctAmount = ((1 + nums.length) * nums.length) / 2;
  return correctAmount - wrongAmount;
};
```

## 350. Intersection of Two Arrays II

```javascript
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var intersect = function (nums1, nums2) {
  let result = [];
  for (let i = 0; i < nums2.length; i++) {
    if (nums1.includes(nums2[i])) {
      result.push(nums2[i]);
      // ?????????????????????
      const pushedIndex = nums1.findIndex((el) => el === nums2[i]);
      nums1.splice(pushedIndex, 1);
    }
  }
  return result;
};
```

## 121. Best Time to Buy and Sell Stock

```javascript
/**
 * @param {number[]} prices
 * @return {number}
 */
var maxProfit = function (prices) {
  let maxProfit = 0;
  let min = prices[0];
  // ??????????????????????????????????????????????????????????????????
  for (let i = 1; i < prices.length; i++) {
    // ???????????? vs. ?????????????????? => ????????????????????????
    min = Math.min(prices[i], min);
    // (???????????? - ??????????????????) vs. ????????????????????? => ???????????????????????????
    maxProfit = Math.max(maxProfit, prices[i] - min);
  }
  return maxProfit;
};
```
