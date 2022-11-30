
# 入门
AutoJs的工作原理是在一个Android App AutoJsX上内置了js引擎，js引擎实现了手机自动化的一套js api。在vs code上写js代码，然后通过局域网推送js代码到AutoJsX，这样就可以跑脚本了。降低了开发的门槛，因为js开发相对简单。下面介绍下环境搭建：
- 在开发手机/虚拟机上装[AutoJsX](https://github.com/ILG2021/AutoJsX/releases/tag/6.3.5) app
- 安装vs code[开发插件](https://marketplace.visualstudio.com/items?itemName=aaroncheng.auto-js-vsce-fixed)
- 下载[脚手架代码](https://github.com/kkevsekk1/webpack-autojs)，这步可以不需要，根据个人习惯。
- ctrl + shift + p 选择autojs启动服务，然后ipconfig查询电脑局域网ip，接着在手机上打开AutoJsX app，点击侧边栏最底下的“连接电脑”。这个时候vs code就会显示连接状态
- vs code写js代码，点击右上角运行按钮，或者按F5，js代码会推送到手机app并运行
- 开发完成之后，使用AutoJsX打包生成最终的产品app。点击js文件右边的三个点——更多——打包应用。多个文件的项目需要建立项目，[参考](/qa?id=如何把图片和脚本一起打包，或者打包多个脚本)

# 综述 <!-- {docsify-ignore-all} -->

由于原作者不再维护 [Auto.js](https://github.com/hyb1996/Auto.js)，我计划在原来4.1版本的基础上继续维护项目，并将原项目命名为 [AutoX.js](https://github.com/kkevsekk1/AutoX)。

欢迎更多开发者参与这个项目的维护与升级。

这篇文档里有加密相关的内容可能和实际运行情况有冲突，我会逐步完善更新，程序代码，尽可能保持一致。

AutoX.js 使用 JavaScript 作为脚本语言，目前使用 [Rhino 1.7.13](https://github.com/mozilla/rhino) 作为脚本引擎，支持 ES5 与部分 ES6 特性。

- 学习 AutoX.js 的 API 之前，建议先学习 JavaScript 的基本语法。
- 如果想要在电脑上开发 AutoX.js，可以使用 VSCode 以及 [AutoX.js 插件](https://marketplace.visualstudio.com/items?itemName=aaroncheng.auto-js-vsce-fixed)。
- 如果想要使用 TypeScript 来开发，目前有开发者公布了一个 [相关工具](https://github.com/pboymt/autojs-dev)。

# AutoX.js 的功能

- [x] AutoX.js 项目脚手架：结合 webpack vscode 插件，开发、编译、打包、部署、混淆、加密一体化 [文档资料](https://github.com/kkevsekk1/webpack-autojs)。(注意`--registry=https://registry.npm.taobao.org`是国内网址，国外开发不需要)
- [x] vscode 插件右键，自动提示操作等 [下载地址](https://marketplace.visualstudio.com/items?itemName=aaroncheng.auto-js-vsce-fixed)
- [x] vscode 自动补全、方法注释等 [文档资料](https://github.com/kkevsekk1/webpack-autojs)
- [x] 修复众多 bug，升级到 5.0.1 ,合并打包插件，升级配置文件等功能
- [x] 支持 WebSocket 

# 模块

本文档的章节大致上是以模块来划分的，总体上可以分成"自动操作"类模块（控件操作、触摸模拟、按键模拟等）和其他类模块（设备、应用、界面等）。

"自动操作"的部分又可以大致分为 [基于控件](/widgetsBasedAutomation) 和 [基于坐标](/coordinatesBasedAutomation) 的操作。

基于坐标的操作是通过指定具体的屏幕坐标，进行点击，例如 `click(100, 200)` 等，这种方式在游戏类脚本中比较有可行性，结合找图找色、坐标放缩功能也能达到较好的兼容性。但是，这种方式对于一般软件脚本不是很高效，而且需要安卓 7.0 以上或 root 权限才能执行。

软件类脚本（例如：批量添加联系人、自动提取短信验证码等等）我们推荐采用基于控件的模拟操作，结合通知、按键等达成更好的工作流。

其他模块主要包括：

- app: 应用。启动应用，卸载应用，使用应用查看、编辑文件、访问网页，发送应用间广播等。
- console: 控制台。记录运行的日志、错误、信息等。
- device: 设备。获取设备屏幕宽高、系统版本等信息，控制设备音量、亮度等。
- engines: 脚本引擎。用于启动其他脚本。
- events: 事件与监听。按键监听，通知监听，触摸监听等。
- floaty: 悬浮窗。用于显示自定义的悬浮窗。
- files: 文件系统。文件创建、获取信息、读写。
- http: HTTP。发送 HTTP 请求，例如 GET, POST 等。
- websocket: websocket 客户端、服务器端，可以进行主动推送消息
- images, colors: 图片和图色处理。截图，剪切图片，找图找色，读取保存图片等。
- keys: 按键模拟。比如音量键、Home 键模拟等。
- shell: Shell 命令。
- threads: 多线程支持。
- ui: UI 界面。用于显示自定义的 UI 界面，和用户交互。

除此之外，AutoX.js 内置了对 [Promise](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise) 的支持。


# 参与共建

[软件源码](https://github.com/ILG2021/AutoJsX)

[文档源码](https://github.com/ILG2021/AutoJsX-Docs)

本文档更新稍有滞后，某些模块文档并没写完，希望有开发者共同参与维护！

不用担心你不懂，我们可以讨论交流! 

欢迎大家 PR ，共同参与开源！
