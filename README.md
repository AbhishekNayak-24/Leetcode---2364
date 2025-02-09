# Leetcode---2364
Count Number Of Bad Pairs
//code in java
import java.util.HashMap;
import java.util.Map;

class Solution {
    public long countBadPairs(int[] nums) {
        Map<Integer, Integer> map = new HashMap<>();
        long totalPairs = 0;
        long goodPairs = 0;

        for (int i = 0; i < nums.length; i++) {
            int diff = nums[i] - i;
            if (map.containsKey(diff)) {
                goodPairs += map.get(diff);
            }
            map.put(diff, map.getOrDefault(diff, 0) + 1);
        }

        totalPairs = (long) nums.length * (nums.length - 1) / 2;
        return totalPairs - goodPairs;
    }

    public static void main(String[] args) {
        Solution solution = new Solution();
        int[] nums = {4, 1, 3, 3};
        long result = solution.countBadPairs(nums);
        System.out.println("The number of bad pairs is: " + result); // Output: 5
    }
}
