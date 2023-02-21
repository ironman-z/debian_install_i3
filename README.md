#### Debian i3wm安装配置

###### 1.安装必需驱动和X环境
    
        apt install -y xserver-xorg-input-evdev xserver-xorg-input-kbd \
                    xserver-xorg-input-mouse firmware-linux-nonfree

        电脑的显卡有关驱动
        虚拟机：xserver-xorg-video-vesa和xserver-xorg-video-vmware
        A卡，xserver-xorg-video-ati
        N卡，xserver-xorg-video-nvidia
        A卡和N需要安装闭源驱动才可以驱动，安装方法请参考Debian可的官方wiki

###### 2.安装i3wm

        apt install -y i3 zsh vim sakura lightdm ttf-wqy-zenhei
    
###### 3.其他软件包和管理工具

        apt install -y xcompmgr sudo fcitx fcitx-rime feh midori \
                    network-manager-gnome volumeicon-alsa pulseaudio \
                    pavucontrol xorg lxappearance rofi  firmware-sof-signed \
                    pulseaudio-module-bluetooth blueman xautolock lxinput \
                    i3lock-fancy firmware-iwlwifi mate-power-manager xinput \
                    picom mate-utils

###### 软件包和管理工具说明

    xcompmgr 用来实现窗口透明
    fcitx 输入法
    feh 图片查看器，可以用来设置桌面背景
    mate-power-manager 电源管理
    network-manager-gnome 网络管理
    volumeicon-alsa 音量控制工具
    pulseaudio 声卡驱动
    pavucontrol 配置声音
    firmware-sof-signed 英特尔 SOF 音频固件
    firmware-intel-sound
    xorg 需要里面的xrandr来做相关配置
    lxappearance 用来调节gtk主题和字体
    rofi 可以配置成程序启动器用来代替默认的dmenu
    firmware-iwlwifi WiFi
    pulseaudio-module-bluetooth 蓝牙驱动
    xautolock 自动锁屏
    lxinput 轻量鼠标键盘管理
    xinput 触摸板
    copyq 剪切板管理器
    mate-utils 截图工具

#### 蓝牙配置

        SAP代表SIM Access Profile，必须禁用
        vi /etc/systemd/system/bluetooth.target.wants/bluetooth.service
        ExecStart=/usr/lib/bluetooth/bluetoothd --noplugin=sap
        
        systemctl daemon-reload
        systemctl restart bluetooth.service
        
        解除阻止
        apt install rfkill
        rfkill unblock all
        
        蓝牙管理工具
        apt install blueman

#### 触控板配置

        xinput list
        xinput list-props 11
        xinput set-prop 11 357 1 2 1 0
        xinput set-prop 11 361 1
        
#### 某些特定硬件上安装、配置

        https://wiki.debian.org/InstallingDebianOn/Acer/Aspire%205%20A515-56
