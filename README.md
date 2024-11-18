
## ESP VTX
基于WIFI-Broadcast原理的ESP32图传。

## 使用说明
### 天空端

### 地面站
- 需要一张能运行monitor模式的2.4G网卡，典型如ar9271 和 Pi(树莓派或各种国产派）
- 将ar9271插入地面站，通过ifconfig 可以看到此时多了一个网络接口
- 使用`sudo tcpdump --monitor-mode -i wlan1` 来测试当前系统和网卡是否支持monitor 模式，如果没有报错，且能正常dump数据，那么即为正常。注意将wlan1 换成你自己的接口名
- 编译地面站
    - 编辑gs/src/main.cpp,将rx_descriptor.interfaces 和 tx_descriptor.interface 更改为你自己的接口名
    - 安装依赖`sudo apt install libdrm-dev libgbm-dev libgles2-mesa-dev libpcap-dev libturbojpeg0-dev libts-dev libsdl2-dev libfreetype6-dev`
    - `cd gs; make`
    - 运行`sudo DISPLAY=:0 ./gs` , 注意DISPLAY有可能是:0.0
