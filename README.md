#ME 游戏框架 for nlua
<b>ME_Unity3D-NLua是一个基于unity+nlua技术的全LUA免费开源（带有资源下载功能）游戏框架</b>

基于https://github.com/Mervill/Unity3D-NLua

整理：小陆(QQ2604904) 参与者：顶梁猪(QQ756500), html5solo

##框架目标

<b>使用lua 编写2D,3D全平台运行游戏，一次编写，到处发布</b>

##核心思路
ME框架的思路就是 一个GameObject 对应挂个LuaBehaviour.cs脚本，这个LuaBehaviour.cs脚本DoFile一个lua脚本，lua脚本和LuaBehaviour.cs和GameObject都可以交互控制。

各各GameObject间通过Lua 消息进行通信。

框架附带打地鼠游戏截图:

![](demo.jpg)

##安装说明
Assets/Engine 为本框所有架核心代码，其它请和 https://github.com/Mervill/Unity3D-NLua 保持一致.

Assets/Engine 为本框所有架核心代码

Assets/Atlas 将要打包的ui图片

Assets/Builds 将要打包的预置物

Assets/Data 为资源输出目录和lua脚本目录，此文件夹将被压缩为zip放入Assets/StreamingAssets

Assets/StreamingAssets 为zip更新包输出目录，在执行ME Tools 菜单相关选项生成后，请把一份上传到wwwroot服务器目录内，供客户端下载更新。

Assets/Engine/Scene/Demo.unity  为测试场景

wwwroot目录为web服务器目录，请上传到您的web服务器 请修改version内json参数,status： 0 无更新，1有更新包;force 1强制更新,0不强制更新,downrul 更新包路径

首次运行工程(Assets/Engine/Scene/Demo.unity),程序从 StreamingAssets 中复制资源文件data.zip并解压到可读目标目录，然后从这可读目标目录加载主入口文件main.lua 执行,框架所有逻辑全部尽可能在lua端执行 。如：在lua中进行版本检测，下载zip，解压覆盖以后每次运行，会检测远程服务器版本，如果有更新，则下载，并自动解压覆盖资源目录。

##打包编译设置
在BuildSetting里，iOS的"Scripting Define Symbols"需要设置为：
    UNITY_IPHONE;UNITY_3D;USE_KERALUA;LUA_CORE;CATCH_EXCEPTIONS
安卓为：
    UNITY_ANDROID;UNITY_3D;USE_KERALUA;LUA_CORE;CATCH_EXCEPTIONS

##特性：
1)全lua代码编写游戏。

2)unity3d editor编辑器负责可视化资源的创建和打包。

3)使用内置ugui来做UI甚至游戏。

4)热更新更彻底：可通过热更新来更新成不同类型的游戏。

5)通过纯lua“打地鼠”小游戏实战来提高框架的实用性.


##地鼠游戏资源打包以及编辑脚本测试使用帮助

1.执行编辑器菜单 ME tools/清理缓存,让一切重新开始.

2.执行编辑器菜单 ME tools/把Atlas目录下的.png图片作为图集资源并放入Data目录.

3.在Project窗体内 鼠标点选选中 Assets/Builds/GUI,然后 执行编辑器菜单 ME tools/独立打包选中目录下的各个对象并放入Data目录

4.执行编辑器菜单 ME tools/制作更新包：把Data目录压缩为一个zip包并放入StreamingAssets目录

通过以上步骤完成资源和升级包的制作了。

如果在编辑器进行代码修改或者资源修改，请重复以上步骤。

如果仅仅修改 Assets/Data/lua 下的逻辑脚本，您只需要执行以上的1和4步骤。


##更新历史:

//------------- now -----------------

更多更新请同步 https://github.com/lulersoft/ME_NLua

//-------------2015-2-1--------------- 版本 0.0.2

(1)添加Lua事件中心 AddListener|RemoveListener|Broadcast 可传table参数,彻底解耦

(2)修改为全局共用一个lua state，据说能提高效率和节省不必要的开销。。。

(3)添加Lua 异步下载 封装

(4)添加Lua 异步HTTP请求 封装

(5)添加Lua 定时器

(6)添加Lua 协程

(7)添加“打地鼠”游戏demo

(8)添加资源总管（哈希表管理资源)

(9)移除ngui,改用ugui

//-------------2015-1-18--------------- 版本 0.0.1

带zip资源生成和下载发布


