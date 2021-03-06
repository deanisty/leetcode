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
#include <string.h>

int findCharIndex(char *s, int start, int end, char c);
/***
 * 思路：使用指针 i,j 设置滑动窗口
 * [i,j) 半开区间为窗口内容
 * j 递增过程中检测 s[j] 处的字符是否和区间中字符重复（如果重复假设为 k）
 * 如果是则移动 i 至 k 的下一个位置
 * 并且递增过程计算 j - i 作为最大的唯一子串长度
 */
int lengthOfLongestSubstring(char* s)
{
    int i, j, k, length = 0;
    int slen = strlen(s);
    // 空字符 或者 长度为1 的字符串 特殊处理
    if(slen <= 1) {
        return slen;
    }

    for(i = 0, j = 0; j < slen; j ++ )
    {
        k = findCharIndex(s, i, j, s[j]);
        if(k >= 0) {
            i = k + 1;
        }
        if(length < j - i + 1)
            length = j - i + 1;
    }

    return length;
}

int findCharIndex(char *s, int start, int end, char c)
{
    int i;
    // 窗口大小为0不处理
    if(start == end) {
        return -1;
    }

    // [start, end)
    for(i = start; i <= end - 1; i++) {
        if(s[i] == c) {
            return i;
        }
    }

    return -1;
}

void main()
{
    char *s = "ab";
    int length = lengthOfLongestSubstring(s);
    printf("%d\n", length);
}
```
