# 日常工作流脚手架

<p align="left">
  <a href="https://www.npmjs.com/package/generator-worker"><img src="https://img.shields.io/npm/v/generator-worker.svg?style=flat-square" alt="Build Status"></a>
  <a href="https://www.npmjs.com/package/generator-worker"><img src="https://img.shields.io/npm/dt/generator-worker.svg?style=flat-square" alt="Downloads"></a>
  <a href="https://github.com/qqw78901/generator-worker"><img src="https://img.shields.io/travis/qqw78901/generator-worker.svg?style=flat-square" alt="Build Status"></a>
</p>

## 开发背景 

进入团队不久，便抽时间做了在一个打包期间动态插入script的htmlwebpackPlugin，地址：[html-webpack-insert-script-plugin](https://www.npmjs.com/package/html-webpack-insert-script-plugin)
随后一周并不满足于这个插件，希望每一次开发自动带上这个插件（直到1.6版本才发npm的就知道当时是并没有发包的想法的），并且希望每一次开发时智能生成当前所需要业务的代码文件结构，作为一个懒人，为解决“万事起头难”这一痛点，便再利用空余时间给自己开发了一套脚手架

##项目简介

脚手架功能

- 具体业务功能打开来看
- 设置host功能


模板特性：
 - 兼容ie8，会处理loose
 - 带lint和precommmit，不合规范的js代码禁止commit
 - 自带有asset（隔壁同事介绍用的一个会计算图片大小的post-css插件）
 - 图片合并雪碧图插件
 - 手游带有rem计算的属性（目前已用px2rem替代）
 - js，css发布地址可配置，静态资源img地址分开配置

该脚手架具有以下模板 

- common  一个单，多页面的模版
    - 页游（2.x版本统一称为common）
    - 端游（2.x版本统一称为common）
    - 手游（2.x版本统一称为common）
- mobile-simple 移动端单页面 不使用js框架，适合小页面
- mobile-vue 移动端vue页面


### 安装项目

```text
npm install yo generator-worker -g
//or
yarn global add yo generator-worker

可以直接安装本代码库
npm install generator-worker -g
也可以在yeoman里搜索安装worker库

```

### 使用

```text
yo worker
```

###更新记录

- v1.1.1 修正多项配置
- v1.2.1 修改util.scss，加入gitignore，增加.xxxx,无文件名文件的克隆 
- v1.3.1 做完年度盛典活动后，把其中尝试用的eslint加入代码 
- v1.3.2 默认注释掉eslint生成的html输出报告，防止误抛线上 
- v1.4.1 大改动，将webpack1改成webpack3,加入设置host的功能 
- v1.4.2 host太烦了，默认关掉，不给乱配 
- v1.4.3 babel配置加上loose 
- v1.4.4 babel配置抽出成.babelrc 
- v1.4.5 修改多项配置 
- v1.5.1 更新依赖到支持node8的版本，主要是node-sass 
- v1.5.2 改改配置 
- v1.6.1 根据日常工作需要更新下配置，尝试发到npm上试试 

抽出时间整理前段时间比较多做的移动端业务对此做出大调整，于是乎有了2.x版本

- v2.1.0 大调整，出于移动端需要，把原来的模板统一归为common，为vue和react框架以及adcenter工作流做准备，加入browserlist，拆分postcss等多项重大修改
- v2.1.3 发包调整fixbug npmignore问题
- v2.1.4 兼容npmignore
- v2.2.1 大调整common模板：调整三款业务的sdk到新版，顺便升级webpack到4.0，切换雪碧图插件到内部都用的spritesmith（虽然觉得原来那个好用），去除各自项目引入htmlinsertplugin，改为引入包html-webpack-insert-script-plugin，同上，改./zip为引入包dist-zip，添加precommit
- v2.3.1 添加获取ip，修改业务中的防劫持称呼为新业务规范---耗时上报全局变量
- v2.3.2 默认开启htmlinsertplugin,开启npm
- v2.3.3 关闭npm
- v2.4.0 升级common html-webpack-insert-script-plugin依赖包,修改mobile-simple为依赖dist-zip等两款包，小整理后加入mobile-vue,但未测试过 对没装yarn的环境的支持
- v2.4.1 fix bug
- v2.5.0 改改mobile-vue
- v2.5.1 precommit bug fixed
- v2.5.2 fix deploy command bug,增加readme以便说明deploy的使用需要开启两个进程这一个情况
- v2.5.3 common模板 增加proposal-class-propertie：对class内使用箭头函数（proposal-class-propertie）的babel默认支持 
- v2.5.4 mobilevue模板：微调配置，common模板修复deploy配置 
- v2.6.0 全线模板添加HtmlWebpackCheckSourcePlugin，包版本使用最新，common模板，关闭jsbeautify,配置host变量改成dev.yy.com 
- v2.7.0 核心配置添加userName为模板做准备，改业务防劫持文件夹命名为耗时上报，该修改仅测试common模板，未覆盖新模板；修复appname横杠变空格问题；common模板：配置host变量改回ip,去除openbrowser插件，补充readme样例，打包后代码注释添加userName，默认注释雪碧图插件，跟随html-webpack-check-source-plugin的api扩展添加配置open
- v2.7.1 fix bug


###TODO

- common模板对es7的async 、ts的支持，common模板考虑添加autoprefixer
- 对没装yarn的环境的支持[done]
- 最近的业务做了一个项目同时运行移动版和pc版的，即改进文件夹结构，改进配置，对手机版应用px2rem、autoprefixer，而pc版正常，所以计划添加一个新模板--[新模板-多端]
- vue默认装上router，注释逻辑代码
- folder js to entry