<!-- Centered content -->
<div align="center">
  <!-- Image -->
  <img src="https://github.com/user-attachments/assets/aa697654-16be-4b74-9d79-e035dc95833d" alt="Image Description" width="300px">
  
  <!-- Title and Information -->
  <h1>Artificial Intelligence (Lab)</h1>
  <h2>Lab 2 Task</h2>
  <p><strong>Arsalan Khan</strong><br>2022115<br>Cyber Security</p>
  <br>
  <h3>Submitted to: Sir Usama Arshad</h3>
  <p>Date: September 11, 2024</p>
</div>

<!-- Separator -->
<hr>

<!-- Code Block 1 -->
<h3>Below is the Python code for theMaze escape game using A* algorithm Algorithm:</h3>

```python
import heapq  # Importing heapq to implement the priority queue for A* algorithm
import random  # Importing random to place the obstacles
import math    # Importing math for distance calculations
```
Goal Adjustment: Start ('S') and Escape ('E')
I changed the treasure hunt mechanics to be a maze escape by setting a fixed escape goal at the bottom-right of the grid.

Now, the escape point ('E') is always at the bottom-right corner, unlike the treasure, which was placed randomly.
```python
# Function to create a grid based on user-defined size
def create_grid(size):
    grid = [[' ' for _ in range(size)] for _ in range(size)]  # Create an empty grid filled with spaces
    grid[0][0] = 'S'  # 'S' marks the starting point at the top-left corner (0,0)
    grid[size-1][size-1] = 'E'  # 'E' marks the escape point at the bottom-right corner
    return grid

# Function to check if a position is valid (within bounds and not blocked by an obstacle)
def is_valid_position(grid, x, y):
    size = len(grid)
    return 0 <= x < size and 0 <= y < size and grid[x][y] != 'X'  # Return true if position is valid
```

Added Path Validation Function (is_path_available)
I introduced a helper function to check if a valid path exists between the start and the goal after placing obstacles.
```python
# Breadth-First Search (BFS) to check if a path exists from start to goal
def is_path_available(grid, start, goal):
    size = len(grid)
    queue = [start]
    visited = set()
    directions = [(-1, 0), (1, 0), (0, -1), (0, 1)]  # Possible directions: up, down, left, right

    while queue:
        current = queue.pop(0)
        if current == goal:
            return True  # A path exists

        for direction in directions:
            next_x = current[0] + direction[0]
            next_y = current[1] + direction[1]
            next_state = (next_x, next_y)

            if is_valid_position(grid, next_x, next_y) and next_state not in visited:
                visited.add(next_state)
                queue.append(next_state)

    return False  # No path exists
```
 Updated Obstacle Placement to Avoid Blocking Paths (add_obstacles)
