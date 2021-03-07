

# Prerequisites

- Install [esp-open-sdk][sdk]
- Install [esptool][esptool]
```sh
$ python3 -m pip install --user esptool
```



# Build RT-Thread

```sh
$ RTT_EXEC_PATH=/usr/local/esp-open-sdk/xtensa-lx106-elf/bin RTT_ROOT=../rt-thread scons
```



# Flash to NodeMCU

```sh
$ esptool.py --baud 230400 write_flash -fs 4MB -ff 80m \
0x00000 bin/boot_v1.7.bin 0x1000 rtthread.bin \
0x3FC000 bin/esp_init_data_default.bin 0x3FE000 bin/blank.bin
```


# Booot message

```
 ets Jan  8 2013,rst cause:2, boot mode:(3,7)

load 0x40100000, len 2592, room 16
tail 0
chksum 0xf3
load 0x3ffe8000, len 764, room 8
tail 4
chksum 0x92
load 0x3ffe82fc, len 676, room 4
tail 0
chksum 0x22
csum 0x22

2nd boot version : 1.7(5d6f877)
SPI Speed : 80MHz
SPI Mode : QIO
SPI Flash Size & Map: 32Mbit(512KB+512KB)
jump to run user1 @ 1000

OS SDK ver: 1.5.0-dev(caff253) compiled @ Oct 23 2017 17:42:20
pcName:ppT uxPriority:13 usStackDepth:2048
pcName:pmT uxPriority:1 usStackDepth:1024
phy ver: 1055_1, pp ver: 10.7

rf cal sector: 1019
pcName:tiT uxPriority:10 usStackDepth:2048
tcpip_task_hdl : 3fff19a0, prio:10,stack:512
pcName:uiT uxPriority:14 usStackDepth:2560
pcName:rtT uxPriority:12 usStackDepth:2048
SDK version:1.5.0-dev(caff253)
mode : softAP(f6:cf:a2:72:70:7c)
dhcp server start:(ip:192.168.4.1,mask:255.255.255.0,gw:192.168.4.1)
add if1
bcn 100
msh >version

 \ | /
- RT -     Thread Operating System
 / | \     4.0.3 build Mar  7 2021
 2006 - 2021 Copyright by rt-thread team
msh >help
RT-Thread shell commands:
free             - Show the memory usage in the system.
ps               - List threads in the system.
help             - RT-Thread shell help.
list_device      - list device in system
list_timer       - list timer in system
list_mempool     - list memory pool in system
list_memheap     - list memory heap in system
list_msgqueue    - list message queue in system
list_mailbox     - list mail box in system
list_mutex       - list mutex in system
list_event       - list event in system
list_sem         - list semaphore in system
list_thread      - list thread
version          - show RT-Thread version information
clear            - clear the terminal screen
```



[sdk]: https://github.com/pfalcon/esp-open-sdk
[esptool]: https://github.com/espressif/esptool
