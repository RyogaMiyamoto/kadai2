# kadai2

# ロボットシステム学・課題２
課題２はROSを用いてパッケージを作成します。  

# 概要
パッケージの作成  
ノードの作成  
ノードの実行  
count.pyの実行  
twice.pyの実行  


# 使用環境
- Raspberry Pi 3 Model B  
- Ubuntu 20.04 LTS
- ROS  

# 操作方法
## 【ROSのインストール】
```
git clone https://github.com/ryuichiueda/ros_setup_scripts_Ubuntu20.04_server.git
cd ros_setup_scripts_Ubuntu20.04_server
./step0.bash　　　　//実行  
./step1.bash       //実行  　　
roscore            //立ち上がりの確認
```
## 【ワークスペースの準備】
### ディレクトリの作成
```
cd
mkdir -p catkin_ws/src
cd ~/catkin_ws/src
catkin_init_workspace 
```

上記のコマンドを実行すると以下のように表示される

```
Creating symlink "/home/ubuntu/catkin_ws/src/CMakeLists.txt" pointing to 
"/opt/ros/melodic/share/catkin/cmake/toplevel.cmake"  
```

### 【環境のビルド】
```
cd ~/catkin_ws
catkin_make
source ~/.bashrc
```

上記のコマンドを実行して、ROS_PACKAGE_PATHにcatkin_ws/srcがセットされているかを以下のコマンドで確認する
```
echo $ROS_PACKAGE_PATH
```

**/home/ubuntu/catkin_ws/src:/opt/ros/noetic/share**と表示されれば、ROS_PACKAGE_PATHにcatkin_ws/srcがセットされている状態だと確認できる

### 【実行】
ああああ  


# 実演動画
[Youtube・課題2](https://youtu.be/CH7Q0QQwE90)

# License
BSD 2-Clause "Simplified" License
