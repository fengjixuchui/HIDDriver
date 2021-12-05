虚拟鼠标键盘驱动程序，使用驱动程序执行鼠标键盘操作。</br>
注意这个驱动目前使用的是测试证书，还没有微软颁发的正式证书，只能在win 10测试模式下执行。</br>


一、项目编译：</br>
建议使用Visual Studio 2019；</br>


二、驱动安装：</br>
1、关闭签名校验，开启调试模式：</br>
在win10中，管理员模式的命令行中，执行如下命令：</br>
bcdedit /set nointegritychecks on</br>
bcdedit /set testsigning on</br>
然后重启win10，进入测试模式</br>

2、使用devcon安装驱动，最好先关闭360等杀毒软件：</br>
cd G:\workspace_github\loki-hidriver\x64\Debug\KMDFDriver</br>
& "D:/Windows Kits/10/Tools/x64/devcon.exe" find "root\hidriver"</br>
& "D:/Windows Kits/10/Tools/x64/devcon.exe" remove "root\hidriver"</br>
& "D:/Windows Kits/10/Tools/x64/devcon.exe" install hidriver.inf "root\hidriver"</br>

3、安装驱动的日志文件，可以在这里检查驱动安装的明细日志：</br>
%windir%\\inf\\setupapi.dev.log</br>
C:\Windows\INF\setupapi.dev.log</br>


三、项目来源：</br>
目前只是针对win10做些兼容性调整，主体代码来源于loki-hidriver项目，感谢原开发者：</br>
https://github.com/hedgar2017/loki-hidriver</br>
