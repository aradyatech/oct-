# oct-
class Solution {
public:
    bool hasValidPath(vector<vector<char>>& grid) {
        int m = grid.size();
        int n = grid[0].size();

        // Total number of characters must be even
        if ((m + n - 1) % 2 != 0)
            return false;

        // dp[i][j][balance]
        vector<vector<vector<bool>>> dp(
            m, vector<vector<bool>>(n, vector<bool>(m + n, false))
        );

        // Starting cell
        int startBalance = (grid[0][0] == '(') ? 1 : -1;

        if (startBalance < 0)
            return false;

        dp[0][0][startBalance] = true;

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {

                if (i == 0 && j == 0)
                    continue;

                for (int balance = 0; balance <= m + n; balance++) {

                    if (grid[i][j] == '(') {

                        // Come from top
                        if (i > 0 && balance > 0 &&
                            dp[i - 1][j][balance - 1]) {
                            dp[i][j][balance] = true;
                        }

                        // Come from left
                        if (j > 0 && balance > 0 &&
                            dp[i][j - 1][balance - 1]) {
                            dp[i][j][balance] = true;
                        }

                    } else {

                        // Current char is ')'
                        // Previous balance must be balance + 1

                        if (i > 0 &&
                            dp[i - 1][j][balance + 1]) {
                            dp[i][j][balance] = true;
                        }

                        if (j > 0 &&
                            dp[i][j - 1][balance + 1]) {
                            dp[i][j][balance] = true;
                        }
                    }
                }
            }
            class Solution {
public:
    vector<int> maxDepthAfterSplit(string seq) {
        vector<int> ans;
        int depth = 0;

        for (char c : seq) {
            if (c == '(') {
                depth++;
                ans.push_back(depth % 2);
            } 
            else {
                ans.push_back(depth % 2);
                depth--;
            }
        }

        return ans;
    }
};
        }

        // Valid parentheses string must end with balance 0
        return dp[m - 1][n - 1][0];
    }
};
