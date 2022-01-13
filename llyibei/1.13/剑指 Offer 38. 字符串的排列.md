# [剑指 Offer 38. 字符串的排列](https://leetcode-cn.com/problems/zi-fu-chuan-de-pai-lie-lcof/)

### 解题思路1

1. 全排列一样的回溯算法，但是字符串中有可能有重复的字符
2. 首先想到处理res中的结果

### 代码实现1

这样其实使用了额外的空间，可以优化一下

```js
var permutation = function(s) {
    let nums = s.split('')
    const path = [],res = [];
    backTracking(nums,nums.length,[])
    let result = []
    //主要是靠这里
    res.forEach((item)=>{
        if(Array.isArray(item)){
            let str = item.join('')
            if(!result.includes(str)){
                result.push(str)
            }
        }
    })
    return result;
    function backTracking(n,k,used){
        if(path.length == k){
            res.push(Array.from(path))
            return
        }
        for(let i=0 ; i<k ; i++){
            if(used[i]) continue;
            path.push(n[i])
            used[i] = true
            backTracking(n,k,used)
            path.pop()
            used[i] = false
        }
    }
};
```

### 解题思路2

在递归函数中设定一个规则，保证在每填一个空位的时候重复字符只会被填入一次

！注意这里的判断是判断相邻位置是否重复，所以s转为num的时候要排序

### 代码实现2

```js
var permutation = function(s) {
    //注意这里
    let nums = s.split('').sort()
    const path = [],res = [],result = []
    backTracking(nums,nums.length,[])
    res.forEach((item)=>{
        if(Array.isArray(item)){
                result.push(item.join(''))
         }
    })
    return result
    function backTracking(n,k,used){
        if(path.length == k){
            res.push(Array.from(path))
            return
        }
        for(let i=0 ; i<k ; i++){
            if(used[i] || (i>0 && !used[i-1] && nums[i-1] === nums[i])) continue;
            path.push(n[i])
            used[i] = true
            backTracking(n,k,used)
            path.pop()
            used[i] = false
        }
    }
};
```

