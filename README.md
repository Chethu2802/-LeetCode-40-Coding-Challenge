# LeetCode-40-Coding-Challenge

All 40 Coding Solutions 
 
*EASY - 20 Problems* 
1. Two Sum 
 
class Solution { 
    public int[] twoSum(int[] nums, int target) { 
        Map<Integer, Integer> map = new HashMap<>(); 
        for (int i = 0; i < nums.length; i++) { 
            int need = target - nums[i]; 
            if (map.containsKey(need)) { 
                return new int[]{map.get(need), i}; 
            } 
            map.put(nums[i], i); 
        } 
        return new int[0]; 
    } 
} 
 
2. Palindrome Number 
class Solution { 
    public boolean isPalindrome(int x) { 
        if (x < 0) return false; 
        int original = x; 
        int reversed = 0; 
        while (x > 0) { 
            reversed = reversed * 10 + x % 10; 
            x /= 10; 
        } 
        return reversed == original; 
    } 
} 
 
3. Roman to Integer 
 
class Solution { 
    public int romanToInt(String s) { 
        int result = 0, prev = 0; 
        for (int i = s.length() - 1; i >= 0; i--) { 
            int curr = 0; 
            switch (s.charAt(i)) { 
                case 'I': curr = 1; break; 
                case 'V': curr = 5; break; 
                case 'X': curr = 10; break; 
                case 'L': curr = 50; break; 
                case 'C': curr = 100; break; 
                case 'D': curr = 500; break; 
                case 'M': curr = 1000; break; 
            } 
            if (curr < prev) result -= curr; 
            else result += curr; 
            prev = curr; 
        } 
        return result; 
    } 
} 
 
4. Longest Common Prefix 
 
class Solution { 
    public String longestCommonPrefix(String[] strs) { 
        String prefix = strs[0]; 
        for (int i = 1; i < strs.length; i++) { 
            while (!strs[i].startsWith(prefix)) { 
                prefix = prefix.substring(0, prefix.length() - 1); 
                if (prefix.isEmpty()) return ""; 
            } 
        } 
        return prefix; 
    } 
} 
 
5. Merge Two Sorted Lists 
 
class Solution { 
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) { 
        ListNode dummy = new ListNode(0); 
        ListNode current = dummy; 
        while (list1 != null && list2 != null) { 
            if (list1.val < list2.val) { 
                current.next = list1; 
                list1 = list1.next; 
            } else { 
                current.next = list2; 
                list2 = list2.next; 
            } 
            current = current.next; 
        } 
        current.next = (list1 != null) ? list1 : list2; 
        return dummy.next; 
    } 
} 
 
6. Remove Duplicates from Sorted Array 
 
class Solution { 
    public int removeDuplicates(int[] nums) { 
        int k = 1; 
        for (int i = 1; i < nums.length; i++) { 
            if (nums[i] != nums[i - 1]) { 
                nums[k++] = nums[i]; 
            } 
        } 
        return k; 
    } 
} 
 
7. Remove Element 
 
class Solution { 
    public int removeElement(int[] nums, int val) { 
        int k = 0; 
        for (int num : nums) { 
            if (num != val) nums[k++] = num; 
        } 
        return k; 
    } 
} 
 
8. Find the Index of the First Occurrence in a String 
 
class Solution { 
    public int strStr(String haystack, String needle) { 
        for (int i = 0; i <= haystack.length() - needle.length(); i++) { 
            if (haystack.substring(i, i + needle.length()).equals(needle)) { 
                return i; 
            } 
        } 
        return -1; 
    } 
} 
 
9. Search Insert Position 
 
class Solution { 
    public int searchInsert(int[] nums, int target) { 
        int left = 0, right = nums.length - 1; 
        while (left <= right) { 
            int mid = left + (right - left) / 2; 
            if (nums[mid] == target) return mid; 
            else if (nums[mid] < target) left = mid + 1; 
            else right = mid - 1; 
        } 
        return left; 
    } 
} 
 
10. Length of Last Word 
 
class Solution { 
    public int lengthOfLastWord(String s) { 
        s = s.trim(); 
        int length = 0; 
        for (int i = s.length() - 1; i >= 0 && s.charAt(i) != ' '; i--) { 
            length++; 
        } 
        return length; 
    } 
} 
 
11. Plus One 
 
class Solution { 
    public int[] plusOne(int[] digits) { 
        for (int i = digits.length - 1; i >= 0; i--) { 
            if (digits[i] < 9) { 
                digits[i]++; 
                return digits; 
            } 
            digits[i] = 0; 
        } 
        int[] result = new int[digits.length + 1]; 
        result[0] = 1; 
        return result; 
    } 
} 
 
