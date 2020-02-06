# sixninemax
给你一个仅由数字 6 和 9 组成的正整数 num。

你最多只能翻转一位数字，将 6 变成 9，或者把 9 变成 6 。

请返回你可以得到的最大数字。

 

示例 1：

输入：num = 9669
输出：9969
解释：
改变第一位数字可以得到 6669 。
改变第二位数字可以得到 9969 。
改变第三位数字可以得到 9699 。
改变第四位数字可以得到 9666 。
其中最大的数字是 9969 。

示例 2：

输入：num = 9996
输出：9999
解释：将最后一位从 6 变到 9，其结果 9999 是最大的数。

示例 3：

输入：num = 9999
输出：9999
解释：无需改变就已经是最大的数字了。

 

提示：

    1 <= num <= 10^4
    num 每一位上的数字都是 6 或者 9 。

class Solution {
public:
    int fun(vector<int> &v)
    {
        int num=0;
        int x = 1;
        for(int j = 0;j<v.size();j++)
        {
            num += v[j]*x;
            x = x*10;
        }
        return num;
    }
    int maximum69Number (int num) {
        int res = num;
        vector<int> v;
        while(res>0)
        {
            v.push_back(res%10);//9 6 6 9
            res = res/10;
        }
        for(int i =0 ;i<v.size();i++)
        {
            cout<<v[i]<<endl;
        }
        int max_num = num;
        vector<int> tmp;
        int flag=0;
        for(int i = v.size()-1;i>=0;i--)
        {
            tmp.assign(v.begin(),v.end());
            if(tmp[i] == 6)
            {
                flag = 1;
                tmp[i] = 9;
            }
            int ans = fun(tmp);
            cout<<ans<<endl;
            max_num = max(max_num ,ans);
            if(flag ==1)
            {
                break;
            }
        }

        return max_num;
        
    }
};

