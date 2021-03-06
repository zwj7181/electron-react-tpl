# electron-react-umi-tpl

[English Version](https://github.com/qld-cf/electron-react-tpl/blob/master/README_EN.md)


更新日志：

1. 2020-06-14 添加远程增量更新，无需下载包来重新安装更新；
[中文](https://github.com/qld-cf/electron-react-tpl/blob/master/CHANGE_LOG.md)
[English Version](https://github.com/qld-cf/electron-react-tpl/blob/master/CHANGE_LOG_EN.md)



`electron 8.2` + `umi 3.1` + `typescript react 16.12` + `redux` + `antDesign 4.0` + `eslint tslint react-tslint`脚手架, 下载即用，已经为你做好了基座设施

#### 客户端集成:
1. 自动更新(electron-builder)
2. 托盘菜单
3. app启动loading加载条
4. electron打印(electron 5.0以上支持)
5. 灰度发布方案
6. electron-log 本地日志
7. electron-store 本地存储
8. app打包图标

TODOLIST:  1. app崩溃信息采集
           2. app消息通知，快捷键等

#### web端:
1. 基于[umi](https://umijs.org/zh-CN)脚手架，基础配置已集成，开发者关注业务代码编写即可
2. 本地存储redux(redux-saga)
3. antDesign >= 4.0
4. iconfont图标

- 菜单配置 `src/layouts/menu/config.tsx`


TODOLIST:  1. node Api功能封装与渲染进程业务解耦


### 开启

```
npm i
npm start
npm run pack
```


### 目录树
```
|-- project
    |-- .editorconfig
    |-- .eslintrc.js
    |-- .gitignore
    |-- .gitlab-ci.yml
    |-- .prettierignore
    |-- .prettierrc.js
    |-- directoryList.md
    |-- package-lock.json
    |-- package.json
    |-- README.md
    |-- tsconfig.json
    |-- typings.d.ts
    |-- eslint-rules 自定义eslint配置
    |   |-- base.js
    |   |-- react.js
    |   |-- ts.js
    |-- src
        |-- main 主进程
        |   |-- app-update.yml 生产环境自动更新配置
        |   |-- bundle.js 自动生成
        |   |-- bundle.js.map
        |   |-- dev-app-update.yml 开发环境自动更新配置
        |   |-- index.js 入口
        |   |-- loading.html
        |   |-- preload.js
        |   |-- README.md
        |   |-- config 编译配置
        |   |   |-- config.js
        |   |   |-- webpack.config.js
        |   |-- controls 控制集
        |   |   |-- AppAutoUpdater.js
        |   |   |-- AppMainWindow.js
        |   |   |-- AppTray.js
        |   |   |-- electron-helper.js
        |   |-- print 打印
        |   |   |-- print.html
        |   |   |-- print.js
        |   |-- public 附件
        |   |   |-- icon.ico
        |   |   |-- icon.png
        |   |   |-- tray.png
        |   |-- script 编译脚本
        |       |-- build.js
        |-- render 渲染进程
            |-- .env
            |-- .umirc.ts
            |-- app.ts
            |-- global.less
            |-- README.md
            |-- .umi umi自动生成配置和插件等
            |   |-- umi.ts
            |   |-- core
            |   |-- plugin-dva
            |   |-- plugin-initial-state
            |   |-- plugin-model
            |   |-- plugin-request
            |-- api 接口集合
            |   |-- api.list.ts
            |-- assets 附件
            |   |-- image
            |   |   |-- yay.jpg
            |   |-- style
            |       |-- bootstrap-part.less
            |       |-- common.less
            |-- common 通用
            |   |-- enum.ts
            |   |-- global.ts
            |-- components 组件
            |   |-- readme.md
            |   |-- AutoUpdate
            |   |   |-- index.tsx
            |   |   |-- style.less
            |   |-- FormCps
            |   |   |-- index.tsx
            |   |   |-- readme.md
            |   |-- TableCps
            |       |-- index.tsx
            |       |-- readme.md
            |-- config 配置
            |   |-- iconfont.ts
            |   |-- menus.tsx
            |-- dist 本地打包生成文件
            |-- layouts 布局
            |   |-- index.less
            |   |-- index.tsx
            |   |-- header
            |   |   |-- index.less
            |   |   |-- index.tsx
            |   |-- loading
            |   |   |-- index.less
            |   |   |-- index.tsx
            |   |-- menu
            |       |-- index.less
            |       |-- index.tsx
            |-- mock
            |   |-- foo.ts
            |-- models redux
            |   |-- xxStore.ts
            |-- pages
            |   |-- home.normal.less
            |   |-- index.tsx
            |   |-- Foo 示例
            |   |   |-- index.tsx
            |   |   |-- components
            |   |   |   |-- TableList.tsx
            |   |   |-- models
            |   |   |   |-- foo.ts
            |   |   |-- services
            |   |       |-- foo.ts
            |   |-- Home 业务
            |       |-- Edge
            |       |   |-- index.tsx
            |       |-- Settings
            |           |-- index.tsx
            |-- utils 工具集

```

### eslint
默认开启[alloy](https://github.com/AlloyTeam/eslint-config-alloy)配置
`eslint-config-alloy`



### log

- 本地调试日志

```js
const log = require('electron-log');
// log.transports.file.file = 'xx/record.log' 本地可指定文件
// 默认日志存放
// on Linux: ~/.config/{appName}/log.log
// on macOS: ~/Library/Logs/{appName}/log.log
// on Windows: user\AppData\Roaming\{appName}\log.log
log.info('Hello, log');
log.warn('Some problem appears');
```

### 注意事项

1. 下载依赖和打包运行错误，请用cnpm或者配置npm config的electron ERROR路径
2. 任何地方的component文件夹名不可首字母大写 会被umi识别为路由而影响热加载等
3. 卡在node install.js : npm config edit 添加：electron_mirror="https://npm.taobao.org/mirrors/electron/"
4. 下载electron 8.2一直失败，请删除包，然后安装全局的8.2版本的electron即可

