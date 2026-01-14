# Maze SLAM & Relocalization Challenge (Final Project)

**Type:** Team project  
**Platform:** Mobile robot (LEGO NXT-based) + simulation twin (Gazebo SDF)  
**Scope:** Mapping + Localization + Navigation

### One-line summary
Developed an autonomous mobile robot stack for maze mapping, localization, and goal-directed navigation using a LEGO NXT-based robot and Gazebo simulation twin.

### What I built
- Implemented autonomous **exploration and occupancy-grid mapping** of unknown mazes.
- Developed **relocalization and goal-reaching** capabilities using particle-filter-based localization.
- Designed **planner and controller** for non-holonomic mobile robot navigation with collision avoidance.
- Built a **reproducible simulation workflow** with launch scripts, map outputs, and short demo videos.

## Overview
Built a simulation twin of a physical maze and developed an autonomous mobile-robot stack to:
- **Task A:** Explore from a random start and build a consistent map.
- **Task B:** Start from a new random pose, relocalize using the saved map, then reach a specified goal.

## Requirements (Project Specs)
- **Simulation twin:** Maze modeled as an SDF world with proper geometry/friction and sensors.
- **Task A (Exploration + Mapping):** autonomous exploration + map generation.
- **Task B (Relocalization + Goal Reach):** global relocalization then navigate to goal.
- **Reproducibility:** one-command launch and no hard-coded start poses.

## System Design (High level)
### Mapping
- Occupancy-grid mapping (log-odds / inverse sensor model) or equivalent.
- Output: final map image/file.

### Localization
- Recursive state estimation (prediction + update).
- Approach supports relocalization (multi-hypothesis recommended using particle filters / MCL).

### Navigation & Control
- Planner + controller suitable for non-holonomic/diff-drive constraints.
- Safety constraints (avoid collisions; smooth motion preferred).

## Deliverables
- `worlds/maze.sdf` + models
- Launch scripts / run commands + README
- Final map output
- Short videos: Task A + Task B
- Report describing models, estimator choices, experiments, and ablations

## Media


## Notes
Public summary only. Full implementation/code may be kept private and shared upon request when appropriate.
