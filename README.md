# ROS2

## Overview

This repository documents the installation and verification process of ROS 2 Humble on Ubuntu.

---

# Installation Steps

## 1. Update System

Update the Ubuntu packages:

```bash
sudo apt update && sudo apt upgrade -y
```

---

## 2. Install Required Tools

Install required packages:

```bash
sudo apt install software-properties-common curl -y
```

---

## 3. Add ROS 2 Security Key

Download the ROS 2 key:

```bash
sudo curl -SsL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
```

---

## 4. Add ROS 2 Repository

Add the ROS 2 repository:

```bash
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu jammy main" | sudo tee /etc/apt/sources.list.d/ros2.list
```

Update packages:

```bash
sudo apt update
```

---

## 5. Install ROS 2 Humble Desktop

Install ROS 2 Humble:

```bash
sudo apt install ros-humble-desktop
```

---

## 6. Configure ROS Environment

Enable ROS automatically:

```bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
```

Apply the environment:

```bash
source ~/.bashrc
```

---

# Verification

## Check ROS Distribution

Command:

```bash
echo $ROS_DISTRO
```

Output:

```text
humble
```

---

## Check ROS System

Command:

```bash
ros2 doctor
```

Output:

```text
All 3 checks passed
```

---

# Evidence

ROS 2 Humble verification screenshot:

![ROS2 Evidence](ROS2_Evidence.jpg)

---

# Problems Encountered

## Low Disk Space Issue

During ROS installation, a low disk space warning appeared.

The problem was solved by cleaning unused packages:

```bash
sudo apt clean
```

```bash
sudo apt autoremove -y
```

Fixing interrupted packages:

```bash
sudo dpkg --configure -a
```

Repairing broken dependencies:

```bash
sudo apt --fix-broken install
```

After freeing disk space, ROS 2 Humble installation completed successfully.

---

# Conclusion

ROS 2 Humble was successfully installed on Ubuntu.

The installation was verified using:

- ROS distribution check
- ROS system diagnostic check

The system passed all ROS checks and is ready to use.
