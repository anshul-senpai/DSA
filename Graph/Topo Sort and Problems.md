# Topo Sort

```c++
class Solution
{
	public:
	void dfs(int i,vector<int>&vis,stack<int>&s,vector<int>adj[]){
	    vis[i] = 1;
	    
	    for(int x:adj[i]){
	        if(vis[x]==0){
	            dfs(x,vis,s,adj);
	        }
	    }
	    
	    s.push(i);
	}
	
	
	vector<int> topoSort(int V, vector<int> adj[]) 
	{
	    vector<int>vis(V,0);
	    vector<int>ans;
	    stack<int>s;
	  
	    for(int i=0;i<V;i++){
	        if(vis[i]==0){
                dfs(i,vis,s,adj);
	        }
	    }
	    
	    while(!s.empty()){
	        ans.push_back(s.top());
	        s.pop();
	    }
	    
	    return ans;
	}
};
```

- `Time Complexity:` `O(V+E)+O(V)`, where V = no. of nodes and E = no. of edges. There can be at most V components. So, another O(V) time complexity.

- `Space Complexity:` `O(2N) + O(N) ~ O(2N): O(2N)` for the visited array and the stack carried during DFS calls and O(N) for recursive stack space, where N = no. of nodes.