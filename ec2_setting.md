## 最新のソフトウェアにアップデート
```
sudo yum update -y
```

## タイムゾーンの変更
```
sudo ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime
```

## /etc/sysconfig/clockの設定変更
```
cat << EOL | sudo tee /etc/sysconfig/clock
ZONE="Asia/Tokyo"
UTC=true
EOL

sudo reboot // 再起動
```

## 新規ユーザ作成
```
sudo useradd -G wheel deploy

grep wheel /etc/group // wheelグループのユーザ確認

echo 'group ALL = NOPASSWD: ALL' | sudo tee --append /etc/sudoers.d/cloud-init  // sudo su - deploy; sudo -sで確認する
```

