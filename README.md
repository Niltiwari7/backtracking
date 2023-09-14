# backtracking

### Generate all substring 

```
#include<iostream>
#include<string>
using namespace std;

void solve(int i,string s,string move)
{
    if(i==s.size()){// if condition true
        cout<<move<<endl;
        return;
    }
    move+=s[i];// do operation what ever question asking
    solve(i+1,s,move);//recursion call
    move.pop_back();//backtraking
   
     solve(i+1,s,move);//recursion call
}
int main(){
    string s;
    cin>>s;
    solve(0,s,"");
}
```
### Generate all subarray
```
#include<iostream>
#include<string>
#include<vector>
using namespace std;

void solve(int i,int n,int *arr,vector<int>ans)
{
    if(i==n){
        for(auto it:ans){
            cout<<it<<" ";
        }
        cout<<endl;
        return ;
    }
    ans.push_back(arr[i]);
    solve(i+1,n,arr,ans);
    ans.pop_back();
    solve(i+1,n,arr,ans);
}
int main(){
   int n;
   cin>>n;
   int arr[n];
   for(int i=0;i<n;i++)cin>>arr[i];
   vector<int>ans;
   solve(0,n,arr,ans);
}
```
### Generate all valid parenthesis

```
class Solution {
public:
    vector<string>res;
    void help(string s,int n,int l,int r)
    {
        if(l<r||l>n||r>n)
        {
            return;
        }
        if(l==n && r==n)res.push_back(s);
        help(s+'(',n,l+1,r);
        help(s+')',n,l,r+1);
    }
    vector<string> generateParenthesis(int n) {
       help("",n,0,0);
       return res;  
    }
};
```
### Combination sum
```
class Solution {
public:
    void solve(vector<int>&arr,int target,vector<int>ds,vector<vector<int>>&ans,int i)
    {
        if(i==arr.size())
        {
            if(target==0)
            {
                ans.push_back(ds);
            }
            return;
        }
        if(arr[i]<=target)
        {
            ds.push_back(arr[i]);
            solve(arr,target-arr[i],ds,ans,i);
            ds.pop_back();
        }
        solve(arr,target,ds,ans,i+1);

    }
    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
       vector<int>ds;
       vector<vector<int>>ans;
      solve(candidates,target,ds,ans,0);
       return ans; 
    }
};
```
#### Combination sum
```
#

class Solution {
public:
    void solve(vector<int>& arr, int target, vector<int>& ds, vector<std::vector<int>>& ans, int i) {
        if (target == 0) {
            ans.push_back(ds);
            return;
        }

        for (int j = i; j < arr.size(); j++) {
            if (j > i && arr[j] == arr[j - 1]) continue;
            if (arr[j] <= target) {
                ds.push_back(arr[j]);
                solve(arr, target - arr[j], ds, ans, j + 1);
                ds.pop_back();
            }
        }
    }

    vector<vector<int>> combinationSum2(vector<int>& candidates, int target) {
        vector<int> ds;
        vector<vector<int>> ans;
        // Sort the candidates to handle duplicates properly
        sort(candidates.begin(), candidates.end());
        solve(candidates, target, ds, ans, 0);
        return ans;
    }
};
```
#### Subset sum-1
```
void solve(vector<int>nums,int i,vector<int>&ans,vector<int>ds)
{
	if(i==nums.size())
	{
		int sum=accumulate(ds.begin(),ds.end(),0);
        ans.push_back(sum);
		return;
	}
	ds.push_back(nums[i]);
	solve(nums, i+1, ans, ds);
	ds.pop_back();
	solve(nums, i+1, ans, ds);
}
vector<int> subsetSum(vector<int> &num){
	// Write your code here.	
	vector<int>ans;
	vector<int>ds;
	solve(num,0,ans,ds);
	sort(ans.begin(),ans.end());
	
	return ans;
}
```
#### Subset sum-2
```
class Solution {
public:
    void solve(vector<int>nums,vector<int>ds,vector<vector<int>>&ans,int i)
    {
       
        ans.push_back(ds);
       for(int j=i;j<nums.size();j++){
           if(j>i && nums[j]==nums[j-1])continue;
           ds.push_back(nums[j]);
           solve(nums,ds,ans,j+1);
           ds.pop_back();
       }
    }
    vector<vector<int>> subsetsWithDup(vector<int>& nums) {
        vector<int>ds;
        sort(nums.begin(),nums.end());
        vector<vector<int>>ans;
        solve(nums,ds,ans,0);
     
        return ans;
    }
};
```

