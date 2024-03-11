# oracle-saved
一甲骨文官方调整硬盘扫描

sudo dd iflag=direct if=/dev/oracleoci/oraclevda of=/dev/null count=1
echo "1" | sudo tee /sys/class/block/`readlink /dev/oracleoci/oraclevda | cut -d'/' -f 2`/device/rescan

二甲骨文改密匙连接开启SSH为ROOT登录

sudo -i

echo root:NWezEgU |chpasswd root

sudo sed -i 's/^#\?PermitRootLogin.*/PermitRootLogin yes/g' /etc/ssh/sshd_config

sudo sed -i 's/^#\?PasswordAuthentication.*/PasswordAuthentication yes/g' /etc/ssh/sshd_config

sudo service sshd restart

三甲骨文救砖

lsblk 或 fdisk -l 命令查看分区

Ubuntu 20.04 ARM 官方原版完整救援包（恢复数据约46G，耗时约1个多小时）

wget --no-check-certificate https://github.com/honorcnboy/BlogDatas/releases/download/OracleRescueKit/Ubuntu20.04.arm.img.gz

用户名:root, 密码:CNBoy.org。

Ubuntu 20.04 AMD 官方原版完整救援包（恢复数据约46G，耗时约1个多小时）

wget --no-check-certificate https://github.com/honorcnboy/BlogDatas/releases/download/OracleRescueKit/Ubuntu20.04.amd.img.gz

用户名:root, 密码:CNBoy.org

使用 Ubuntu 20.04 ARM 官方原版完整救援包，命令如下：

gzip -dc /root/Ubuntu20.04.arm.img.gz | dd of=/dev/sdb

使用 Ubuntu 20.04 AMD 官方原版完整救援包，命令如下：

gzip -dc /root/Ubuntu20.04.amd.img.gz | dd of=/dev/sdb

使用 debian10 ARM 网络精简救援包，命令如下：

gzip -dc /root/dabian10.arm.img.gz | dd of=/dev/sdb

watch -n 5 pkill -USR1 ^dd$

备份制作一份 AMD / ARM 救援包

dd if=/dev/sdb | gzip > /root/own.img.gz

四科技lion自研的VPS集群控制系统

apt update -y  && apt install -y curl 

curl -sS -O https://kejilion.pro/kejilion.sh && chmod +x kejilion.sh && ./kejilion.sh

五甲骨文一键dd ubuntu20.04

bash <(wget --no-check-certificate -qO- 'https://raw.githubusercontent.com/MoeClub/Note/master/InstallNET.sh') -u 20.04 -v 64 -p NWezEgU382
