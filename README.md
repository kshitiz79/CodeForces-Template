# CodeForces-Template


/*
    Author : Young Lord
*/

#include <bits/stdc++.h>
using namespace std;

using ll = long long;
using pii = pair<int,int>;
using pll = pair<ll,ll>;
using vi = vector<int>;
using vll = vector<ll>;

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    int T;
    cin >> T;
    while (T--) {
        // solve
    }

    return 0;
}



# Fast input for large arrays


vi read_ints(int n){
    vi a(n);
    for(int &x : a) cin >> x;
    return a;
}



# Prefix Sum

vll prefix_sum(const vi &a){
    int n = a.size();
    vll p(n+1,0);
    for(int i=0;i<n;i++) p[i+1]=p[i]+a[i];
    return p;
}




 # GCD / LCM
 
ll lcm(ll a,ll b){
    return a/gcd(a,b)*b;
}




# DSU (Disjoint Set Union)

struct DSU {
    vi p, sz;
    DSU(int n): p(n), sz(n,1) {
        iota(p.begin(), p.end(), 0);
    }
    int find(int x){
        if(p[x]==x) return x;
        return p[x]=find(p[x]);
    }
    bool unite(int a,int b){
        a=find(a); b=find(b);
        if(a==b) return false;
        if(sz[a]<sz[b]) swap(a,b);
        p[b]=a; sz[a]+=sz[b];
        return true;
    }
};





# BFS / DFS

void bfs(int src, vector<vi>& g, vi& dist){
    queue<int> q;
    dist[src]=0;
    q.push(src);
    while(!q.empty()){
        int u=q.front(); q.pop();
        for(int v:g[u]){
            if(dist[v]==-1){
                dist[v]=dist[u]+1;
                q.push(v);
            }
        }
    }
}



# Binary Search Pattern

int l=0,r=1e9,ans=-1;
while(l<=r){
    int m=(l+r)/2;
    if(check(m)){
        ans=m;
        r=m-1;
    }else l=m+1;
}



# Mod operations


const ll MOD = 1e9+7;

ll modpow(ll a,ll b){
    ll r=1;
    while(b){
        if(b&1) r=r*a%MOD;
        a=a*a%MOD;
        b>>=1;
    }
    return r;
}















