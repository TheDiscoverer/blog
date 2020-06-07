## 复原IP地址

- 题目链接：
- Tag：

## 题目描述
给定一个只包含数字的字符串，复原它并返回所有可能的 IP 地址格式。有效的 IP 地址正好由四个整数（每个整数位于 0 到 255 之间组成），整数之间用 '.' 分隔。
示例:
```
输入: "25525511135"
输出: ["255.255.11.135", "255.255.111.35"]
```
## 解法
深搜方法.定义dfs方法获取第num段字符串。首先判断num是否 <=4, 判断字符串是否合法（0 - 255），将子段插入到list中

如果 num == 4，分两种情况
- 后序没有字符串了，说明结束，转化成IP地址。
- 后序还有字符串，说明错了。

如果num  < 4，那么递归获取第 num + 1 段。

移除list最后元素。

```
class Solution {
    List<Integer> list  = new LinkedList<>();
    List<String> rt = new LinkedList<>();
    public List<String> restoreIpAddresses(String s) {
        if(s == null || s.length() < 4) 
            return rt;
        for(int i = 1; i <= 3; i++) {
            dfs(s, 0, i, 1);
        }
        return rt;
    }
    public void dfs(String str, int s, int e, int num) {
        if(num >= 5)
            return;
        int curr = Integer.parseInt(str.substring(s, e));
        if(curr <= 255 && curr >= 0 && (curr + "").length() == e - s) 
            list.add(curr);
        else
            return;
        if(num == 4 && e == str.length()) {
            process();
            list.remove(num - 1);
            return;
        }
        for(int i = e + 1; i <= e + 3 && i <= str.length(); i++)
            dfs(str, e, i, num + 1);
        list.remove(num - 1);
    }
    public void process() {
        StringBuilder sb = new StringBuilder();
        for(int i = 0; i < 4; i++) {
            sb.append(list.get(i)+".");
        }
        rt.add(sb.toString().substring(0, sb.length() - 1));
    }
}
```