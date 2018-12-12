## Quickstart

#### The following is an example workflow and sequence of commands using default settings:

```sh
source /opt/ros/kinetic/setup.bash                  # Setup the general ROS environmnet variables.

mkdir -p ~/ros_workspace_example/src                # Create your own workspace. (Actions are only allowed in the `src/`)
cd ~/ros_workspace_example/

catkin init                                         # Initialize it with a hidden marker file.

cd ~/ros_workspace_example/src/                     # Navigate to the source space, and create your own packages.
catkin create pkg pkg_a
catkin create pkg pkg_b
catkin create pkg pkg_c --catkin-deps pkg_a
catkin create pkg pkg_d --catkin-deps pkg_a pkg_b

catkin list                                         # List the packages in the workspace.
catkin build                                        # Build all packages in the workspace.

cd ..                                               # Load this workspace's environment.
source devel/setup.bash
```
###### _(refer to https://catkin-tools.readthedocs.io/en/latest/quick_start.html)_



## Catkin Actions' DEMOs

#### Initialize it with a hidden marker file
```sh
$ pwd
/home/root/ros_workspace_example

$ catkin init
Catkin workspace `/home/root/ros_workspace_example` is already initialized. No action taken.
------------------------------------------------------------------------------------
Profile:                     default
Extending:             [env] /home/root/workspace_1/devel:/opt/ros/kinetic
Workspace:                   /home/root/ros_workspace_example
------------------------------------------------------------------------------------
Source Space:       [exists] /home/root/ros_workspace_example/src
Log Space:         [missing] /home/root/ros_workspace_example/logs
Build Space:       [missing] /home/root/ros_workspace_example/build
Devel Space:       [missing] /home/root/ros_workspace_example/devel
Install Space:      [unused] /home/root/ros_workspace_example/install
DESTDIR:            [unused] None
------------------------------------------------------------------------------------
Devel Space Layout:          linked
Install Space Layout:        None
------------------------------------------------------------------------------------
Additional CMake Args:       None
Additional Make Args:        None
Additional catkin Make Args: None
Internal Make Job Server:    True
Cache Job Environments:      False
------------------------------------------------------------------------------------
Whitelisted Packages:        None
Blacklisted Packages:        None
------------------------------------------------------------------------------------
Workspace configuration appears valid.
------------------------------------------------------------------------------------
```

#### List the packages in the workspace
```sh
$ pwd
/home/root/ros_workspace_example/src

$ tree
.
├── pkg_a
│   ├── CMakeLists.txt
│   └── package.xml
├── pkg_b
│   ├── CMakeLists.txt
│   └── package.xml
├── pkg_c
│   ├── CMakeLists.txt
│   └── package.xml
└── pkg_d
    ├── CMakeLists.txt
    └── package.xml
4 directories, 8 files

$ catkin list
- pkg_a
- pkg_b
- pkg_c
- pkg_d
```

#### Build all packages in the workspace
```sh
$ pwd
/home/root/ros_workspace_example/src

$ catkin build
------------------------------------------------------------------------------------
Profile:                     default
Extending:             [env] /home/root/workspace_1/devel:/opt/ros/kinetic
Workspace:                   /home/root/ros_workspace_example
------------------------------------------------------------------------------------
Source Space:       [exists] /home/root/ros_workspace_example/src
Log Space:         [missing] /home/root/ros_workspace_example/logs
Build Space:        [exists] /home/root/ros_workspace_example/build
Devel Space:        [exists] /home/root/ros_workspace_example/devel
Install Space:      [unused] /home/root/ros_workspace_example/install
DESTDIR:            [unused] None
------------------------------------------------------------------------------------
Devel Space Layout:          linked
Install Space Layout:        None
------------------------------------------------------------------------------------
Additional CMake Args:       None
Additional Make Args:        None
Additional catkin Make Args: None
Internal Make Job Server:    True
Cache Job Environments:      False
------------------------------------------------------------------------------------
Whitelisted Packages:        None
Blacklisted Packages:        None
------------------------------------------------------------------------------------
Workspace configuration appears valid.

NOTE: Forcing CMake to run for each package.
------------------------------------------------------------------------------------
[build] Found '4' packages in 0.0 seconds.
[build] Updating package table.
Starting  >>> catkin_tools_prebuild
Finished  <<< catkin_tools_prebuild                [ 1.1 seconds ]
Starting  >>> pkg_a
Starting  >>> pkg_b
Finished  <<< pkg_a                                [ 1.1 seconds ]
Starting  >>> pkg_c
Finished  <<< pkg_b                                [ 1.1 seconds ]
Starting  >>> pkg_d
Finished  <<< pkg_c                                [ 1.1 seconds ]
Finished  <<< pkg_d                                [ 1.1 seconds ]
[build] Summary: All 5 packages succeeded!
[build]   Ignored:   None.
[build]   Warnings:  None.
[build]   Abandoned: None.
[build]   Failed:    None.
[build] Runtime: 3.4 seconds total.
[build] Note: Workspace packages have changed, please re-source setup files to use them.
```

#### Clean all the build products
```sh
$ pwd
/home/root/ros_workspace_example

$ catkin clean

[clean] Warning: This will completely remove the following directories. (Use `--yes` to skip this check)
[clean] Log Space:     /home/root/ros_workspace_example/logs
[clean] Build Space:   /home/root/ros_workspace_example/build
[clean] Devel Space:   /home/root/ros_workspace_example/devel

[clean] Are you sure you want to completely remove the directories listed above? [yN]: y
[clean] Removing develspace: /home/root/ros_workspace_example/devel
[clean] Removing buildspace: /home/root/ros_workspace_example/build
[clean] Removing log space: /home/root/ros_workspace_example/logs
```
