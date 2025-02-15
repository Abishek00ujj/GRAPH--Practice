## BFS of graph


# Given a undirected graph represented by an adjacency list adj, which is a vector of vectors where each adj[i] represents the list of vertices connected to vertex i. Perform a Breadth First Traversal (BFS) starting from vertex 0, visiting vertices from left to right according to the adjacency list, and return a list containing the BFS traversal of the graph.

Note: Do traverse in the same order as they are in the adjacency list.

Examples:


# Input: adj = [[2,3,1], [0], [0,4], [0], [2]]
![image](https://github.com/user-attachments/assets/47182bfb-b07d-4f40-8ab7-b7c17843f514)

Output: [0, 2, 3, 1, 4]
Explanation: Starting from 0, the BFS traversal will follow these steps: 
Visit 0 → Output: 0 
Visit 2 (first neighbor of 0) → Output: 0, 2 
Visit 3 (next neighbor of 0) → Output: 0, 2, 3 
Visit 1 (next neighbor of 0) → Output: 0, 2, 3, 
Visit 4 (neighbor of 2) → Final Output: 0, 2, 3, 1, 4


``` java
 class Solution {
    // Function to return Breadth First Traversal of given graph.
    public ArrayList<Integer> bfsOfGraph(int V, ArrayList<ArrayList<Integer>> adj) {
        // code here
        
    Queue<Integer> queue=new LinkedList<Integer>();
    ArrayList<Integer> answer=new ArrayList<Integer>();
    boolean visited[]=new boolean[V];
    queue.add(0);
    visited[0]=true;
       while(!queue.isEmpty())
       {
           int node=queue.poll();
           visited[node]=true;
           answer.add(node);
           
           for(int x:adj.get(node))
           {
               if(!visited[x])
               {
                   visited[x]=true;
                   queue.add(x);
               }
           }
       }
       return answer;
    }
}


```
