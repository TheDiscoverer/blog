## 不同路径 II

- 题目链接：https://leetcode-cn.com/problems/unique-paths-ii/
- Tag：动态规划

## 题目描述
一个机器人位于一个 m x n 网格的左上角 （起始点在下图中标记为“Start” ）。 机器人每次只能向下或者向右移动一步。机器人试图达到网格的右下角（在下图中标记为“Finish”）。 现在考虑网格中有障碍物。那么从左上角到右下角将会有多少条不同的路径？ 网格中的障碍物和空位置分别用 1 和 0 来表示。说明：m 和 n 的值均不超过 100。

## 解法
dp[i][j] = dp[i][j] ==1 ? 0 : dp[i - 1][j] + dp[i][j - 1]

但是对于第一行和第一列需要预先初始化，初始化也需要考虑当前点是否为障碍点。
```
class Solution {
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        int len1 = obstacleGrid.length, len2 = obstacleGrid[0].length;
        obstacleGrid[0][0] = obstacleGrid[0][0] == 1 ? 0 : 1;
        for(int i = 1; i < len2; i++) 
            obstacleGrid[0][i] = (obstacleGrid[0][i - 1] == 1 && obstacleGrid[0][i] == 0) ? 1 : 0;
        for(int i = 1; i < len1; i++)
            obstacleGrid[i][0] = (obstacleGrid[i][0] == 0 && obstacleGrid[i - 1][0] == 1) ? 1 : 0;
        for(int i = 1; i < len1; i++) {
            for(int j = 1; j < len2; j++) {
                if(obstacleGrid[i][j] == 1)
                    obstacleGrid[i][j] = 0;
                else {
                    obstacleGrid[i][j] = obstacleGrid[i-1][j] + obstacleGrid[i][j-1];
                }
            }
        }
        return obstacleGrid[len1 - 1][len2 - 1];
    }
}
```