12. Sqrt(x) 
 
class Solution { 
    public int mySqrt(int x) { 
        if (x < 2) return x; 
        long left = 1, right = x / 2, ans = 0; 
        while (left <= right) { 
            long mid = left + (right - left) / 2; 
            long sq = mid * mid; 
            if (sq == x) return (int) mid; 
            if (sq < x) { 
                ans = mid; 
                left = mid + 1; 
            } else { 
                right = mid - 1; 
            } 
        } 
        return (int) ans; 
    } 
} 
13. Climbing Stairs 
 
class Solution { 
    public int climbStairs(int n) { 
        if (n <= 2) return n; 
        int first = 1, second = 2; 
        for (int i = 3; i <= n; i++) { 
            int third = first + second; 
            first = second; 
            second = third; 
        } 
        return second; 
    } 
} 
 
14. Best Time to Buy and Sell Stock 
 
class Solution { 
    public int maxProfit(int[] prices) { 
        int minPrice = Integer.MAX_VALUE; 
        int maxProfit = 0; 
        for (int price : prices) { 
            minPrice = Math.min(minPrice, price); 
            maxProfit = Math.max(maxProfit, price - minPrice); 
        } 
        return maxProfit; 
    } 
} 
15. Single Number 
 
class Solution { 
    public int singleNumber(int[] nums) { 
        int result = 0; 
        for (int num : nums) result ^= num; 
        return result; 
    } 
} 
 
16. Majority Element 
 
class Solution { 
    public int majorityElement(int[] nums) { 
        int count = 0, candidate = 0; 
        for (int num : nums) { 
            if (count == 0) candidate = num; 
            count += (num == candidate) ? 1 : -1; 
        } 
        return candidate; 
    } 
} 
 
17. Move Zeroes 
 
class Solution { 
    public void moveZeroes(int[] nums) { 
        int pos = 0; 
        for (int num : nums) { 
            if (num != 0) nums[pos++] = num; 
        } 
        while (pos < nums.length) nums[pos++] = 0; 
    } 
} 
 
18. Contains Duplicate 
 
class Solution { 
    public boolean containsDuplicate(int[] nums) { 
        Set<Integer> set = new HashSet<>(); 
        for (int num : nums) { 
            if (!set.add(num)) return true; 
        } 
        return false; 
    } 
} 
 
19. Missing Number 
 
class Solution { 
    public int missingNumber(int[] nums) { 
        int n = nums.length; 
        int sum = n * (n + 1) / 2; 
        for (int num : nums) sum -= num; 
        return sum; 
    } 
} 
 
20. Valid Anagram 
 
class Solution { 
    public boolean isAnagram(String s, String t) { 
        if (s.length() != t.length()) return false; 
        int[] freq = new int[26]; 
        for (char c : s.toCharArray()) freq[c - 'a']++; 
        for (char c : t.toCharArray()) freq[c - 'a']--; 
        for (int f : freq) if (f != 0) return false; 
        return true; 
    } 
} 
 
*MEDIUM - 10 Problems* 
21. Add Two Numbers 
 
class Solution { 
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) { 
        ListNode dummy = new ListNode(0); 
        ListNode curr = dummy; 
        int carry = 0; 
        while (l1 != null || l2 != null || carry != 0) { 
            int sum = carry + (l1 != null ? l1.val : 0) + (l2 != null ? l2.val : 0); 
            carry = sum / 10; 
            curr.next = new ListNode(sum % 10); 
            curr = curr.next; 
            if (l1 != null) l1 = l1.next; 
            if (l2 != null) l2 = l2.next; 
        } 
        return dummy.next; 
    } 
} 
 
22. Longest Substring Without Repeating Characters 
 
class Solution { 
    public int lengthOfLongestSubstring(String s) { 
        Map<Character, Integer> map = new HashMap<>(); 
        int left = 0, max = 0; 
        for (int right = 0; right < s.length(); right++) { 
            char c = s.charAt(right); 
            if (map.containsKey(c)) left = Math.max(left, map.get(c) + 1); 
            map.put(c, right); 
            max = Math.max(max, right - left + 1); 
        } 
        return max; 
    } 
} 
 
23. 3Sum 
 
