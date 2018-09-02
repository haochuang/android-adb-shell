# android-adb-shell

some Android adb shell, which we used for android developing.


* # Android adb常用命令

在进行调试的时候,对我们的工作有帮助，提高效率,可以常翻常用.

* 1.查看最上层成activity名字:

```
  adb shell dumpsys activity | findstr "mFocusedActivity" 
```
 或者 

```
  adb shell dumpsys window w | findstr \/ | findstr name=
```

* 2.查看Activity的任务栈：

```
  adb shell dumpsys activity activities
```

* 3.显示所有的activities的信息,包括任务栈等:
	
```
  adb shell dumpsys activity
```

* 4.查看Android应用包名package和入口activity名称 ：
```
 aapt dump badging E:\apk\es3.apk
```

* 5.显示accounts信息:

```
  adb shell dumpsys account
```

* 6.显示CPU信息 :

```
  adb shell dumpsys cpuinfo
```
* 7.查看CPU使用信息

```
  adb shell top -n 1 -d 0.5 | findstr proc_ id
```

* 8.显示键盘，窗口和它们的关系

 ```
  adb shell dumpsys window
 ```

* 9.当我们需要知道设备的分辨率时

 ```
  adb shell dumpsys window displays
 ```

* 10.查看UI绘制的各个层级信息

```
  adb shell dumpsys SurfaceFlinger
```

* 11.显示wifi信息

```
  adb shell dumpsys wifi
```

* 12.电量信息及CPU 使用时长

 ```
  adb shell dumpsys batteryinfo $package_name
 ```

* 13.获取安装包信息

```
  adb shell dumpsys package packagename
```

* 14.每个应用的启动次数和时间

```
  adb shell dumpsys usagestats
```

* 15.显示状态栏相关的信息

```
  adb shell dumpsys statusbar
```

* 16.强制关闭一个应用程序；

 ```
  adb shell am force-stop <PACKAGE>
 ```
* 17.查看内存信息

```
  adb shell cat proc/meminfo
 ```

* 18.查看可输入的设备

 ```
  adb shell getevent -p
```
* 19.获得特定设备的输入信息

 ```
  adb shell getevent /dev/input/event0
 ```

* 20.点击

 ```
  adb shell input tap x y
 ```

* 21.发送按键

```
  adb shell input keyevent 82(keycode)
 ```

* 22.输入文本

```
  adb shell input text XXXX
 ```
  
* 23.查看报名中包含mobileqq的进程

 ```
  adb shell ps | findstr mobileqq
 ```
  
* 24.远程进程ID

```
  adb jdwp
 ```
  
* 25.获取序列号
 
 ```
  adb get-serialno
 ```
  
* 26.重启到bootloader，即刷机模式

```
  adb reboot bootloader
 ```
  
* 27.重启到recovery，即恢复模式

```
  adb reboot recovery
 ```
  
* 28.获取机器MAC地址：

 ```
  adb shell  cat /sys/class/net/wlan0/address
 ```
  
* 29.获取CPU序列号

 ```
  adb shell cat /proc/cpuinfo
 ```
  
* 30.覆盖安装（保留数据和缓存文件，重新安装apk）

```
  adb install -r <apkfile>
 ```
  
* 31.安装apk到sd卡

 ```
  adb install -s <apkfile>
 ```
  
* 32.卸载app但保留数据和缓存文件

```
  adb uninstall -k <package>
 ```
  
* 33.查看设备cpu和内存占用情况

 ```
  adb shell top
 ```
  

* 34.查看占用内存前6的app

```
  adb shell top -m 6
 ```
  
* 35.刷新一次内存信息，然后返回

```
  adb shell top -n 1
 ```
  
* 36.查询各进程内存使用情况

```
  adb shell procrank
 ```
  
* 37.查看指定进程状态

```
  adb shell ps -x [PID] 
 ```
  
* 38.查看后台services信息

 ```
  adb shell service list 
 ```
  
* 39.查看当前内存占用（该方式只能得出系统整个内存的大概使用情况） 车 如果你想查看所有进程的内存使用情况

 ```
  adb shell procrank
 ```
  
* 40.查看IO内存分区

 ```
  adb shell cat /proc/iomem
 ```
  
* 41.查看wifi密码

```
  adb shell cat /data/misc/wifi/*.conf
 ```
  
* 42.清除log缓存

 ```
  adb logcat -c
 ```
  
* 43.查看设备信息

```
  adb shell cat /system/build.prop
 ```
  
* 44.跑monkey

```
  adb shell monkey -v -p your.package.name 500
 ```
  
* 45.列出目标设备上安装的所有app的包名

```
  adb shell pm list packages
 ```
  
* 46.截屏命令：

```
  adb shell screencap -p /sdcard/screen.png
 ```
  将截屏文件拉到本地

```
  adb pull /sdcard/screen.png
 ```
  删除截屏文件

```
  adb shell rm /sdcard/screen.png
 ```
  
* 录制手机屏幕,视频格式为mp4,存放到手机sd卡里，默认录制时间为180s：

 ```
  adb shell screenrecord
 ```

* 限制视频录制时间为10s,如果不限制,默认180s:

