# 第一章

### ROS程序实现流程

1. **创建一个工作空间并初始化**

   ```bash
   mkdir -p 自定义空间名称/src
   cd 自定义空间名称
   catkin_make
   ```

   > 创建一个工作空间以及一个 src 子目录，然后再进入工作空间调用 catkin_make命令编译。

   

2. **进入 src 创建 ros 包并添加依赖**

   ```bash
   cd src
   catkin_create_pkg 自定义ROS包名 roscpp rospy std_msgs
   ```

   > 在工作空间下生成一个功能包，该功能包依赖于 roscpp、rospy 与 std_msgs

   

   **vscode：**

   ```bash
   cd 工作空间
   code .	# 启动vscode
   ```

   选定 src 右击 ---> create catkin package创建 ROS 功能包，设置包名添加依赖

   快捷键 ctrl + shift + B 调用编译（已修改json文件）

   

3. **编辑源文件**

   C++使用以下代码可在终端输出中文

   ```cpp
   setlocale(LC_ALL, "");
   ```

   python编辑完后需额外为文件添加可执行权限

   ```bash
   chmod +x 自定义文件名.py
   或 chmod +x *.py 为所有py文件添加权限
   ```

   

4. **编辑 ros 包下的 Cmakelist.txt文件**

   1. c++

      ```c++
      add_executable(步骤3的源文件名
        src/步骤3的源文件名.cpp
      )
      target_link_libraries(步骤3的源文件名
        ${catkin_LIBRARIES}
      )
      ```

   2. python

      ```python
      catkin_install_python(PROGRAMS scripts/步骤3的源文件名.py
        DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
      )
      ```

   

5. **编译并执行**

   编译: ctrl + shift + B

   刷新bash```source ./devel/setup.bash```

   执行
