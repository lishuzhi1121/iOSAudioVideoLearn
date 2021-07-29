# FFmpeg-iOS编译笔记
适用于 iOS 的 ffmpeg 静态库编译记录

## 1. 编译

下载该目录中的编译脚本 `FFmpeg-iOS-build-script` 如下图：

![FFmpeg-iOS-build-script](https://raw.githubusercontent.com/lishuzhi1121/oss/master/uPic/2021/07/29-111838-dEpTlk.png)

编译脚本默认编译的ffmpeg版本是4.3.1，如果需要编译其他版本可修改 `build-ffmpeg.sh` 中开头的 `FF_VERISON`。

执行编译脚本 `build-ffmpeg.sh` ，耗时根据网络等因素大概10-20分钟吧，最终结果将保存在 `FFmpeg-iOS` 这个目录中。

## 2. 集成测试

新建一个iOS App工程项目，以 `FFmpegiOSDemo` 为例，将编译结果 `FFmpeg-iOS` 整个文件夹拷贝到项目目录中，如下图：

![FFmpeg-iOS](https://raw.githubusercontent.com/lishuzhi1121/oss/master/uPic/2021/07/29-113300-dRgbWv.png)
**由于git单个文件不能超过100M的大小，所以本项目中把拷贝过来的文件进行了压缩，使用时需要先解压缩。**

在Xcode中打开工程项目，将刚刚拷贝过来的 `FFmpeg-iOS` 拖到工程里，如下图：
![add-file](https://raw.githubusercontent.com/lishuzhi1121/oss/master/uPic/2021/07/29-113752-YJRb9M.png)

弹窗中选择如下：
![copy](https://raw.githubusercontent.com/lishuzhi1121/oss/master/uPic/2021/07/29-113840-c3AFl7.png)

添加系统依赖库：
![lib](https://raw.githubusercontent.com/lishuzhi1121/oss/master/uPic/2021/07/29-114208-bj4dKY.png)

> libz.tbd
> libbz2.tbd
> libiconv.tbd
> CoreMedia.framework
> AVFoundation.framework
> VideoToolbox.framework
> AudioToolbox.framework

添加Library Search Path：
![Library](https://raw.githubusercontent.com/lishuzhi1121/oss/master/uPic/2021/07/29-114556-jx85b4.png)

添加Header Search Path（注意是recursive的）：
![Header](https://raw.githubusercontent.com/lishuzhi1121/oss/master/uPic/2021/07/29-122003-ptNcdK.png)

运行测试：
![code](https://raw.githubusercontent.com/lishuzhi1121/oss/master/uPic/2021/07/29-122304-V58EiP.png)
