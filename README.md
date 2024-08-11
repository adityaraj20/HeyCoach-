
Approach 1: Depth-First Search (DFS)
DFS is a suitable approach for this problem as it explores all possible paths until it finds the exit or reaches a dead end.   

- Create a visited array to keep track of visited cells.
- Define a recursive function to explore neighbors:
* If the current position is out of bounds, a wall, or already visited, return False.
* If the current position is the exit, return True.
* Mark the current position as visited.
* Recursively explore the four neighbors.
* If any neighbor returns True, return True.
* Backtrack by unmarking the current position.
- Call the recursive function with the starting position.

def is_path_exists(grid, start, end):
    m, n = len(grid), len(grid[0])
    
    def dfs(x, y):
        if x == end[0] and y == end[1]:
            return True
        if x < 0 or x >= m or y < 0 or y >= n or grid[x][y] == 1:
            return False
        
        grid[x][y] = 2  
        
        return dfs(x + 1, y) or dfs(x - 1, y) or dfs(x, y + 1) or dfs(x, y - 1)
    
    return dfs(start[0], start[1])
   
Time Complexity: O(m * n) in the worst case, where m and n are the dimensions of the grid.
Space Complexity: O(m * n) in the worst case for the recursion stack

Approach 2: Breadth-First Search (BFS)
BFS can also be used, but DFS is generally preferred for maze-like problems due to its potential to find the shortest path faster.

Modified Problem
A possible modification is to find the shortest path from start to exit. This can be achieved by using BFS and keeping track of the distance from the starting point for each visited cell.
