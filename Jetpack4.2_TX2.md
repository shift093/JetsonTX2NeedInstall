### 安裝指南

#### 準備

兩台PC
一台TX2
一台螢幕支援hdmi
一台自動DHCP分享器
兩條網路線(TX2、主機需要同一個網域底下)


#### 步驟一

下載jetpack到主機(ubuntu16.04)
https://developer.nvidia.com/embedded/downloads

apt更新
```
sudo apt update
sudo apt grade
```

#### 步驟二

```
# 先在主機安裝sdk manager
cd Dowloads
ls ./sdk...(tab)
sudo apt install ./skdmanager...(tab)
# run
skdmanager
```

#### 步驟三

登入後
a.選擇 host+tx2
b.打勾,同意
c.等待安裝,flash(~ Insatalling... 50%)
  c1.過程如果跳出視窗需要(manual)手動重置tx2
  c2.長按power強制關機tx2,拔電源線,重新接上開機,按recovery兩秒接著按reset放開後,等兩秒再放開recovery
  c3.`lsusb`查看是否usb有抓到`Nvidia Cropertion`==tx2板子
d.主機:用其他電腦VNC遠端控制主機(只有一個螢幕的方法)
螢幕接TX2(這時候已經安裝好TX2的OS了，會有畫面)
tx2:設定帳號密碼等等...結束後
登入TX2`ifconfig`查TX2虛擬IP(待會要在主機那邊登入TX2，以便安裝SDK檔案)
取得ip後到主機這邊輸入ip及帳密，開始安裝SDK

註：主機有安裝opencv會衝突，導致TX2安裝過程computer vision會Error

#### 步驟四

設定VNC 的 server, nvidia官方用`vino`
```
# 安裝常用套件
sudo apt install ssh vino 

# 設定VNC 桌面遠端(desktop sharing) -> 
  * 預設為disable所以需要再設定
    * 
    * ![image](https://github.com/shift093/JetsonTX2NeedInstall/blob/master/jetson_setup.png)
```
