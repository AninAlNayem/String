# String
### Rabin Karp's rolling hash method to find longest palindromic prefix
#### Shortest Palindrome
##### Description
You are given a string S. You can add some characters at the begining of the string. Your task is to create shortest palindrome by adding some (possibly none) characters at the begining of S.

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
      ph=(ph*p+(str[i]-'a'+1))%mod; // Calculating hash from i to 0.  let s="abc", i=0 => ph=a , i=1 => ph=(a*p)+b , i=2 => ph=((a*p)+b)*p+c= a*p^2+b*p^1+c*p^0.
      sh=(sh+((str[i]-'a'+1)*p_pow)%mod)%mod; // Calcuating hash from 0 to i; ph= a*p^0+b*p^1+c*p^2
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
