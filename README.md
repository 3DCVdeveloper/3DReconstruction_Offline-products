# 3DReconstruction_Offline-products
Offline Product 3D Reconstruction and Real time Pose Tracking System Based on RGBD Camera

# 测试说明与数据结果分析
ROS 通信下，同步接收和保存 RGBD 图片的 demo

首先在终端测试 ROS 通信是否有效 rostopic list，然后测试接收的主题，如：rostopic

hz/camera/depth_registered/hw_registered/image_rect_raw/compressedDepth

首先打开/test/RGBDsave.py，修改里面保存图片的路径和订阅的 topic

![image](https://github.com/user-attachments/assets/c3eb5cec-2af3-40d0-9b2d-2463c0d1cad1)

安装库 pip install rospy 和其他需要的库

为了 anaconda 和 ROS 的 python 兼容，激活虚拟环境和 source 一下

cd 所在的目录，终端运行 python RGBDsave.py。如果还是出错请尝试用 pyhton2

运行 ：python2 RGBDsave.py。

G2L 算法 DEMO（离线单帧图片处理）

准备 

修改内参数据

在/G2L_Net/utils 文件夹下找到 utils_funs.py，这里存放这一些实用的函数，找到 def define_paras()手动填入相机内参 K

![image](https://github.com/user-attachments/assets/54369c0c-341d-4755-a3f5-51f7caacbb21)

修改存放测试 RGB 和 depth 图片文件夹的路径：

![image](https://github.com/user-attachments/assets/16a59322-a25a-4c56-a38a-08a02193de01)

注意本项目使用的是绝对路径，可在终端用 pwd 查看文件夹路径。

修改图片的文件名称，如‘0001.png’，depth 图片和 RGB 图片需要同名；再修改测试列表文件/G2L_Net/models/1valseg_astra.lst

![image](https://github.com/user-attachments/assets/60917290-ec19-4506-af3d-8edbdffb8d65)

# 程序测试

cd 到/G2L_Net/demo 文件夹中 终端运行（也可以在 Pycharm 上 run）test_AR.py 或者 test_linemod.py，会得到可视化结果：

这是一个带有三维轴向的 aruco marker

![image](https://github.com/user-attachments/assets/11f7cae8-2fa7-42ae-9c68-86a8261258a8)

物体位姿的可视化，整个立方 box 代表物体的位置，其中红色一面表示物体的正视平面

![image](https://github.com/user-attachments/assets/97796bf8-3632-49a8-acde-125195f81f1d)

以下为 DEMO 输出的数据结果：

![image](https://github.com/user-attachments/assets/a6a173cf-69d4-49e6-9e93-61386662d618)