class Solution { 
    public List<List<Integer>> threeSum(int[] nums) { 
        Arrays.sort(nums); 
        List<List<Integer>> res = new ArrayList<>(); 
        for (int i = 0; i < nums.length - 2; i++) { 
            if (i > 0 && nums[i] == nums[i - 1]) continue; 
            int l = i + 1, r = nums.length - 1; 
            while (l < r) { 
                int sum = nums[i] + nums[l] + nums[r]; 
                if (sum == 0) { 
                    res.add(Arrays.asList(nums[i], nums[l], nums[r])); 
                    l++; r--; 
                    while (l < r && nums[l] == nums[l - 1]) l++; 
                } else if (sum < 0) l++; 
                else r--; 
            } 
        } 
        return res; 
    } 
} 
 
24. Container With Most Water 
 
class Solution { 
    public int maxArea(int[] height) { 
        int left = 0, right = height.length - 1, max = 0; 
        while (left < right) { 
            int area = Math.min(height[left], height[right]) * (right - left); 
            max = Math.max(max, area); 
            if (height[left] < height[right]) left++; 
            else right--; 
        } 
        return max; 
    } 
} 
 
25. Group Anagrams 
 
class Solution { 
    public List<List<String>> groupAnagrams(String[] strs) { 
        Map<String, List<String>> map = new HashMap<>(); 
        for (String s : strs) { 
            char[] chars = s.toCharArray(); 
            Arrays.sort(chars); 
            String key = new String(chars); 
            map.computeIfAbsent(key, k -> new ArrayList<>()).add(s); 
        } 
        return new ArrayList<>(map.values()); 
    } 
} 
 
26. Product of Array Except Self 
 
class Solution { 
    public int[] productExceptSelf(int[] nums) { 
        int n = nums.length; 
        int[] res = new int[n]; 
        res[0] = 1; 
        for (int i = 1; i < n; i++) res[i] = res[i - 1] * nums[i - 1]; 
        int right = 1; 
        for (int i = n - 1; i >= 0; i--) { 
            res[i] *= right; 
            right *= nums[i]; 
        } 
        return res; 
    } 
} 
 
27. Search in Rotated Sorted Array 
 
class Solution { 
    public int search(int[] nums, int target) { 
        int left = 0, right = nums.length - 1; 
        while (left <= right) { 
            int mid = left + (right - left) / 2; 
            if (nums[mid] == target) return mid; 
            if (nums[left] <= nums[mid]) { 
                if (target >= nums[left] && target < nums[mid]) right = mid - 1; 
                else left = mid + 1; 
            } else { 
                if (target > nums[mid] && target <= nums[right]) left = mid + 1; 
                else right = mid - 1; 
            } 
        } 
        return -1; 
    } 
} 
28. Find First and Last Position of Element in Sorted Array 
 
class Solution { 
    public int[] searchRange(int[] nums, int target) { 
        return new int[]{find(nums, target, true), find(nums, target, false)}; 
    } 
    private int find(int[] nums, int target, boolean first) { 
        int l = 0, r = nums.length - 1, ans = -1; 
        while (l <= r) { 
            int m = l + (r - l) / 2; 
            if (nums[m] == target) { 
                ans = m; 
                if (first) r = m - 1; else l = m + 1; 
            } else if (nums[m] < target) l = m + 1; 
            else r = m - 1; 
        } 
        return ans; 
    } 
} 
 
29. Combination Sum 
 
class Solution { 
    public List<List<Integer>> combinationSum(int[] candidates, int target) { 
        List<List<Integer>> result = new ArrayList<>(); 
        backtrack(candidates, 0, target, new ArrayList<>(), result); 
        return result; 
    } 
    private void backtrack(int[] c, int start, int target, List<Integer> curr, List<List<Integer>> 
res) { 
        if (target == 0) { 
            res.add(new ArrayList<>(curr)); 
            return; 
        } 
        for (int i = start; i < c.length; i++) { 
            if (c[i] <= target) { 
                curr.add(c[i]); 
                backtrack(c, i, target - c[i], curr, res); 
                curr.remove(curr.size() - 1); 
            } 
        } 
    } 
} 
 
30. Top K Frequent Elements 
 
class Solution { 
    public int[] topKFrequent(int[] nums, int k) { 
        Map<Integer, Integer> freq = new HashMap<>(); 
        for (int n : nums) freq.put(n, freq.getOrDefault(n, 0) + 1); 
        PriorityQueue<Map.Entry<Integer, Integer>> pq = new PriorityQueue<>((a,b) -> 
a.getValue() - b.getValue()); 
        for (var e : freq.entrySet()) { 
            pq.offer(e); 
            if (pq.size() > k) pq.poll(); 
        } 
        int[] res = new int[k]; 
        for (int i = 0; i < k; i++) res[i] = pq.poll().getKey(); 
        return res; 
    } 
} 
 
*HARD - 10 Problems* 
31. Median of Two Sorted Arrays 
 
