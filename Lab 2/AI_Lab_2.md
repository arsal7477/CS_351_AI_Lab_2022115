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
<h3>Below is the Python code for theMaze escape game using Bredth First Search Algorithm:</h3>

```python
import queue  # Importing queue to implement BFS
import random  # Importing random to place the obstacles randomly and shuffle directions

# Function to create a maze based on user-defined size and fixed exit at bottom-right corner
def create_maze(size):
    maze = [[' ' for _ in range(size)] for _ in range(size)]  # Create an empty maze filled with spaces
    maze[0][0] = 'S'  # 'S' marks the starting point at the top-left corner (0,0)
    maze[size-1][size-1] = 'E'  # 'E' marks the exit at the bottom-right corner (size-1, size-1)
    return maze, (size-1, size-1)  # Return the maze and the exit's fixed position

# Function to check if a position is valid (within bounds and not blocked by an obstacle)
def is_valid_position(maze, x, y):
    size = len(maze)
    return 0 <= x < size and 0 <= y < size and maze[x][y] not in ['X']  # Return true if position is valid and not blocked

# BFS function to find the initial path from start to exit with randomized direction order
def bfs(maze, start, goal):
    size = len(maze)
    q = queue.Queue()  # Create a queue for BFS
    q.put(start)  # Start from the initial position
    visited = set()  # Use a set to track visited positions
    visited.add(start)  # Mark the start position as visited
    parent = {}  # Dictionary to store the parent of each state for path reconstruction

    directions = [(-1, 0), (1, 0), (0, -1), (0, 1)]  # Possible directions: up, down, left, right

    while not q.empty():
        current = q.get()  # Get the current position from the queue

        # If we reach the exit (goal), stop the search
        if current == goal:
            break

        # Shuffle the directions to explore in random order
        random.shuffle(directions)

        # Explore neighboring positions in the shuffled direction order
        for direction in directions:
            next_x = current[0] + direction[0]  # Calculate next x-coordinate
            next_y = current[1] + direction[1]  # Calculate next y-coordinate
            next_state = (next_x, next_y)  # Form the next state (position)

            # Check if the next position is valid and not already visited
            if is_valid_position(maze, next_x, next_y) and next_state not in visited:
                q.put(next_state)  # Add the valid position to the queue
                visited.add(next_state)  # Mark the position as visited
                parent[next_state] = current  # Track how we reached this state

    # Reconstruct the path from start to goal
    path = []
    current = goal  # Start from the goal (exit) and work backwards
    while current != start:
        path.append(current)  # Add current position to the path
        current = parent.get(current, start)  # Move to the parent of the current state
    path.append(start)  # Add the start position to the path
    path.reverse()  # Reverse the path to start from the beginning (start to goal)

    return path

# Function to add random obstacles to the maze ensuring a valid path exists
def add_obstacles(maze, num_obstacles, path):
    size = len(maze)
    possible_positions = [(x, y) for x in range(size) for y in range(size)
                          if (x, y) not in path and maze[x][y] not in ['S', 'E']]  # Exclude the path and start/exit

    # Place obstacles only in positions not part of the path
    for _ in range(num_obstacles):
        if not possible_positions:
            break  # No more positions available for obstacles
        obstacle_x, obstacle_y = random.choice(possible_positions)
        maze[obstacle_x][obstacle_y] = 'X'  # Place the obstacle 'X'
        possible_positions.remove((obstacle_x, obstacle_y))  # Remove the position from possible positions

    return maze

# Function to print the maze with lines and the path marked
def print_maze_with_path(maze, path):
    maze_with_path = [row.copy() for row in maze]  # Copy the original maze to preserve it
    for (x, y) in path:
        if maze_with_path[x][y] not in ['S', 'E']:  # Don't overwrite start 'S' and exit 'E'
            maze_with_path[x][y] = '*'  # Mark the path with '*'

    # Print the maze with lines to separate cells clearly
    print("\nMaze with Path:")
    print('-' * (len(maze_with_path) * 4 + 1))  # Print top border line
    for row in maze_with_path:
        print('| ' + ' | '.join(row) + ' |')  # Print row with borders between cells
        print('-' * (len(maze_with_path) * 4 + 1))  # Print horizontal line after each row

# Main function to play the game
def maze_escape():
    # Ask the user for maze size and number of obstacles
    size = int(input("Enter the maze size (e.g., 6 for a 6x6 maze): "))
    num_obstacles = int(input(f"Enter the number of obstacles (less than {size * size - 2}): "))  # Ensure fewer obstacles than available spaces

    # Create the maze with the exit fixed at the bottom-right corner
    maze, goal = create_maze(size)

    # Generate a valid path using randomized BFS before placing obstacles
    path = bfs(maze, (0, 0), goal)

    # Add random obstacles while ensuring the path remains valid
    maze = add_obstacles(maze, num_obstacles, path)

    # Print the initial maze
    print("\nInitial Maze:")
    print_maze_with_path(maze, [])  # Empty path initially

    # Print the path that was generated
    print("\nPath to the Exit:")
    print_maze_with_path(maze, path)  # Show the path to the exit

# Run the game
maze_escape()
```
