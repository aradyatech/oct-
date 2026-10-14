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
class Solution {
public:
    int minInsertions(string s) {
        int open = 0;
        int insertions = 0;

        for (int i = 0; i < s.size(); i++) {
            if (s[i] == '(') {
                open++;
            } else {
                if (i + 1 < s.size() && s[i + 1] == ')') {
                    i++;
                } else {
                    insertions++;
                }

                if (open > 0) {
                    open--;
                } else {
                    insertions++;
                }
            }
        }

        return insertions + 2 * open;
    }
};
class Solution {
public:
    int sumOfSquares(vector<int>& nums) {
        int n = nums.size();
        int sum = 0;

        for (int i = 1; i <= n; i++) {
            if (n % i == 0) {
                sum += nums[i - 1] * nums[i - 1];
            }
        }

        return sum;
    }
};
        }

        // Valid parentheses string must end with balance 0
        return dp[m - 1][n - 1][0];
    }
};

class Solution {
public:
    long long maxAlternatingSum(vector<int>& nums) {
        sort(nums.begin(), nums.end(),
             [](int a, int b) {
                 return 1LL * a * a > 1LL * b * b;
             });

        long long ans = 0;
        int n = nums.size();

        for (int i = 0; i < n; i++) {
            long long sq = 1LL * nums[i] * nums[i];

            if (i < (n + 1) / 2) {
                ans += sq;
            } else {
                ans -= sq;
            }
        }

        return ans;
    }
};

class Solution {
public:
    string maxSumOfSquares(int num, int sum) {
        if (sum > 9 * num) return "";
        
        string ans = "";
        
        for (int i = 0; i < num; i++) {
            int digit = min(9, sum);
            ans += char('0' + digit);
            sum -= digit;
        }
        
        if (sum != 0) return "";
        
        return ans;
    }
};
