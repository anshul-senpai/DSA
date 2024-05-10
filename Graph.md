# It contains all the standard Graph based problems.

## Traversal Techniques

### BFS on directed/undirected Graph

#### BFS from 0 to its connected nodes.

```c++
vector<int> bfsOfGraph(int V, vector<int> adj[]) {
        
    vector<int>ans;
    vector<int>vis(V,-1);
    queue<int>q;

    q.push(0);
    ans.push_back(0);
    vis[0] = 1;
    while(!q.empty()){
        int x = q.size();
        
        for(int j=0;j<x;j++){
            int nodeVal = q.front();
            q.pop();
            
            for(int x:adj[nodeVal]){
                if(vis[x]==-1){
                    q.push(x);
                    ans.push_back(x);
                    vis[x] = 1;
                }
            }
        }
    }

    return ans;
}
```

#### BFS from 0 to all the nodes (disconnected also).

```c++
vector<int> bfsOfGraph(int V, vector<int> adj[]) {
        
    vector<int>ans;
    vector<int>vis(V,-1);
    queue<int>q;
    
    for(int i=0;i<V;i++){
        if(vis[i]==-1){
        q.push(0);
        ans.push_back(0);
        vis[0] = 1;
        while(!q.empty()){
            int x = q.size();
            
            for(int j=0;j<x;j++){
                int nodeVal = q.front();
                q.pop();
                
                for(int x:adj[nodeVal]){
                    if(vis[x]==-1){
                        q.push(x);
                        ans.push_back(x);
                        vis[x] = 1;
                    }
                }
            }
        }
        }
    }
    
    return ans;
}
```