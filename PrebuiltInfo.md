# 预编译包说明 #

本预编译包的编译环境如下：

Windows XP SP3

Visual Studio 9.0.30729.1 (2008 SP1)

OpenSceneGraph 2.8.2

**如果您的操作系统或者开发环境不符合上述的要求，那么您将无法正常运行本预编译包的内容！**

本预编译包的生成过程中需要依赖一些第三方工程的动态和静态链接库，以生成对应的OSG插件文件。大部分的第三方工程使用与预编译包相同的工作环境生成，并同时具有Debug和Release两个版本；少数第三方工程的生成环境可能与本预编译包不符，作者通过基本的测试，认为它们可以工作于当前环境中，但是不保证所有的相关功能都能够运行正常。用到的第三方工程版本及其环境说明请见后文。

为了降低用户的下载负荷，本预编译包的所有内容被分离为可以取舍的多个文件，如下所示：
  * osg-core-2.8.2-release：核心功能库、头文件及常用插件的Release版本。
  * osg-core-2.8.2-debug：核心功能库、头文件及常用插件的Debug版本。
  * osg-extra-2.8.2-release：补充插件的Release版本。
  * osg-extra-2.8.2-debug：补充插件的Debug版本。
  * osg-examples-2.8.2-release：所有示例程序的Release版本。
  * osg-examples-2.8.2-debug：所有示例程序的Debug版本。
  * osg-data-2.8.2：测试和开发中常用的数据文件集。

所有的压缩包解压缩之后均会自动生成OpenSceneGraph-2.8.2文件夹，并在其中释放OSG开发所需的各种头文件，动态和静态链接库文件，以及应用程序。压缩包osg-core-2.8.2同时还会释放一个osg\_env.bat文件，用于简单的预编译包测试。

编辑osg\_env.bat，第一行：

`@set PROGRAM_PATH=C:\Program Files`

将这里的C:\Program Files修改为解压OSG时的父目录，例如E:\Projects；保存这个批处理文件。

双击执行osg\_env.bat，此时应当生成一个控制台窗口，下载Release版本的用户输入：

`# osgversion`

`# osgviewer cow.osg`

Debug版本的用户输入：

`# osgversiond`

`# osgviewerd cow.osg`

测试OpenSceneGraph预编译包的版本，以及一个基本的OSG程序能否正常执行。

