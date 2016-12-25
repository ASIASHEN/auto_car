# 树莓派小车
这是一个树莓派小车的项目，目标实现小车的自动行驶。
使用了：

+ python tornado框架
+ python socker编程
+ deep learning darknet框架

# 项目说明页面

[raspberrypi基于深度学习的自动避障智能小车_目录](http://www.findspace.name/easycoding/1819)

# 项目结构

```bash
.
├── car 
│   ├── cam_motion.py
│   ├── Car.py
│   ├── config.ini
│   └── socket_server.py
├── darknet
│   ├── a.py
│   ├── darknet
│   ├── data
│   │   └── labels
│   │       ├── 100.png
...
│   │       ├── 99.png
│   │       └── make_labels.py
│   ├── predictions.png
│   ├── run.sh
│   ├── test.jpg
│   ├── tiny-yolo.cfg
│   └── tiny-yolo.weights
├── Design.fzz
├── devlog.md
├── pc_control
│   ├── config.ini
│   └── control_client.py
├── README.md
└── web_server
    ├── config.ini
    ├── data
    │   └── labels
    │       ├── 100.png
...
    │       ├── 99.png
    │       └── make_labels.py
    ├── entry.py
    ├── predictions.png
    ├── static
    ├── templates
    │   └── cam.html
    └── test.jpg
```



`car/`目录是小车上运行的项目，`config.ini`文件需要自己参考`config_example.ini`新建。

`darknet`目录是深度学习框架所需文件，注意在`web_server`项目里还有个`data`文件夹，因为在通过web_server调用darknet时，运行目录是web_server，而darknet里面运行时需要一些参数和配置文件等，可以在darknet命令行参数里指定的可以直接写固定路径，但是有些是darknet里面固定的相对路径，队友没有修改，所以需要将部分内容copy过去。在github项目里，我去掉了，可以从data.zip里解压出来。

`Design.fzz`是设计图纸，用Fritzing打开

`devlog.md`是开发日志。

`pc_control`是手动控制的测试项目。

`web_server`则是运行在PC的server，`templates`文件夹是tornado框架所用的，里面的`cam.html`只是内嵌了moiton的页面。`test.jpg`是接收到的图片文件，`prediction.jpg`是darknet运行时产生的图片文件，用红框标出了识别出的物体。`config.ini`文件同理，仿照example新建即可。

在小车上运行时，如果是csi摄像头，一定要记得先`modporbe`加载到`/dev/video0`上去。

# 总结

整体来说，代码还是过于简陋了，最后实现的避障效果也很差。不过赶作业来说，足够了。后续还希望能继续优化。

欢迎勘误。