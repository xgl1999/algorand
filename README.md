# algorand install script

1、安装依赖

sudo apt update
sudo apt install libsodium-dev

2、下载安装文件

mkdir ~/inst
cd ~/inst

下载 install_stable_linux-amd64.tar.gz 文件

-解压

tar -xf install_stable_linux-amd64.tar.gz

-运行

./update.sh -i -c stable -p ~/node -d ~/node/data -n

-如果您在尝试下载更新时遇到错误：

sudo apt install ca-certificates

再试  ./update.sh -i -c stable -p ~/node -d ~/node/data   一次

看到 algrand install 成功 提示。

cd ~/node

./goal logging enable -n MeaningfulHostName

<MeaningfulHostName> 使用你的节点名

./goal logging

-启动节点！

./goal node start -d data

-查看 节点运行 如果它输出一个数字（进程ID），那么algod正在运行

pgrep algod


-通过运行carpenter实用程序来查看协议活动,打印日志

./carpenter -file data/latest.log


-查看节点状态

./goal node status -d ~/node/data


-新建用户

./goal account new -d ~/node/data


-增加 全局变量

vim .bashrc 

export ALGORAND_DATA=/root/node/data


-启动停止命令

./goal node start

./goal node stop
