# Intersection of two arrays II
## https://leetcode.com/problems/intersection-of-two-arrays-ii

Given two arrays, write a function to compute their intersection.
```
Example 1:

Input: nums1 = [1,2,2,1], nums2 = [2,2]
Output: [2,2]

Example 2:

Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
Output: [4,9]
```
**Note:**
1. Each element in the result should appear as many times as it shows in both arrays.
2. The result can be in any order.

**Follow up:**

What if the given array is already sorted? How would you optimize your algorithm?
What if nums1's size is small compared to nums2's size? Which algorithm is better?
What if elements of nums2 are stored on disk, and the memory is limited such that you cannot load all elements into the memory at once?

# Implementation :
```java
class Solution {
    public int[] intersect(int[] nums1, int[] nums2) {
        Map<Integer,Integer> map = new HashMap<>();
        for(int num : nums2) {
            if(!map.containsKey(num)) 
                map.put(num, 1);
            else 
                map.put(num, map.get(num)+1);
        }
        
        List<Integer> res = new ArrayList<>();
        for(int x : nums1) {
            if(map.containsKey(x) && map.get(x) > 0) {
                res.add(x);
                map.put(x, map.get(x) -1);
            }
        }
        
        int[] out = new int[res.size()];
        for(int i = 0; i < res.size(); i++)
            out[i] = res.get(i);
        
        return out;
    }
}
```
