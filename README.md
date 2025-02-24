# Multi-Agent Path Planning with A* Algorithm

This project implements a multi-agent path planning system using the A* algorithm in a grid environment. It's designed to find optimal paths for multiple agents while avoiding obstacles and collisions.

## Features

- Grid-based environment representation
- A* pathfinding algorithm implementation
- Support for multiple agents
- Obstacle avoidance
- Collision prevention between agents
- Visualization of the grid and paths

## Requirements

- Python 3.x
- NumPy
- Matplotlib

## Installation

1. Clone this repository:
   ```
   git clone https://github.com/HBX814/multi-agent-path-planning.git
   ```
2. Install the required packages:
   ```
   pip install numpy matplotlib
   ```

## Usage

Run the main script to see the path planning in action:

```
python main.py
```

This will generate a random grid environment, place agents and obstacles, and find paths for all agents to their goals.

## Classes

- `GridEnvironment`: Represents the grid world with obstacles
- `PrioritizedPlanner`: Implements the prioritized A* algorithm for multi-agent path planning
- `CollisionAvoidancePlanner`: Extends the planner with collision avoidance between agents
- `PathPlannerTest`: Provides test scenarios and visualization for the path planning algorithms

## Customization

You can modify the following parameters in the script:

- Grid size
- Number of agents
- Number and position of obstacles
- Start and goal positions for agents

## Explanation of Algorithms

### A* Algorithm

The A* algorithm is used for pathfinding in this project. It's an informed search algorithm that finds the least-cost path from a start node to a goal node. A* uses a best-first search and finds a least-cost path from a given initial node to one goal node (out of one or more possible goals).

Key components of A*:
- f(n) = g(n) + h(n)
  - g(n): cost of the path from the start node to n
  - h(n): heuristic estimate of the cost from n to the goal

The algorithm maintains a priority queue of nodes to be traversed, sorted by their f(n) values. It expands nodes with the lowest f(n) value first, ensuring an optimal path is found if one exists.

### Prioritized Planning

The project uses a prioritized planning approach for multi-agent pathfinding:

1. Assign priorities to agents (e.g., based on distance to goal)
2. Plan paths for agents in order of priority
3. Treat previously planned paths as moving obstacles for subsequent agents

This method is computationally efficient but may not always find optimal solutions for all agents.

### Collision Avoidance

The `CollisionAvoidancePlanner` extends the basic planner to prevent collisions between agents:

- It considers the planned paths of higher-priority agents as time-dependent obstacles
- When planning a path for an agent, it checks for potential collisions with previously planned paths
- If a collision is detected, it attempts to find an alternative path or wait until the path is clear

## Visualization

The script generates visualizations of:

- The grid environment with obstacles
- Start and goal positions of agents
- Calculated paths for each agent

## Contributing

Contributions to improve the algorithm, add features, or fix bugs are welcome. Please feel free to submit a pull request or open an issue.

