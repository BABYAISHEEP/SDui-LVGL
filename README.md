## 1. 项目说明

本项目的前身是作为本人的本科毕业设计，如今已经结束了相关流程，因此开源了此工程。

项目想法起源于各大平台都有调用stableDiffusion API的功能实现绘图，但是在嵌入式平台中却没有找到类似的项目(公开的)，由于本人对于Linux和LVGL的认知尚浅，因此想通过本项目提升技术。也因此，本项目有很多地方的代码并不高明，仅作为抛砖引玉的作用，也希望各位大佬可以迭代出更强大的版本！

代码逻辑解释：后续补上

## 2. 工程前期准备		

如果您阅读过百问网的相关代码，您会发现“**画板**”部分非常的相像：

API方面，如今已经有v3版本的接口，但是我使用的本地SD只有v1的版本。如果您在各大提供post等测试的平台看过v3接口的具体内容，其实具体细节的变化并不大，因此可以先研究最初始的，也可以触类旁通。

具体的v1接口示范：**http://你的IP:你的端口/docs**

网上也有相关的说明文档：

(v1)很详细：https://blog.csdn.net/Python_anning/article/details/135269356

(v1)有实操：https://zhuanlan.zhihu.com/p/624042359

(v2)：https://juejin.cn/post/7265666505101164603		https://cloud.tencent.com/developer/article/2359971

LVGL框架版本选择：本文撰写时已经有9.0.0版本，而互联网上很多文章可能还在用8.3.x甚至是7.x.x，此时并不需要惊慌，因为很多接口是通用的。当你使用一个函数，如果你的编译器会提供自动补全，而且有弹出相关的参数定义，那么您输入的函数大概率是可以使用的。但是不同版本的函数对参数的定义可能会不一样，因此这部分需要各位大佬自行解决。

前文提到我使用了百问网的画板接口，它并不兼容我的9.x.x版本，但是有取巧的方法：网上提供的接口为了稳定性，会在对应的头文件中加入版本控制的宏判断语句，对应的宏在框架的 有记录。因此我们只需要删除掉相关的接口判断语句即可，如果编译不通过再继续找问题。

## 3. 开发过程中的笔记

截图：fbgrab -d /dev/fb0 /home/cat/play/1.png

关闭图形显示：systemctl set-default multi-user.target

打开图形显示：systemctl set-default graphical.target

### 需要的库

**sudo apt install imagemagick**

负责处理PNG和BMP转换

用法 

PNG转BMP sprintf(command, "convert %s %s", input, output);

**sudo apt install coreutils**

负责BASE64与文件的转换

用法 编码到文件 sprintf(base64_decode, "base64 -d %s > %s", input, output);

用法 文件到编码 sprintf(command, "base64 -w 0 %s > %s", bmp_file, base_name);







TODO ...
