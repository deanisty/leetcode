#### 题目

给定一个字符串，请你找出其中不含有重复字符的 最长子串 的长度。

示例 1:

输入: "abcabcbb"
输出: 3 
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
示例 2:

输入: "bbbbb"
输出: 1
解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。
示例 3:

输入: "pwwkew"
输出: 3
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
     请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。
     
     
     
#### 解答

```C
#include <stdio.h>
#include <stdlib.h>


int lengthOfLongestSubstring(char* s)
{
    int i, j, start, length;
    j = start = 0;
    length = 1;

    do {
        for(i = start; i < j; i ++)
        {
            if(s[i] == s[j]) {
                if(j - i > length) {
                    length = j - i;
                }
                start ++;
                break;
            }
        }
        j++;
    }while(s[j]);

    return length;
}


void main()
{
    char *s = "testlongeststr";
    int length = lengthOfLongestSubstring(s);
    printf("%d\n", length);
}
```
