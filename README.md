# README

## 引言
本实验为基于地面平面拟合的地面分割实验，重点是让学员理解激光雷达的点云数据处理，掌握无人驾驶激光雷达障碍物检测的前期处理--地面分割。本实验的激光点云数据处理包括：1）对原始激光点云数据进行杂波滤波和滤掉过高区域的点云，2）对原始激光点云进行降采样处理，3）选取种子点集，4）建立地面平面模型，5）得到地面点与非地面点。本实验包含1个工作空间，该工作空间下有2个ROS包：plane_ground_filter, UI_plane_ground_filter. 其中，UI_plane_ground_filter：为本实验的软件界面，使用python语言编写；plane_ground_filter：为本实验的核心代码，其中的激光雷达数据处理都在该ROS包中。

## 依赖

- ros kinect(Ubuntu 16.04)
- pyqt5

## 建立工作空间并编译


```
将本实验工作空间拷贝到放在用户笔记本中,并进入该工作空间

%cd fitting

对本实验进行编译

% catkin_make
```

## 开始运行


！！！开始本实验前需要先进行一个路径设置，需要修改地方在fitting/src/fit/UI_plane_ground_filter/scropt/main.py中，将该py文件中的约在66行左右的os.system语句中的 'source ~/project/fitting/devel/setup.bash'改为'source *用户工作空间目录*/fitting/devel/setup.bash'！！！。

```
% cd fitting
% source devel/setup.bash
% roslaunch UI_plane_ground_filter test.launch
```

- 在交互面板中，点击按钮"Start",启动本实验核心程序，届时会打开一个新的terminal窗口和一个RVIZ显示窗口，交互界面中的Guide Book打开实验指导书，其中设置的参数如下：
- "Clip_h"设置要滤除的过高激光点云高度，当点云数据大于Clio_h+Lidar_h时，点云数据滤掉。
- "Lidar_h"激光雷达高度信息。
- "Min_dist"激光雷达点云最近有效点距离。
- "Max_dist"激光雷达点云最远有效点距离。
- "Ilter Num"迭代次数。
- "LPR Num"LPR（Lowest Point Representative）的最低高度点的数量。
- " Seed_th"选取种子点的阈值，当点云内的点的高度小于LPR的高度加上此阈值时，我们将该点加入种子点集。
- "Dist_th"平面距离阈值，计算点云中每一个点到我们拟合的平面的正交投影的距离，而这个平面距离阈值，就是用来判定点是否属于地面。

##示例demo

![demo](https://github.com/ZhongQiXue0423/Picture/blob/master/nihe1.png)

##联系我们
如果您有特殊的相关实验课件需要，或者向我们反馈本实验的BUG,或者是想向我们反馈一些特别的实验数据，请联系我们：
```
Email: 18810381552@163.com
电话  18810381552  钟
```
注： 反馈的数据以rosbag包的格式



