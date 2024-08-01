# Installing ROS Noetic on Ubuntu in VirtualBox

This README provides a comprehensive guide on how to install ROS Noetic on Ubuntu using VirtualBox. It includes all necessary commands, their explanations, and optional steps for enhancing the setup experience.

## Prerequisites

### VirtualBox Installation
- Download and install the latest version of [VirtualBox](https://www.virtualbox.org/).
- Ensure your system meets the hardware requirements to run a virtual machine smoothly.

### Ubuntu Installation
- Download the Ubuntu Desktop 20.04.1 ISO file from the [official Ubuntu website](https://releases.ubuntu.com/20.04/).
- Create a new VM in VirtualBox and install Ubuntu 20.04.1.

## Setting Up Ubuntu

### Full-Screen Mode
To enter full-screen mode in VirtualBox, press `Host Key (Right Ctrl by default) + F`.

### Enable Copy and Paste
To enable shared clipboard and drag-and-drop between host and guest systems:
1. In VirtualBox, go to **Settings > General > Advanced**.
2. Set "Shared Clipboard" and "Drag'n'Drop" to "Bidirectional".

## Installing ROS Noetic

### Setting Up the Sources List
```sh
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-noetic.list'
```
This command adds the ROS package repository to your system's sources list, enabling access to ROS packages.

### Adding the ROS Key
```sh
sudo apt install curl
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
```
Installs `curl` and adds the ROS package key to your system, allowing secure installation of ROS packages.

### Updating the Package Index
```sh
sudo apt update
```
Refreshes the list of available packages, including those from the newly added ROS repository.

### Installing ROS Noetic
```sh
sudo apt install ros-noetic-desktop-full
```
Installs the full ROS Noetic desktop package, which includes all necessary tools and libraries.

### Environment Setup
```sh
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```
This command adds the ROS setup script to your bash startup file, ensuring ROS commands are available in every terminal session.

### Installing rosinstall
```sh
sudo apt install python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
```
Installs `rosinstall` and other necessary tools for managing ROS workspaces and packages.

## Table of Commands and Their Meanings

| Command                         | Description |
|---------------------------------|-------------|
| `cd`                            | Change directory. Example: `cd /path/to/directory`. |
| `mkdir`                         | Create a new directory. Example: `mkdir new_folder`. |
| `ls`                            | List files and directories in the current directory. |
| `pwd`                           | Print the current working directory. |
| `sudo apt update`               | Update the list of available packages from repositories. |
| `sudo apt upgrade`              | Upgrade all the packages installed on your system to the latest version. |
| `sudo apt install [package]`    | Install a specified package. Example: `sudo apt install vim`. |
| `echo "text" >> file`           | Append text to a file. Example: `echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc`. |
| `source file`                   | Execute commands from a file in the current shell. |
| `ping [address]`                | Check the network connection to a specific address. |

## Optional Step: Configuring Vim for ROS Commands

To make editing files easier, you can use `vim`, a text editor available in Ubuntu. For example, you can use `vim ~/.bashrc` to edit the bash startup file.

### Editing Files with Vim
```sh
vim ~/.bashrc
```
Opens the specified file for editing. You can add the ROS setup script to the bash startup file for convenience.

## Differences Between `bash` and `zsh`

- **`bash` (Bourne Again Shell)**: The default shell for many Linux distributions, including Ubuntu. It is widely used and has a large number of built-in commands and features.
- **`zsh` (Z Shell)**: An alternative to bash with additional features like spelling correction, theme support, and a more flexible scripting syntax. It is not the default shell in Ubuntu but can be installed and used as a replacement.

---

### Notes
For troubleshooting common issues, please refer to the `TROUBLESHOOTING.md` file in this repository. If you encounter any issues not covered here, consult the [ROS documentation](http://wiki.ros.org/noetic) or seek assistance from the community.

---

This README provides a clear guide for installing ROS Noetic on Ubuntu using VirtualBox, along with useful configurations and explanations of commands. Make sure to follow each step carefully and refer to the additional documentation for troubleshooting.