class Solution { 
    public double findMedianSortedArrays(int[] nums1, int[] nums2) { 
        if (nums1.length > nums2.length) return findMedianSortedArrays(nums2, nums1); 
        int m = nums1.length, n = nums2.length, lo = 0, hi = m; 
        while (lo <= hi) { 
            int px = (lo + hi) / 2; 
            int py = (m + n + 1) / 2 - px; 
            int lx = px == 0 ? Integer.MIN_VALUE : nums1[px - 1]; 
            int rx = px == m ? Integer.MAX_VALUE : nums1[px]; 
            int ly = py == 0 ? Integer.MIN_VALUE : nums2[py - 1]; 
            int ry = py == n ? Integer.MAX_VALUE : nums2[py]; 
            if (lx <= ry && ly <= rx) { 
                if ((m + n) % 2 == 0) return (Math.max(lx, ly) + Math.min(rx, ry)) / 2.0; 
                else return Math.max(lx, ly); 
            } else if (lx > ry) hi = px - 1; 
            else lo = px + 1; 
        } 
        return 0; 
    } 
} 
32. Regular Expression Matching 
 
class Solution { 
    public boolean isMatch(String s, String p) { 
        int m = s.length(), n = p.length(); 
        boolean[][] dp = new boolean[m + 1][n + 1]; 
        dp[0][0] = true; 
        for (int j = 1; j <= n; j++) if (p.charAt(j - 1) == '*') dp[0][j] = dp[0][j - 2]; 
        for (int i = 1; i <= m; i++) { 
            for (int j = 1; j <= n; j++) { 
                if (p.charAt(j - 1) == '.' || p.charAt(j - 1) == s.charAt(i - 1)) dp[i][j] = dp[i - 1][j - 1]; 
                else if (p.charAt(j - 1) == '*') { 
                    dp[i][j] = dp[i][j - 2]; 
                    if (p.charAt(j - 2) == '.' || p.charAt(j - 2) == s.charAt(i - 1)) dp[i][j] = dp[i][j] || 
dp[i - 1][j]; 
                } 
            } 
        } 
        return dp[m][n]; 
    } 
} 
 
33. Merge k Sorted Lists 
 
class Solution { 
    public ListNode mergeKLists(ListNode[] lists) { 
        PriorityQueue<ListNode> pq = new PriorityQueue<>((a,b) -> a.val - b.val); 
        for (ListNode list : lists) if (list != null) pq.add(list); 
        ListNode dummy = new ListNode(0); 
        ListNode curr = dummy; 
        while (!pq.isEmpty()) { 
            ListNode node = pq.poll(); 
            curr.next = node; 
            curr = node; 
            if (node.next != null) pq.add(node.next); 
        } 
        return dummy.next; 
    } 
} 
 
34. Trapping Rain Water 
class Solution { 
    public int trap(int[] height) { 
        int left = 0, right = height.length - 1; 
        int leftMax = 0, rightMax = 0, water = 0; 
        while (left < right) { 
            if (height[left] < height[right]) { 
                if (height[left] >= leftMax) leftMax = height[left]; 
                else water += leftMax - height[left]; 
                left++; 
            } else { 
                if (height[right] >= rightMax) rightMax = height[right]; 
                else water += rightMax - height[right]; 
                right--; 
            } 
        } 
        return water; 
    } 
} 
 
35. N-Queens 
 
class Solution { 
    public List<List<String>> solveNQueens(int n) { 
        List<List<String>> result = new ArrayList<>(); 
        char[][] board = new char[n][n]; 
        for (char[] row : board) Arrays.fill(row, '.'); 
        solve(board, 0, result); 
        return result; 
    } 
    private void solve(char[][] board, int row, List<List<String>> res) { 
        if (row == board.length) { 
            List<String> list = new ArrayList<>(); 
            for (char[] r : board) list.add(new String(r)); 
            res.add(list); 
            return; 
        } 
        for (int col = 0; col < board.length; col++) { 
            if (isValid(board, row, col)) { 
                board[row][col] = 'Q'; 
                solve(board, row + 1, res); 
                board[row][col] = '.'; 
            } 
        } 
    } 
    private boolean isValid(char[][] b, int r, int c) { 
        for (int i = 0; i < r; i++) if (b[i][c] == 'Q') return false; 
        for (int i = r - 1, j = c - 1; i >= 0 && j >= 0; i--, j--) if (b[i][j] == 'Q') return false; 
        for (int i = r - 1, j = c + 1; i >= 0 && j < b.length; i--, j++) if (b[i][j] == 'Q') return false; 
        return true; 
    } 
} 
 
36. Word Ladder 
 
