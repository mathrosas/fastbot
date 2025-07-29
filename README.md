# FastBot

Repository for the FastBot robotics project. Contains all packages needed to run FastBot on real hardware.

## Repository Structure

```
fastbot/
├── fastbot_description    # URDF robot model and meshes
├── lslidar_ROS2_driver    # RPLIDAR sensor driver publishing `/fastbot/scan`
├── serial_motor_msgs      # Custom ROS 2 message definitions for motor commands and feedback
├── serial_motor           # Node interfacing motor driver hardware using `serial_motor_msgs`
└── fastbot_bringup        # Launch files and configurations to ROSify the robot on real hardware
```

## Prerequisites

* ROS 2 Humble (tested)
* Ubuntu Server on Raspberry Pi (real robot)

## Installation

Clone this repository into your ROS 2 workspace `src` directory:

```bash
cd ~/ros2_ws/src
git clone https://github.com/mathrosas/fastbot.git
```

Build and source your workspace:

```bash
cd ~/ros2_ws
colcon build
source install/setup.bash
```

## Usage

### Bringup on Real Hardware

1. On your Raspberry Pi (Ubuntu Server), ensure ROS 2 Humble is installed and your workspace built and sourced.

2. Launch the FastBot drivers on the robot:

   ```bash
   ros2 launch fastbot_bringup bringup.launch.xml
   ```

3. From an external computer (same network and `ROS_DOMAIN_ID`) or another terminal, teleoperate the robot:

   ```bash
   ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args --remap cmd_vel:=/fastbot_1/cmd_vel
   ```

## Contributing

Issues and pull requests are welcome.

## License

Specify your project license here.

