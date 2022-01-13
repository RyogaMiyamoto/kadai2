# kadai2

# ロボットシステム学・課題２
課題２は プログラムです。  

# 概要
**echo 1 > /dev/myled0**と入力するとLEDが光ります。  
**echo 0 > /dev/myled0**と入力するとLEDが消えます。  

# 使用環境
- Raspberry Pi 3 Model B  
- Ubuntu 20.04 LTS

# 回路の情報
## 使用したもの  
- Raspberry Pi 3 Model B ×1


## 写真


# 操作方法
## 【インストールの方法】
```
git clone git@github.com:RyogaMiyamoto/kadai1.git
cd kadai1/  
make                    //コンパイル  
sudo insmod myled.ko  
sudo chmod 666 /dev/myled0
```
## LEDの点灯
### 【インストールの方法】のコマンドを実行後に以下のコマンドを実行
```  
echo 1 > /dev/myled0　　//LED点灯  
echo 0 > /dev/myled0　　//LED消灯
```

## fishの表示
### 【インストールの方法】のコマンドを実行後に以下のコマンドを実行
```   
cat /dev/myled0         //fishの表示  
```
**fish** が表示され続けるので、controlキーとCを同時に押すことでfish表示画面から抜け出すことができます

# 実演動画
[Youtube・課題2](https://youtu.be/CH7Q0QQwE90)

# License