The obstacle placement logic is modified to check if an obstacle blocks the path. If it does, it reverts that obstacle and tries again.
```python
# Function to add random obstacles to the grid without blocking the path from 'S' to 'E'
def add_obstacles(grid, num_obstacles):
    size = len(grid)
    original_grid = [row.copy() for row in grid]  # Make a copy of the grid without obstacles

    for _ in range(num_obstacles):
        obstacle_x, obstacle_y = random.randint(0, size-1), random.randint(0, size-1)
        # Ensure obstacles are not placed on the start 'S' or escape 'E'
        while grid[obstacle_x][obstacle_y] in ['S', 'E']:
            obstacle_x, obstacle_y = random.randint(0, size-1), random.randint(0, size-1)

        # Temporarily place an obstacle
        grid[obstacle_x][obstacle_y] = 'X'

        # Check if a valid path exists after placing the obstacle
        if not is_path_available(grid, (0, 0), (size-1, size-1)):
            # If the path is blocked, remove the obstacle and try again
            grid[obstacle_x][obstacle_y] = ' '
    
    return grid
```
Remaining code is almost the same as the Tresure Hunt game
```python
# Heuristic function: Calculates the straight-line (Euclidean) distance between the current node and the goal
def heuristic(a, b):
    return math.sqrt((a[0] - b[0])**2 + (a[1] - b[1])**2)

# A* algorithm function to find the shortest path
def a_star(grid, start, goal):
    size = len(grid)
    # Priority queue to keep track of nodes to explore (using heapq)
    open_list = []
    heapq.heappush(open_list, (0, start))  # Add the start node with priority 0

    # Dictionaries to store the cost to reach each node and the path taken
    g_score = {start: 0}  # Cost from start to current node
    parent = {start: None}  # To reconstruct the path

    directions = [(-1, 0), (1, 0), (0, -1), (0, 1)]  # Possible directions: up, down, left, right

    while open_list:
        _, current = heapq.heappop(open_list)  # Get the node with the lowest f(n)

        # If we reach the goal (escape), stop the search
        if current == goal:
            break

        # Explore neighboring positions (up, down, left, right)
        for direction in directions:
            next_x = current[0] + direction[0]  # Calculate next x-coordinate
            next_y = current[1] + direction[1]  # Calculate next y-coordinate
            next_state = (next_x, next_y)  # Form the next state (position)

            # Check if the next position is valid
            if is_valid_position(grid, next_x, next_y):
                tentative_g_score = g_score[current] + 1  # Cost of moving to the next position

                # If the next state has not been explored or we found a cheaper path to it
                if next_state not in g_score or tentative_g_score < g_score[next_state]:
                    g_score[next_state] = tentative_g_score  # Update the cost to reach this state
                    f_score = tentative_g_score + heuristic(next_state, goal)  # Calculate the total cost f(n)
                    heapq.heappush(open_list, (f_score, next_state))  # Add the state to the open list
                    parent[next_state] = current  # Set the current state as the parent of the next state

    # Reconstruct the path from start to goal
    path = []
    current = goal  # Start from the goal (escape) and work backwards
    while current is not None:
        path.append(current)  # Add current position to the path
        current = parent[current]  # Move to the parent of the current state
    path.reverse()  # Reverse the path to start from the beginning (start to goal)

    return path

# Function to print the grid with lines and the path marked
def print_grid_with_path(grid, path):
    grid_with_path = [row.copy() for row in grid]  # Copy the original grid to preserve it
    for (x, y) in path:
        if grid_with_path[x][y] not in ['S', 'E']:  # Don't overwrite start 'S' and escape 'E'
            grid_with_path[x][y] = '*'  # Mark the path with '*'

    # Print the grid with lines to separate cells clearly
    print("\nGrid with Path:")
    print('-' * (len(grid_with_path) * 4 + 1))  # Print top border line
    for row in grid_with_path:
        print('| ' + ' | '.join(row) + ' |')  # Print row with borders between cells
        print('-' * (len(grid_with_path) * 4 + 1))  # Print horizontal line after each row

# Main function to play the game
def maze_escape():
    # Ask the user for grid size and number of obstacles
    size = int(input("Enter the grid size (e.g., 6 for a 6x6 grid): "))
    num_obstacles = int(input(f"Enter the number of obstacles (less than {size * size - 2}): "))  # Make sure obstacles are less than available spaces

    # Create the grid with start 'S' and escape 'E'
    grid = create_grid(size)

    # Add random obstacles to the grid without blocking the path from 'S' to 'E'
    grid = add_obstacles(grid, num_obstacles)

    # Print the initial grid
    print("\nInitial Grid:")
    print_grid_with_path(grid, [])  # Empty path initially

    # Start the search using A* algorithm
    print("\nSearching for the escape using A* algorithm...\n")
    path = a_star(grid, (0, 0), (size-1, size-1))  # Perform A* search

    # Print the final grid with the path marked
    print("\nPath to Escape:")
    print_grid_with_path(grid, path)  # Show the path to escape

# Run the game
maze_escape()

```
Output:

![1](https://github.com/user-attachments/assets/191ebc6f-ad36-45c0-9bb8-468b7de37740)![2](https://github.com/user-attachments/assets/ae4ccd72-7474-4fdd-be50-1166b8e50f65)

