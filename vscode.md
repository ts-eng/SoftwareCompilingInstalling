# vscode打开服务器上的项目
* 在本地安装Remote Development插件  

# vscode cmake编译
* 在服务器上安装C++，CMake和CMake Tools插件  
* vscode底部会出现CMake编译模式(Debug/Release/...)、编译工具、构建目标、运行目标等选择工具，选择对应的工具使用即可  

# vscode gdb调式
* 按下ctrl+shift+D打开“运行和调试”面板，点击“创建launch.json文件”创建launch.json文件，此时“configurations”为空.  
* 在打开的launch.json页面，点击“添加配置”，此时“configurations”后面弹出菜单，选择“C/C++： (gdb)启动”，自动填充“configurations”.  
* 更爱“program”和“args”. ${workspaceFolder}是工程目录(.vscode所在目录).  
