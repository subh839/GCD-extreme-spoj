# GCD-extreme-spoj

#include<bits/stdc++.h>
#define RE(i,n) for (int i = 1; i <= n; i++)
 
using namespace std;
lli phi[1000001];
lli sum[1000001];
lli   f[1000001];
void init(int N)
{
	RE(i , N) phi[i] = i;
 
	for(int i=2;i<=N;i++)
	if(phi[i] == i)
	{
		for(int j=i;j<=N;j+=i)
		phi[j] /= i , phi[j] *= (i - 1);
	}
 
	for(int i=1;i<=N;i++)
	{
		for(int j=i;j<=N;j+=i)
		{
			f[j] += (i * phi[j/i]);
		}
	}
 
	RE(i , N)
	sum[i] = sum[i-1] + f[i] - i;
 
}
 
int main()
{
	init(1000000);
	int N;
 
	while(1)
	{
		cin>>N;
		if(N == 0) break;
 
		cout<<sum[N]<<endl;
	}
}
