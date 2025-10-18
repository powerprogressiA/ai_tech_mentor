# Copilot Instructions for AI Coding Agents

## Project Overview
This repository contains AI and robotics modules, with a focus on the "Mind-Controlled Car" ROS 2 package. The main components are in `ai_tech_mentor/` and `ai_tech_mentor/mind-controlled-car/`.

### Mind-Controlled Car (ROS 2)
- Located in `mind-controlled-car/`.
- Implements a ROS 2 Jazzy package for a mind-controlled vehicle using Emotiv Insight BLE, Pixhawk/MAVROS, and u-blox F9P.
- Key launch file: `launch/complete_system.launch.py` (starts all nodes).
- Main nodes:
  - `emotiv_node`: Publishes mental commands (simulated in code).
  - `mind_interpreter`: Converts mental commands to velocity commands.
  - `pixhawk_bridge`: Bridges velocity commands to Pixhawk (demo, no MAVROS calls in code).
  - `gps_node`: Simulates GPS data.
- Example build/run workflow:
  ```sh
  cd ~/mind_car_ws
  colcon build --symlink-install
  source install/setup.bash
  ros2 launch mind_control_car complete_system.launch.py
  ```
- Dependencies: ROS 2 Jazzy, Python, rclpy, std_msgs, geometry_msgs (see `package.xml`).

## Developer Workflows
- **Build**: Use `colcon build --symlink-install` in the ROS workspace.
- **Run**: Use `ros2 launch mind_control_car complete_system.launch.py`.
- **Node code**: All main logic is in `mind_control_car/` submodules.
- **Docs**: MkDocs config in `mkdocs.yml` and docs in `docs/`.

## Conventions & Patterns
- Each ROS node is a Python class in `mind_control_car/` and follows the rclpy Node pattern.
- Topic names: `mental_command`, `cmd_vel`.
- Use `get_logger().info()` for runtime logging.
- No custom message types; only standard ROS messages.
- Simulated/demo logic is used in place of hardware integration in code.

## Integration Points
- Emotiv Insight BLE (simulated in code)
- Pixhawk/MAVROS (integration to be implemented)
- u-blox F9P GPS (simulated)

## Key Files & Directories
- `mind-controlled-car/launch/complete_system.launch.py`: Launches all nodes
- `mind-controlled-car/mind_control_car/`: Node implementations
- `mind-controlled-car/package.xml`: ROS 2 dependencies
- `mind-controlled-car/mkdocs.yml`: Documentation structure

## Tips for AI Agents
- Follow the ROS 2 node and topic structure as in the provided node files.
- When adding new nodes, mimic the structure of existing ones.
- For hardware integration, stub/demo logic may need to be replaced with real device code.
- Keep all new ROS nodes in the `mind_control_car/` package.
