# dt_otp

嵌入式：动态令牌-dll & so实现库

这是 vs2010 cpp dll项目


/*****************************************
  Description: OTP动态令牌: DLL/SO动态链接库
  Authod     : EXP | http://exp-blog.com
  Modify By  : None
  Date       : 2015-07-20
******************************************/

===================================
动态链接库（dll/so）编译构建方法.

共需构建4个动态链接库:
1.dt_otp_x86.dll(win)
2.dt_otp_x64.dll(win)
3.dt_otp_x86.so(linux)
4.dt_otp_x64.so(linux)
===================================

```
Windows 环境编译构建（*.dll）:
	1. 安装VS2010 （默认只安装32位编译器，安装时必须同时选中64位编译器）
	2. 编译 win_86(dll):
		2.1. 选择编译器: 生成(Build) -> 配置管理器 -> 活动解决平台 -> Win32(默认)
		2.2. 右键项目 -> 属性 -> 配置属性 -> C/C++ -> 代码生成 -> 运行时库 -> 选MTD 
			(目的是把运行库静态编译进去，否则其他没装VC库的机器就跑不了了)
		2.3. 右键项目 -> 重新生成
		2.4. 在本项目的 ./dt_otp/Debug 目录下可找到 dt_otp.dll 文件, 此为 32位版本.
		2.5. 重命名为 dt_otp_x86.dll 以示区分.
	3. 编译 win_64(dll):
		3.1. 选择编译器: 生成(Build) -> 配置管理器 -> 活动解决平台 -> 新建 -> x64
		3.2. 右键项目 -> 属性 -> 配置属性 -> C/C++ -> 代码生成 -> 运行时库 -> 选MTD 
			(目的是把运行库静态编译进去，否则其他没装VC库的机器就跑不了了)
		3.3. 右键项目 -> 重新生成
		3.3. 在本项目的 ./dt_otp/x64/Debug 目录下可找到 dt_otp.dll 文件, 此为 64位版本.
		3.4. 重命名为 dt_otp_x64.dll 以示区分.

Linux 环境编译构建（*.so）:
	1. 安装64位Linux虚拟机（推荐Ubuntu）
	2. 安装 GCC 32和64 位环境 （默认64位系统只有64位GCC）
	3. 把项目 ./dt_otp/dt_otp 整个目录上传到 Linux 任意目录位置.
	4. 执行已编写好的脚本 sh make.sh, 将会自动编译、构建.
	5. 构建成功后 ./dt_otp/dt_otp 目录下会新增两个库文件 dt_otp_x86.so 和 dt_otp_x64.so
```