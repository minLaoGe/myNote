# myNote  this is a web file made by me. 

# this is algorithm

## 1 无重复字符的最长字符串

```java
  class Solution {


    public int lengthOfLongestSubstring(String s) {
        int n = s.length(), ans = 0;
        Map<Character, Integer> map = new HashMap<>();
        for (int end = 0, start = 0; end < n; end++) {
            char alpha = s.charAt(end);
            if (map.containsKey(alpha)) {
                //为什么我们需要加入这段   因为有可能 在  abba 情况下，会有 start > map.get(alpha)情况。
                start = Math.max(map.get(alpha),start);
            }
            ans = Math.max(ans, end - start + 1);
            map.put(s.charAt(end), end + 1);
        }
        return ans;
    }
}


```