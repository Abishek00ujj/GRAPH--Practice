## DFS of Graph

# Given a connected undirected graph represented by an adjacency list adj, which is a vector of vectors where each adj[i] represents the list of vertices connected to vertex i. Perform a Depth First Traversal (DFS) starting from vertex 0, visiting vertices from left to right as per the adjacency list, and return a list containing the DFS traversal of the graph.

Note: Do traverse in the same order as they are in the adjacency list.

Examples:

Input: adj = [[2,3,1], [0], [0,4], [0], [2]]

![image](https://github.com/user-attachments/assets/2987bbd7-decc-4a2d-a1df-4c84c25723f0)


# Output: [0, 2, 4, 3, 1]
Explanation: Starting from 0, the DFS traversal proceeds as follows: 
Visit 0 → Output: 0 
Visit 2 (the first neighbor of 0) → Output: 0, 2 
Visit 4 (the first neighbor of 2) → Output: 0, 2, 4 
Backtrack to 2, then backtrack to 0, and visit 3 → Output: 0, 2, 4, 3 
Finally, backtrack to 0 and visit 1 → Final Output: 0, 2, 4, 3, 1


``` java

class Solution {
    // Function to return a list containing the DFS traversal of the graph.
    public ArrayList<Integer> dfsOfGraph(ArrayList<ArrayList<Integer>> adj) {
        
        
        ArrayList<Integer> answer=new ArrayList<>();
        boolean visited[]=new boolean[adj.size()];
        Arrays.fill(visited,false);
        visited[0]=true;
        // answer.add(0);
        dfs(0,answer,adj,visited);
        return answer;
    }
    public void dfs(int node,ArrayList<Integer> answer,ArrayList<ArrayList<Integer>> adj,boolean visited[])
    {
        visited[node]=true;
        answer.add(node);
        for(int x:adj.get(node))
        {
            if(!visited[x])
            {
                dfs(x,answer,adj,visited);
            }
        }
    }
}

