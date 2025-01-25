## Connected Components in an Undirected Graph


# Given an undirected graph edges, the objective is to return a list of all connected components. Each connected component should be represented as a list of its vertices, with all components returned in a collection where each component is listed separately.

Examples :

Input: e=3, v=5, edges = [{0, 1},{2, 1},{3, 4}]
Output: [[0, 1, 2],[3, 4]]
Explanation: 

# ![image](https://github.com/user-attachments/assets/88a9b5c4-b0ce-47fe-a610-f8a61ce774af)
Example 2:

Input: e=5, v=7, edges=[{0, 1},{6, 1},{2, 4},{2, 3},{3, 4}]
Output: [[0, 1, 6],[2, 3, 4],[5]]
Constraints:
0 <= edges[i][0], edges[i][1] < v
1 ≤ v, e ≤ 105

``` java

class Solution
{
    public ArrayList<ArrayList<Integer>> connectedcomponents(int v, int[][] edges)
    {
        ArrayList<ArrayList<Integer>> ans=new ArrayList<>();
        for(int i=0;i<v;i++)
        {
            ans.add(new ArrayList<Integer>());
        }
        for(int i=0;i<edges.length;i++)
        {
            int u=edges[i][0];
            int V=edges[i][1];
            ans.get(u).add(V);
            ans.get(V).add(u);
        }
        int visited[]=new int[v];
        Arrays.fill(visited,0);
        ArrayList<ArrayList<Integer>> ans1=new ArrayList<>();
        for(int i=0;i<v;i++)
        {
            if(visited[i]==0)
            {
                ArrayList<Integer> x=new ArrayList<>();
                traversal(i,ans,x,visited);
                Collections.sort(x);
                ans1.add(x);
            }
        }
        return ans1;
    }
    public void traversal(int node,ArrayList<ArrayList<Integer>> ans,ArrayList<Integer> x,int visited[])
    {
        visited[node]=1;
        x.add(node);
        for(int m:ans.get(node))
        {
            if(visited[m]==0)
            {
                traversal(m,ans,x,visited);
            }
        }
    }
}