```
  adb shell screenrecord  --time-limit 10 /sdcard/demo.mp4
```

* 指定视频分辨率大小:

```
  adb shell screenrecord --size 1280*720 /sdcard/demo.mp4
```

* 指定视频的比特率:

 ```
  adb shell screenrecord --bit-rate 6000000 /sdcard/demo.mp4
```

* 在命令行显示log:

```
  adb shell screenrecord --time-limit 10 --verbose /sdcard/demo.mp4
```

* 47.设置.获取属性信息

```
  adb shell getprop [key]
```

* 设置属性
```
  adb shell setprop [key] [value]
```

* 监听系统属性的变化，如果期间系统的属性发生变化则把变化的值显示出来

```
  adb shell watchprops
```

* 48.adb logcat 每一条日志消息都有一个标记和优先级与其关联。

 （1）标记是一个简短的字符串，用于标识原始消息的来源 (例如"View" 来源于显示系统)。优先级是下面的字符，顺序是从低到高：

	* V — 明细 (最低优先级)

	* D — 调试

	* I — 信息

	* W — 警告

	* E — 错误

	* F — 严重错误

	* S — 无记载 (最高优先级，没有什么会被记载)

* （2）查看过滤日志

 ```
  adb logcat ActivityManager:I *:S
 ```

 *:S 用于设置所有标记的日志优先级为S，可以确保输出符合指定的过滤器设置的一种推荐的方式，这样过滤器就成为了日志输出的“白名单”

* 显示所有优先级大于等于“warning”的日志

```
  adb logcat *:W
```

* （3）日志消息在标记和优先级之外还有很多元数据字段，这些字段可以通过修改输出格式来控制输出结果， -v 选项加上下面列出的内容可以控制输出字段：

	* brief — 显示优先级/标记和原始进程的PID (默认格式)

	* process — 仅显示进程PID

	* tag — 仅显示优先级/标记

	* thread — 仅显示进程：线程和优先级/标记

	* raw — 显示原始的日志信息，没有其他的元数据字段

	* time — 显示日期，调用时间，优先级/标记，PID

	* long —显示所有的元数据字段并且用空行分隔消息内容

	* 使用 thread 输出格式

```
  adb logcat -v thread
```

* （4）Android日志系统为日志消息保持了多个循环缓冲区，而且不是所有的消息都被发送到默认缓冲区，要想查看这些附加的缓冲区，可以使用-b 选项，以下是可以指定的缓冲区：


	* radio — 查看包含在无线/电话相关的缓冲区消息

	* events — 查看事件相关的消息

	* main — 查看主缓冲区 (默认缓冲区)

	* 查看radio缓冲区


```
  adb logcat -b radio
```

* 48.打印应用程序的log

```
  adb logcat -b main -v time>app.log
```

* 49.打印射频相关的log，SIM STK也会在里面，modem相关的ATcommand等，当然跟QXDM差的很远了

```
  adb logcat -b radio -v time> radio.log
```

* 50.打印系统事件的日志，比如触屏事件

```
  adb logcat -b events -v time
```

* 51.tcpdump 是很有用的，对于TCP/IP协议相关的都可以使用这个来抓

```
  adb shell tcpdump -s 10000 -w /sdcard/capture.pcap
```

* 52.状态信息，里面包含有dmesg，dumpstate和dumpsys

```
  adb bugreport>bugreport.log
```

* 53.kernel的log凡是跟kernel相关的，比如driver出了问题（相机，蓝牙，usb，启动，等等吧）

```
  adb shell dmesg > ldmesg_kernel.log
```

* 54.dumpstate是系统状态信息，里面比较全，包括手机当前的内存信息.cpu信息.logcat缓存，kernel缓存等等 。

```
  adb shell dumpstate
```

* 55.关于系统service的内容都在这个里面

```
  adb shell dumpsys
```

* 56.显示内存信息
```
  adb shell dumpsys meminfo system
```

* 57.删除包相关的所有数据(数据和缓存)

```
  adb shell clear <packageName>
```

* 58.输出安装包的 apk 路径

```
  adb shell pm path <packages>`
```
 
* 59.内存信息（meminfo package_name or pid 使用程序的包名或者进程id显示内存信息）

 ```
  adb shell dumpsys meminfo
 ```

* 60.得到com.haochuang.test进程使用的内存的信息    

```
  adb shell dumpsys meminfo com.haochuang.test
```

* 61.磁盘相关信息

```
  adb shell dumpsys diskstats
```

* 62.电池相关信息

```
  adb shell dumpsys battery
```

* 63.显示Alarm信息

```
  adb shell dumpsys alarm
```

* 64.统计系统耗电量

```
  adb shell dumpsys batterystats
```

* 65.设置线程的优先级

```
  adb shell dumpsys activity|grep oom_adj 
```
  
* 66.指定进程内存地址映射

```
  adb shell cat proc/pid/maps
```

* 67.指定进程内存详细使用信息

```
  adb shell cat proc/pid/smaps
```

* 68.VSS. RSS. PSS. USS 信息

```
  adb shell procrank
```

* 69.指定进程VSS. RSS. PSS. USS 详细信息

```
  adb shell procmem pid
```
