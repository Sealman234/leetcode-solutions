# LeetCode Solutions

## 169. Majority Element (Easy)

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var majorityElement = function(nums) {
    
    // helper
    const countInArray = (array, target) => {
        let count = 0;
        for(let i=0; i<=array.length; i++){
            if(array[i]===target) count+=1;
        }
        return count;
    }
    
    let countResults = [];
    for(let i=0; i<=nums.length; i++){
        countResults.push(countInArray(nums, nums[i]));
    }
    
    const maxCount = Math.max(...countResults);
    const maxCountIndex = countResults.findIndex(element => element === maxCount);
    
    return nums[maxCountIndex];
};
```
