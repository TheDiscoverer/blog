## 

- 题目链接：https://leetcode-cn.com/problems/zigzag-conversion/
- Tag：字符串

## 题目描述
将一个给定字符串根据给定的行数，以从上往下、从左到右进行 Z 字形排列。

比如输入字符串为 "LEETCODEISHIRING" 行数为 3 时，排列如下：
```
L   C   I   R
E T O E S I I G
E   D   H   N
```

之后，你的输出需要从左往右逐行读取，产生出一个新的字符串，比如："LCIRETOESIIGEDHN"。

请你实现这个将字符串进行指定行数变换的函数：
```
string convert(string s, int numRows);
```
示例 1:

输入: s = "LEETCODEISHIRING", numRows = 3

输出: "LCIRETOESIIGEDHN"


## 解法
一开始把题目看错了，以为把那个图形打印出来。构建numRows个StringBuffer，然后来回遍历append字符。
```
class Solution {
    public String convert(String s, int numRows) {
        if(numRows == 1)
            return s;
        boolean isGoDown = false;
        int index = 0;
        List<StringBuffer> list = new ArrayList<>();
        for(int i = 0; i < numRows; i++) {
            list.add(new StringBuffer());
        }
        for(char ch : s.toCharArray()) {
            if(index == 0 || index == numRows - 1) {
                isGoDown = !isGoDown;
            }
            list.get(index).append(ch);
            index += isGoDown ? 1 : -1;
        }
        StringBuffer sb = new StringBuffer();
        for(int i = 0; i < list.size(); i++) {
            sb.append(list.get(i));
        }
        return sb.toString();
    }
}

```