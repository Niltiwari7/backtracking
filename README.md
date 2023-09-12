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


