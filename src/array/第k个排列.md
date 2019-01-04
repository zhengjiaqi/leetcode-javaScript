###第k个排列

给出集合 [1,2,3,…,n]，其所有元素共有 n! 种排列。

按大小顺序列出所有排列情况，并一一标记，当 n = 3 时, 所有排列如下：

1. "123"
2. "132"
3. "213"
4. "231"
5. "312"
6. "321"
给定 n 和 k，返回第 k 个排列。

**说明**

- 给定 n 的范围是 [1, 9]。
- 给定 k 的范围是[1,  n!]。

**示例1:**

    输入: n = 3, k = 3
    输出: "213"

**示例2:**

    输入: n = 4, k = 9
    输出: "2314"

[解答思路](https://blog.csdn.net/sinat_35261315/article/details/78412805)

**解答：**

    /**
    * @param {number} n
    * @param {number} k
    * @return {string}
    */
    var getPermutation = function(n, k) {
        let arr = Array.apply(null, {length: n}).map(function(value, index){
                return index + 1;
                });
        let res = '';
        
        // 需要找到第k个排列（k从1开始），以第i个位置开头（i从1开始）
        console.log('arr:', arr)
        for(let i = 1; i <= n; i++){
            if(i !== n){
                let numIndex = Math.ceil(k / factorial(n - i)) - 1;
                if(numIndex >= arr.length){
                    numIndex = numIndex % arr.length;
                }
                let num = arr.splice(numIndex, 1)[0];
                res += num;
            } else {
                res += arr[0];
            }
        }
            
        function factorial(num) {
            if(num <= 1){
                return 1;       
            } else {
                return num * factorial(num - 1)
            }
        }
        return res
        
    };