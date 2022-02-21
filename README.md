# LeetCode Solutions

## Table of contents

* [169. Majority Element](#169-majority-element)

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
    if (!used.find((el) => el === nums[i])) {
      used.push(nums[i]);
      if (countInArray(nums, nums[i]) > nums.length / 2) return nums[i];
    }
  }
};
```