class Solution { 
    public int ladderLength(String beginWord, String endWord, List<String> wordList) { 
        Set<String> dict = new HashSet<>(wordList); 
        if (!dict.contains(endWord)) return 0; 
        Queue<String> queue = new LinkedList<>(); 
        queue.add(beginWord); 
        int steps = 1; 
        while (!queue.isEmpty()) { 
            int size = queue.size(); 
            for (int i = 0; i < size; i++) { 
                String word = queue.poll(); 
                if (word.equals(endWord)) return steps; 
                char[] chars = word.toCharArray(); 
                for (int j = 0; j < chars.length; j++) { 
                    char original = chars[j]; 
                    for (char c = 'a'; c <= 'z'; c++) { 
                        chars[j] = c; 
                        String next = new String(chars); 
                        if (dict.contains(next)) { 
                            dict.remove(next); 
                            queue.add(next); 
                        } 
                    } 
                    chars[j] = original; 
                } 
            } 
            steps++; 
        } 
        return 0; 
    } 
} 
 
37. Sudoku Solver 
 
class Solution { 
    public void solveSudoku(char[][] board) { 
        solve(board); 
    } 
    private boolean solve(char[][] board) { 
        for (int i = 0; i < 9; i++) { 
            for (int j = 0; j < 9; j++) { 
                if (board[i][j] == '.') { 
                    for (char c = '1'; c <= '9'; c++) { 
                        if (isValid(board, i, j, c)) { 
                            board[i][j] = c; 
                            if (solve(board)) return true; 
                            board[i][j] = '.'; 
                        } 
                    } 
                    return false; 
                } 
            } 
        } 
        return true; 
    } 
    private boolean isValid(char[][] b, int r, int c, char ch) { 
        for (int i = 0; i < 9; i++) { 
            if (b[r][i] == ch) return false; 
            if (b[i][c] == ch) return false; 
            if (b[3 * (r / 3) + i / 3][3 * (c / 3) + i % 3] == ch) return false; 
        } 
        return true; 
    } 
} 
 
38. Minimum Window Substring 
 
class Solution { 
    public String minWindow(String s, String t) { 
        Map<Character, Integer> map = new HashMap<>(); 
        for (char c : t.toCharArray()) map.put(c, map.getOrDefault(c, 0) + 1); 
        int left = 0, count = t.length(), minLen = Integer.MAX_VALUE, start = 0; 
        for (int right = 0; right < s.length(); right++) { 
            char c = s.charAt(right); 
            if (map.containsKey(c)) { 
                if (map.get(c) > 0) count--; 
                map.put(c, map.get(c) - 1); 
            } 
            while (count == 0) { 
                if (right - left + 1 < minLen) { 
                    minLen = right - left + 1; 
                    start = left; 
                } 
                char lc = s.charAt(left); 
                if (map.containsKey(lc)) { 
                    map.put(lc, map.get(lc) + 1); 
                    if (map.get(lc) > 0) count++; 
                } 
                left++; 
            } 
        } 
        return minLen == Integer.MAX_VALUE ? "" : s.substring(start, start + minLen); 
    } 
} 
 
39. Largest Rectangle in Histogram 
class Solution { 
    public int largestRectangleArea(int[] heights) { 
        Stack<Integer> stack = new Stack<>(); 
        int maxArea = 0; 
        for (int i = 0; i <= heights.length; i++) { 
            int currHeight = (i == heights.length) ? 0 : heights[i]; 
            while (!stack.isEmpty() && currHeight < heights[stack.peek()]) { 
                int height = heights[stack.pop()]; 
                int width = stack.isEmpty() ? i : i - stack.peek() - 1; 
                maxArea = Math.max(maxArea, height * width); 
            } 
            stack.push(i); 
        } 
        return maxArea; 
    } 
} 
40. Edit Distance 
class Solution { 
    public int minDistance(String word1, String word2) { 
        int m = word1.length(), n = word2.length(); 
        int[][] dp = new int[m + 1][n + 1]; 
        for (int i = 0; i <= m; i++) dp[i][0] = i; 
        for (int j = 0; j <= n; j++) dp[0][j] = j; 
        for (int i = 1; i <= m; i++) { 
            for (int j = 1; j <= n; j++) { 
                if (word1.charAt(i - 1) == word2.charAt(j - 1)) dp[i][j] = dp[i - 1][j - 1]; 
                else dp[i][j] = 1 + Math.min(dp[i - 1][j - 1], Math.min(dp[i - 1][j], dp[i][j - 1])); 
            } 
        } 
        return dp[m][n]; 
    } 
} 
 
Submission Proof 
 



 
