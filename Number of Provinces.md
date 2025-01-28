## Number of Provinces



# Given an undirected graph with V vertices. We say two vertices u and v belong to a single province if there is a path from u to v or v to u. Your task is to find the number of provinces.

Note: A province is a group of directly or indirectly connected cities and no other cities outside of the group.


# Example 1:

Input:
[
 [1, 0, 1],
 [0, 1, 0],
 [1, 0, 1]
]

Output:
2
Explanation:
The graph clearly has 2 Provinces [1,3] and [2]. As city 1 and city 3 has a path between them they belong to a single province. City 2 has no path to city 1 or city 3 hence it belongs to another province.

``` java

class Solution {
    static int numProvinces(ArrayList<ArrayList<Integer>> adj, int V)
    {
        boolean visited[]=new boolean[V+1];
        ArrayList<ArrayList<Integer>> ad=new ArrayList<ArrayList<Integer>>();
        for (int i = 0; i < V; i++) {
            ad.add(new ArrayList<>());
        }
        for(int i=0;i<V;i++)
        {
            for(int j=0;j<V;j++)
            {
                if(adj.get(i).get(j)==1 && i!=j)
                {
                    int u=i;
                    int v=j;
                    ad.get(u).add(v);
                    ad.get(v).add(u);
                }
            }
        }
        // boolean visited[]=new boolean[V+1];
        int ans=0;
        for(int i=0;i<V;i++)
        {
            if(!visited[i])
            {
                ans++;
                dfs(i,visited,ad);
            }
        }
        return ans;
    }
    public static void dfs(int node,boolean visited[],ArrayList<ArrayList<Integer>> ad)
    {
        visited[node]=true;
        for(int x:ad.get(node))
        {
            if(!visited[x])
            {
                dfs(x,visited,ad);
            }
        }
    }
};
