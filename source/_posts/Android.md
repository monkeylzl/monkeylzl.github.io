---
title: Android
date: 2017-03-08 09:40:01
tags: Android
---
Android环境的搭建主要有三个部分：JDK，IDE，SDK
#### JDK
由于Android的主题部分采用的是Java语言，所以首先进行Java环境的配置
1. 下载JDK，官网下载地址[http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html]()，选择相应的JDK。  
<center>
![](https://raw.githubusercontent.com/monkeylzl/MarkdownPhotos/master/AndroidEnvironmentBuilding/JDK.png)
</center>  
安装过程中可以自定义路径，这里以"D:\Java\jdk1.8.0_101"和"D:\Java\jre1.8.0_101"为例，注意安装路径中不要出现中文或者是空格，等待安装完。
JDK=Java Development Kit，Java开发工具集，主要包括JRE和编译器组件。是进行Java开发的必要环境。所以安装JDK就包括JRE的安装。JDK是JRE的完全超集。
JRE=Java Runtime Environment，Java运行时环境，主要提供运行Java Class的环境。JDK中本身包含JRE。如果只想运行Java程序，而不需要进行编译（非开发环境，生产环境），可以安装JRE，不用安装JDK。
JVM=Java Virtue Machine，Java虚拟机。Java是一种半编译半解释程序，.java源程序经过编译后生成字节码文件.class文件。JVM虚拟机就是一个虚拟的计算机专门用来运行Java程序的虚拟计算机。JVM虚拟机会在安装JRE的时候自动安装
2. 配置环境变量  
我的电脑->属性->高级系统设置->环境变量,配置JAVA_HOME，PATH，CLASSPATH。  

**用户变量**  
- 变量名：JAVA_HOME，  
变量值：D:\Java\jdk1.8.0_101（填写自己的安装路径）  

- 变量名：Path  
 变量值：D:\Java\jdk1.8.0_101\bin  
注意：原来Path变量中有的变量值不要覆盖，直接将D:\MyEclipse\Java\jdk1.8.0_101\bin放在最前面，最后加分号进行隔离  

 **系统变量**  
- 变量名：CLASSPATH  
变量值：.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;  
注意：最前面的点不要忘记，JAVA_HOME是java安装目录,但要加上2个%比如%JAVA_HOME%系统才能识别  
<center>
![](https://raw.githubusercontent.com/monkeylzl/MarkdownPhotos/master/AndroidEnvironmentBuilding/variable.png)
</center>  

3. 配置成功之后，运行cmd（win+R），测试java和javac命令，出现如图所示表示配置成功。
<center>
![](https://raw.githubusercontent.com/monkeylzl/MarkdownPhotos/master/AndroidEnvironmentBuilding/cmdjava.png)
</center>   
<center>
![](https://raw.githubusercontent.com/monkeylzl/MarkdownPhotos/master/AndroidEnvironmentBuilding/cmdjavac.png)
</center>

- 可以运行java -version命令查看自己的JDK版本,确定java version版本与文件夹D:\Java\jdk1.8.0_101一致，位数与自己电脑的一致。    
<center>
![](https://raw.githubusercontent.com/monkeylzl/MarkdownPhotos/master/AndroidEnvironmentBuilding/JavaVersion.png)
</center>
#### IDE
**Android Studio的安装**
- 下载[Android Developer官网](https://developer.android.com/studio/index.html)
- 安装时按照提示即可，安装过程中会提示SDK的安装路径，**注意一定不要包含空格等特殊字符**
- 第一次打开会出现如下情况  
<center>
![](https://raw.githubusercontent.com/monkeylzl/MarkdownPhotos/master/AndroidEnvironmentBuilding/problem.png)
</center>  
为了避免，可以在第一次运行AS时要在D:\Android\Android Studio\bin\idea.properties中添加
disable.android.first.run=true即可

#### SDK
- 在安装Android Studio时刻会安装SDK，但是需要更多的Android版本时，需要打开SDK Manager下载，此时需要进行翻墙，可以进行如下设置，选择Tools->options,进行下图的设置，一定要勾选Force...  
<center>
![](https://raw.githubusercontent.com/monkeylzl/MarkdownPhotos/master/AndroidEnvironmentBuilding/Internet.png)
</center>  
设置完之后，选择Packages->Reload，即可下载更新
<center>
![](https://raw.githubusercontent.com/monkeylzl/MarkdownPhotos/master/AndroidEnvironmentBuilding/Reload.png)
</center>
