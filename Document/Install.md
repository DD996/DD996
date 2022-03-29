# Install document

### Prerequisites

1. MITK-2018.4.0 link: https://www.mitk.org/download/releases/MITK-2018.04/

![image-20220329151643455](img\image-20220329151643455.png)

* 请下载源码的压缩包



2. CMAKE-3.12.1-win64-x64 link: https://github.com/Kitware/CMake/releases?page=12

![image-20220329151714349](img\image-20220329151714349.png)

* 下载对应的压缩包(即win64-x64)



3. QT-5.12.2 link: https://download.qt.io/official_releases/qt/5.12/5.12.2/qt-opensource-windows-x86-5.12.2.exe.mirrorlist

![image-20220329151849142](img\image-20220329151849142.png)

* 所给链接是镜像文件列表的链接，页面中会有很多文件链接，请找到截图中所示的镜像链接（CN专用的镜像链接，一般为高校的镜像。然后右键链接，复制链接，使用迅雷进行下载，浏览器下载速度可能过慢，请自行选择快速下载的方法）



4. Visual Studio 2017 community link: https://my.visualstudio.com/Downloads?q=visual%20studio%202017&wt.mc_id=o~msft~vscom~older-downloads

![image-20220329152755814](img\image-20220329152755814.png)

* 下载是免费的但需要注册用户，选择x64（理论上x86也可以，在后续的安装中会产生部分分歧）



### Install

1. 创建MITK文件夹并在其中创建MITK-src和MITK-build文件夹，将MITK源码解压到MITK-src中

   ![image-20220329154321934](img\image-20220329154321934.png)

   

2. 创建cmake文件夹并将cmake解压到该文件夹中

   ![image-20220329154408801](img\image-20220329154408801.png)

   

3. 创建QT文件夹，然后将QT的安装路径设置为该文件夹（安装QT也需要注册用户），安装过程中，只需要勾选以下的组件，其他非必要无需勾选

   ![image-20220329155231240](img\image-20220329155231240.png)

   ![image-20220329155242252](img\image-20220329155242252.png)

   * 其中MSVC可能需要按照位数修改，目前成功编译的结果选择了32-bit

     

4. Visual Studio 2017的安装只需要选择截图中的部分即可，其他选项非必要

   ![image-20220329160205282](img\image-20220329160205282.png)

   

5. 按照截图中的路径找到cmake-gui.exe

   ![image-20220329154443152](img\image-20220329154443152.png)

   

6. 然后在source code的路径中配置为MITK-src的路径，build the binaries的路径配置为MITK-build的路径

   ![image-20220329154610835](img\image-20220329154610835.png)

   

7. 在configure之前需要添加实体"CMAKE_PREFIX_PATH"，类型为path，值为QT的MSVC路径

   ![image-20220329155641482](img\image-20220329155641482.png)

   

8. 接着进行两次configure，不见红之后generate就能生成项目文件了

   ![image-20220329155805801](img\image-20220329155805801.png)

   * 生成器选择Visual Studio 2017

     

9. generate done表示已经成功生成项目文件，然后open Project即可在Visual Studio 2017中打开项目，接着对ALL_BUILD进行生成

   ![image-20220329160828465](img\image-20220329160828465.png)

   * 需要注意上述的平台为Debug Win32，前面QT如果安装的是32位，这里是win32的话应该不会在使用QT库的时候出现"X64与X86冲突"的错误，如果装了64位的话需要创建新的配置，配置平台X64，但是我尝试失败了就直接将QT重装成32位的

   

10. 由于该项目的源码还包括官方git仓库中的大量代码，需要联网下载代码，因此编译的时间很长。同时可能因为网络问题连接不上git，请找人白嫖代理或者自己购买代理。修改git代理的命令可以在网上简单找到。接着会遇到一个最繁琐的问题，可能会提示某些文件生成失败，在输出里面会提示字符标准不对，请找到错误列表查看是哪个文件的错误，然后按照后续给出的链接中的视频方式来另存为文件。win10的记事本可能找不到Unicode，只需要选择UTF-16 LE就可以了，这两标准据说一样，亲测可行。

* 视频连接: https://www.bilibili.com/video/BV1Bs411F7eS
* 字符标准的知乎回答: https://www.zhihu.com/question/386822566/answer/1185195182
