# turtle_sample2

## 概要
ROS2学習のためのturtlesimを用いたサンプルプログラム．
turtle_practiceパッケージを作成して，パッケージ確認順に沿って編集していくことでLaunch，Topic(publish,subscrive)，Service(client), Parameterの順で学べる

## ワークスペース作成
> mkdir -p ~/<ワークスペース名>/src     
> cd <ワークスペース名>     
> colcon build  
> source install/setup.bash

例：
> mkdir -p ~/turtle_ws/src     
> cd turtle_ws     
> colcon build  
> source install/setup.bash

## パッケージ作成
> cd ~/<パッケージを配置するフォルダ>   
> ros2 pkg create <パッケージ名> --build-type <ビルドタイプ> --node-name <ノード名> --dependencies <依存パッケージ>

例：
> cd ~/turtle_ws/src/turtle_sample2     
> ros2 pkg create turtle_practice --build-type ament_cmake --node-name turtle_practice --dependencies rclcpp std_msgs geometry_msgs turtlesim

## ビルド
> cd ~/<ワークスペース>  
> colcon build  
> source install/setup.bash

例：
> cd ~/turtle_ws  
> colcon build  
> source install/setup.bash

## 実行
> ros2 run <パッケージ名> <ノード名>

例：
> ros2 run turtle_practice turtle_plactice

## パッケージ確認順
1. turtle_publish
2. turtle_subscribe
3. turtle_client
4. turtle_parameter

## デバッグコマンド
### Node関係
* 起動しているNodeの確認
    > ros2 node list

* Nodeの詳細確認
    > ros2 node info

### Topic関係
* 存在するTopicの確認
    > ros2 topic list

* Topicの通信状況の確認
    > ros2 topic echo <topic名>

* Topicの詳細確認
    > ros2 topic info <topic名>

* Topicへ送信
    > ros2 topic pub <topic名> <topic通信の型> <通信データ>

### Service関係
* 存在するServiceの確認
    > ros2 service list

* Service通信の型の確認
    > ros2 service type

* Serviceへ送信
    > ros2 service call <service名> <service通信の型> <通信データ>

### Parameter関係
* Parameterの一覧確認
    > ros2 param list

* Parameterのセット
    > ros2 param set <node名> <parameter名> <設定値>

* Parameterの設定値確認
    > ros2 param get <node名> <parameter名>

* Parameterの保存
    > ros2 param dump <node名> > <保存ファイルへのパス>　   

    例：
    > ros2 param dump /turtle_control > ~/turtle_ws/wrc/turtle_sample2/turtle_control/config/params.yaml

### 通信の型関係
* 通信の型に含まれる変数の確認
    > ros2 interface show <通信の型>　

    例：
    > ros2 interface show geometry_msgs/msg/Twist

## フォルダ構成
~/turtle_ws     
　　/build　　　　# システムトラブル時は削除      
　　/include　　　# システムトラブル時は削除      
　　/src    
　　　　/<パッケージ>　　# パッケージは必ず/**_ws/src下に配置　   
　　　　　　/config　　　# parameterファイル置き場   
　　　　　　/launch　　　# launchファイル置き場　   
　　　　　　/src　　　　　#ソースファイル置き場　   
　　　　　　　　/<パッケージ名>.cpp     
　　　　/CMakeLists.txt     
　　　　/package.xml
