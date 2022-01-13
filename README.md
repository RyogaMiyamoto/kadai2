# kadai2

# ロボットシステム学・課題２
課題２はROSを用いてパッケージを作成します。  

# 概要
パッケージの作成  
ノードの作成  
ノードの実行  
count.pyの実行  
twice.pyの実行  
Ubuntuを4端末を使い、実行を確認します。

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

### 【count.pyの実行】
以下の順番でコマンドを実行してください
```
端末１　roscore
端末２  chmod +x count.py
端末２  rosrun mypkg count.py
端末３  rostopic list         //以下の３つのトピックがあるか確認
/count_up
/rosout
/rosout_agg
端末３  rostopic echo /count_up
```
**rostopic echo /count_up**を実行すると1秒間に10ずつ数字が上がっていきます

### 【twice.pyの実行1】
以下の順番でコマンドを実行してください
```
端末３  chmod +x twice.py
端末３  rosrun mypkg twice.py
端末３  vi twice.py           //ここで実行２の為にコードを書き換える
```
**rosrun mypkg twice.py**を実行すると**count.pyの実行**で得た数字を2倍にして表示します

**twice.pyの実行1**の時点ではtwice.pyのコードは以下のようになっています
```
import rospy
from std_msgs.msg import Int32

def cb(message):
    rospy.loginfo(message.data*2)

if __name__ == '__main__':
    rospy.init_node('twice')
    sub = rospy.Subscriber('count_up', Int32, cb)
    rospy.spin()
```

twice.pyを以下のコードに書き換える
```
#!/usr/bin/env python3
import rospy
from std_msgs.msg import Int32

n = 0

def cb(message):
    global n
    n = message.data*2

if __name__ == '__main__': 
    rospy.init_node('twice')
    sub = rospy.Subscriber('count_up', Int32, cb) 
    pub = rospy.Publisher('twice', Int32, queue_size=1) 
    rate = rospy.Rate(10)
    while not rospy.is_shutdown():
        pub.publish(n)
        rate.sleep()
```

### 【twice.pyの実行2】
以下の順番でコマンドを実行してください
```
端末３  rosrun mypkg twice.py
端末４  rostopic list        //以下の4つのトピックがあるか確認
/count_up
/rosout
/rosout_agg
/twice
端末４  rostopic echo /twice
```
**twice.pyの実行1**で得た数字の2倍の数字が表示されます


# 実演動画
[Youtube・課題2](https://youtu.be/CH7Q0QQwE90)

# License
BSD 2-Clause "Simplified" License

# 参考
https://ryuichiueda.github.io/robosys2020/lesson10_ros.html#/  
https://youtu.be/PL85Pw_zQH0

