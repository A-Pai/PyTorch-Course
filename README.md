# PyTorch-Course
系统、完整、全面地介绍PyTorch，基于Jupiter Notebook和html图文并茂，交互式探索。

Jupyter Notebook文件应该在VS Code中打开，需按照以下教程安装Live Server（Go Live）插件。

Live Server（Go Live）安装使用教程

引入：为什么在 ipynb 里打开 HTML，必须先在 VS Code 添加插件

我们要做的事：在 ipynb 的 markdown cell（或 HTML 输出）里放一个链接，点击后打开 ECOD图解.html。
这个链接是 http://127.0.0.1:5500/ECOD图解.html，http 地址背后必须有一个服务器提供文件；直接用 file:// 双击打开 html 会受浏览器跨域和相对路径限制，ipynb 里的 http 链接也无法指向本地文件。
所以必须在 VS Code 中添加相关插件 Live Server，由它在本地 5500 端口起一个静态服务器，ipynb 里的链接才有服务可连，点击才能打开。
第 1 步：安装插件

点左侧栏四个小方块图标，或快捷键：Windows Ctrl+Shift+X，Mac Cmd+Shift+X，打开扩展市场。
搜索框输 live server。
认准作者 Ritwick Dey、紫色波纹图标的那个，点 Install。
注意别装成 Live Server Preview、Five Server 等同名替代品。
安装完不用重启，右下角会出现 Go Live 按钮。
第 2 步：以文件夹方式打开 VS Code（关键）

用菜单 File → Open Folder（中文：文件 → 打开文件夹），选中存放ipynb 的项目目录，点「选择文件夹」。
不能只双击打开单个 html 文件：只开裸文件时没有工作区根，Live Server 的服务器根目录定位不稳，链接容易 404。
打开后检查：左侧资源管理器文件树顶部必须出现文件夹名称，下面是整棵目录树；如果只看到孤零零一个文件，说明打开方式错了。
快捷入口：欢迎页点 Open Folder；或在系统资源管理器右键文件夹 →「通过 Code 打开」（需安装时勾选了添加到 PATH）。
第 3 步：启动服务器

点右下角 Go Live，浏览器自动弹出页面。
启动成功后按钮文字变成 Port: 5500，表示服务跑在 5500 端口；再点一次即停止。
另一种启动方式：左侧文件树右键 ECOD图解.html → Open with Live Server，直接定位到该页面。
第 4 步：在 ipynb 里点链接，并用浏览器打开

保持 Go Live 亮起的状态，在 markdown cell 里放：
[👉 在浏览器打开 ECOD图解](http://127.0.0.1:5500/ECOD图解.html)
点击该链接，默认用系统默认浏览器打开。
点击后想指定浏览器：设置 workbench.externalBrowser，可填 chrome、edge、firefox 或 default。
workbench.browser.openLocalhostLinks 控制 127.0.0.1 链接的去向：保持 false 时点击走外部浏览器；改成 true 则在 VS Code 内部标签页打开。
可选设置（默认不用动）

Ctrl+, 打开设置，搜 Live Server 修改，或写进项目的 .vscode/settings.json。
liveServer.settings.port：端口，默认 5500。
liveServer.settings.host：绑定地址，默认 127.0.0.1。
liveServer.settings.root：服务器根目录，默认工作区根。
liveServer.settings.CustomBrowser：指定 Live Server 启动时用的浏览器，如 chrome，默认系统默认浏览器。
常见问题

点链接连不上：先确认 Go Live 已亮起、按钮显示 Port:5500；端口被占用时它会自动换到 5501，链接里的端口也要跟着改。
中文文件名 404：把链接里的中文做百分号编码，或直接把 html 改成英文名。
核心结论

逻辑链：ipynb 里的 http 链接需要本地服务器 → VS Code 添加 Live Server 插件 → Open Folder 建立根目录 → 点 Go Live → 点链接用浏览器打开。
文件夹根目录是前提，Go Live 是启动动作，顺序不能反。