之后，您可以参考osg\_env.bat中的内容，设置自己系统中的环境变量，并开始OSG程序的开发。如果您有任何问题，欢迎登陆[osgChina论坛](http://bbs.osgchina.org)，或者在[这里](http://code.google.com/p/osgenginebook/issues/list)向作者提问。

## osg-core-2.8.2 ##

本预编译包中包含了OpenSceneGraph-2.8.2的16个核心功能库文件，18个插件文件，10个OSG格式绑定插件，以及6个实用程序。它们足可以用于大部分情形下的OSG应用程序开发。

一些需要特别加以说明的动态库文件和插件如下表所示：

| **文件名** | **描述** | **地位** | **依赖关系** |
|:--------|:-------|:-------|:---------|
| OpenThreads | 多线程处理的功能实现 | 必需     | -        |
| osg     | 场景图形的核心功能实现 | 必需     | -        |
| osgAnimation | 各种场景动画效果的实现 | 部分插件需要 | -        |
| osgDB   | 场景数据读写处理的实现 | 必需     | -        |
| osgFX   | 简单场景特效的演示实现 | 部分插件需要 | -        |
| osgGA   | 用户交互漫游功能的实现 | 必需     | -        |
| osgManipulator | 场景对象交互控制操作的实现 | 部分插件需要 | -        |
| osgParticle | 场景粒子效果的实现 | 部分插件需要 | -        |
| osgShadow | 场景阴影效果的实现 | 部分插件需要 | -        |
| osgSim  | 常用仿真模拟功能的演示实现 | 部分插件需要 | -        |
| osgTerrain | 地形网格的处理实现 | 部分插件需要 | -        |
| osgText | 文字渲染的实现 | 必需     | -        |
| osgUtil | 场景管理和绘制的实用工具集 | 必需     | -        |
| osgViewer | 场景渲染的结果视景器 | 必需     | -        |
| osgVolume | 体渲染功能的实现 | 部分插件需要 | -        |
| osgWidget | 三维GUI控件和布局管理的实现 | 部分插件需要 | -        |
| osgdb\_curl | 网络地址解析与数据传输 | 网络功能需要 | curl     |
| osgdb\_freetype | 矢量字体的解析与绘制 | 文字渲染需要 | freetype |
| osgdb\_gif | GIF图像格式解析 | 可选     | libungif |
| osgdb\_jpeg | JPG图像格式解析 | 可选     | jpeg     |
| osgdb\_png | PNG图像格式解析 | 可选     | libpng   |
| osgdb\_tiff | TIF图像格式解析 | 可选     | libtiff  |

本预编译包所含的其它常用的数据格式插件如下所示：

模型：3ds ive obj openflight osg osga osgtgz

图像：bmp dds rgb tga

其它：glsl

以及osgdb\_osganimation等10个专用于.osg格式绑定的插件，它们可以辅助osgdb\_osg插件识别其他核心库的数据。

本预编译包所含的实用程序包括：

osg2cpp osgarchive osgconv osgfilecache osgversion osgviewer


## osg-extra-2.8.2 ##

本预编译包中包含了OpenSceneGraph-2.8.2的39个补充插件。它们的存在与否对于大部分OSG程序的开发和运行不会有太大影响，但是可以极大地丰富OSG对于各种数据格式的支持。一些需要特别加以说明的插件列表如下：

| **文件名** | **描述** | **依赖关系** |
|:--------|:-------|:---------|
| osgdb\_dae | Collada模型格式解析 | collada  |
| osgdb\_dicom | DICOM医学影像格式解析 | dcmtk    |
| osgdb\_exr | 高范围动态图格式解析 | openexr  |
| osgdb\_gdal | GDAL数据格式解析 | gdal     |
| osgdb\_jp2 | Jpeg 2000图像格式解析 | jasper   |
| osgdb\_ogr | OGR数据格式解析 | gdal     |
| osgdb\_pdf | PDF文档格式解析 | poppler  |
| osgdb\_svg | SVG图像格式解析 | librsvg  |
| osgdb\_vnc | VNC远程监控插件 | vncclient |

本预编译包所含的其它数据格式插件如下所示：

模型：3dc ac bsp dot dw dxf geo lwo lws md2 mdl shp stl txf txp x

图像：hdr pic pnm vtf

其它：bvh cfg gz logo normals rot scale tgz trans zip


## osg-examples-2.8.2 ##

本预编译包中包含了122个OSG的示例程序。


## 第三方工程版本说明 ##

本预编译包在生成过程中直接和间接用到的所有第三方工程如下表所示。您可以参考这个列表，自行使用其它版本的第三方库来重新生成某些插件；或者据此检查用户程序运行中可能出现的各种问题：

| **第三方库** | **被依赖关系** | **生成方式** |
|:---------|:----------|:---------|
| boost-1.40.0 | collada openvrml | 本机生成，动态库 |
| cairo-1.8.8 | pango librsvg poppler | 本机生成，静态库 |
| collada-dom-2.2 | **osgdb\_dae** | 本机生成，动态库 |
| curl-7.19.7 | **osgdb\_curl** | 本机生成，静态库 |
| dcmtk-3.5.4 | **osgdb\_dicom** | 本机生成，静态库 |
| expat-2.0.1 | fontconfig | 本机生成，静态库 |
| fontconfig-2.7.3 | cairo pango poppler | 本机生成，静态库 |
| freetype-2.3.10 | **osgdb\_freetype** fontconfig cairo pango poppler openvrml | 本机生成，静态库 |
| gdal-1.6.2 | **osgdb\_gdal** **osgdb\_ogr** | 本机生成，动态库 |
| gdk-pixbuf-0.22.0 | librsvg   | 本机生成，静态库 |
| glib-2.22.2 | pango gdk-pixbuf librsvg poppler | 直接获取，动态库 |
| glut-3.7.6 | **osgviewerGLUT** | 直接获取，动态库 |
| ilmbase-1.0.1 | **openexr** | 本机生成，动态库 |
| intl-0.14.4 | gdk-pixbuf | 本机生成，静态库 |
| jasper-1.900.1 | **osgdb\_jp2** | 本机生成，静态库 |
| jpeg-6b  | **osgdb\_jpeg** libtiff vncclient | 本机生成，静态库 |
| libpng-1.2.37 | **osgdb\_png** cairo dcmtk gdk-pixbuf poppler | 本机生成，静态库 |
| librsvg-2.26.0 | **osgdb\_svg** | 本机生成，静态库 |
| libtiff-3.8.2 | **osgdb\_tiff** | 本机生成，静态库 |
| libungif-4.1.4 | **osgdb\_gif** | 本机生成，静态库 |
| libxml2-2.6.30 | collada dcmtk librsvg poppler | 本机生成，静态库 |
| minizip-1.01 | collada   | 本机生成，静态库 |
| openexr-1.6.1 | **osgdb\_exr** | 本机生成，动态库 |
| pango-1.26.0 | librsvg   | 本机生成，静态库 |
| pcre-8.00 | **collada** | 本机生成，静态库 |
| pixman-0.16.2 | cairo     | 本机生成，静态库 |
| poppler-0.12.0 | **osgdb\_pdf** | 本机生成，静态库 |
| tinyxml-2.5.3 | collada   | 本机生成，静态库 |
| vncclient-0.9.2 | **osgdb\_vnc** | 本机生成，静态库 |
| zlib-1.2.3 | **osgdb\_zip** collada curl dcmtk libpng libtiff libvncclient minizip cairo gdk-pixbuf poppler openexr | 本机生成，静态/动态库 |

注：