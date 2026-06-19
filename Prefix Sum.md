### PREFIX AND SUFFIX

##### 1.https://leetcode.com/problems/subarray-sum-equals-k/
``` java
class Solution {
    public int subarraySum(int[] nums, int k) {
        HashMap <Integer,Integer> map = new HashMap<>();
        map.put(0,1);
        int sum = 0;
        int count = 0;
        
        for (int num : nums){
            sum+=num;
            if(map.containsKey(sum-k)){
                count+=map.get(sum-k);
            }
            map.put(sum,map.getOrDefault(sum,0)+1);
        }
        return count;
        
    }
}
``` 
##### 2. https://leetcode.com/problems/contiguous-array/

``` java
class Solution {
    public int findMaxLength(int[] nums) {
        HashMap<Integer,Integer> map = new HashMap<>();
        map.put(0,-1);
        int n= nums.length;
        int zero =0;
        int one = 0;
        int res = 0;

        for (int i=0; i<n; i++){
            if (nums[i]==0){
                zero++;
            }
            else{
                one++;
            }
            int diff = zero - one;
            if (!map.containsKey(diff)){
                map.put(diff,i);
            }else{
                int idx = map.get(diff);
                int len = i - idx;
                res = Math.max(res, len);
            }
        }
        return res;
    }
}
```

##### 3. https://leetcode.com/problems/subarray-sums-divisible-by-k/
``` java
class Solution {
    public int subarraysDivByK(int[] nums, int k) {
        HashMap <Integer , Integer> map = new HashMap<>();
        map.put(0,1);
        int sum = 0;
        int res = 0;
        for (int num: nums){
            sum+=num;
            int rem = ((sum%k)+k)%k;
            if (map.containsKey(rem)){
                res+=map.get(rem);
            }
            map.put(rem,map.getOrDefault(rem,0)+1);
        }
        return res;

    }
}
```
