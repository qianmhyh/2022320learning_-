```cpp
#include<bits/stdc++.h>
using namespace std;

#define MAXN 100005

struct p{
	int to,l;
};

vector <int> p[MAXN]; 
int n,m,start,fin,ans[MAXN];

void solve(int u,int v)
{
	if(ans[u]!=0) return; 
	
	ans[u]=v;
	
	for(int j=0;j<p[u].size();j++)//n 为点数
	{
		solve(p[u][j],v);
	} 
}

int main()
{
	cin>>n>>m;
	for(int i=1;i<=m;i++)
	{
		cin>>start>>fin;//start 起点  fin 终点 
		p[fin].push_back(start);//反向构图 
	}
	
	for(int i=n;i>=1;i--)
	{
		solve(i,i);
	}
	
	for(int i=1;i<=n;i++)
	{
		cout<<ans[i]<<' ';
	}
	return 0;
}
```
