# String
### Rabin Karp's rolling hash method to find longest palindromic prefix
#### Shortest Palindrome
```cpp
#include <bits/stdc++.h>
#define ll long long
using namespace std;

ll p=31;
ll mod=1e9+7;
ll ph=0,sh=0,p_pow=1;

int main() {
    
   string str;cin>>str;
   ll len=str.length();
   
   ll maxPos=0;

   for(ll i=0;i<len;i++){
      ph=(ph*p+(str[i]-'a'+1))%mod;
      sh=(sh+((str[i]-'a'+1)*p_pow)%mod)%mod;
      if(ph==sh){
        maxPos=i;
      }
      p_pow=(p_pow*p)%mod;
    }
    for(ll i=len-1;i>maxPos;i--){
        cout<<str[i];
    }
    for(ll i=0;i<len;i++){
        cout<<str[i];
    }cout<<"\n";

return 0;
}

```
