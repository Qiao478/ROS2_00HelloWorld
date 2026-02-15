# ROS2_00HelloWorld

终端输入：
mikdir -p ROS2_HelloWorld/src       #创建一个名为ROS2_HelloWorld的文件夹，作为工作空间，并在ROS2_HelloWorld下创建一个名为src的文件夹
cd ROS2_HelloWorld                  #进入ROS2_HelloWorld的工作空间  
colcon build                        #编译

编译结束后的工作空间如下图所示:
[先欠着，我不会放图片，后期再来补]

[编写程序步骤]
1.创建功能包
2.编辑源文件
3.编辑配置文件
4.编译
5.执行

C++实现
终端输入：
ros2 pkg create 00HelloWorld_cpp --build-type ament_cmake --dependencies rclcpp --node-name HelloWorld #创建功能包，注意要在工作空间的src下
#ros2 pkg create         创建一个功能包
#00HelloWorld_cpp        功能包的包名
#--build-type            制定构建类型
#ament_cmake              C++类型
#--dependencies          设置依赖
#rclcpp                  C++
#--node-name             设置一个节点
#HelloWorld              节点的名字为HelloWorld

编辑00HelloWorld_cpp/src目录下的HelloWorld进行编辑，编辑内容：
/*
需求：在终端输出Hello World
*/

#include"rclcpp/rclcpp.hpp"

int main(int argc,char **argv){
//初始化ROS2客户端
	rclcpp::init(argc,argv);
//创建节点指针
	auto node =rclcpp::Node::make_shared("helloworld_node_cpp");
//输出日至
	RCLCPP_INFO(node->get_logger(),"Hello World");
//释放资源
	rclcpp::shutdown();
	return 0;
}

Python实现
终端输入
ros2 pkg create 00HelloWorld_python --build-type ament_python --dependencies rclpy --node-name HelloWorld_python

import rclpy
def main():
    #初始化
    rclpy.init()
    #创建节点
    node = rclpy.create_node("helloworld_python")
    #输出日至
    node.get_logger().info("helloworld(python)")
    #释放资源
    rclpy.shutdown()



colson build                              #编译，在工作空间00HelloWorld_cpp路径下
或编译某（几）个文件
colcon build --packages-select 文件名

. install/setup.bash                      #更新环境变量  或写做 cource install/setup.bash
ros2 run 00HelloWorld_cpp HelloWorld      #运行工作空间00HelloWorld_cpp  节点HelloWorld

