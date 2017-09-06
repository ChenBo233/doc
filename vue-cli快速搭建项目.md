# vue-cli 快速搭建项目 #

1. 安装node.js
2. 基于node.js,利用淘宝npm镜像安装相关依赖 --- 在cmd里直接输入：npm install -g cnpm --registry=https://registry.npm.taobao.org ，回车，等待安装...
3. 安装全局vue-cli脚手架,用于帮助搭建所需的模板框架 --- 在cmd里 1)输入：cnpm install -g vue-cli，回车，等待安装...  2).输入：vue，回车，若出现vue信息说明表示成功
4. 创建项目 --- 在cmd里输入：vue init webpack vue_test(项目文件夹名) ， 选择配置项后完成
5. 安装依赖 --- 在cmd里  1).输入：cd vue_test（项目名），回车，进入到具体项目文件夹 2).输入：cnmp install，回车，等待一小会儿 --- 回到项目文件夹，会发现项目结构里，多了一个node_modules文件夹（该文件里的内容就是之前安装的依赖）
6. 启动测试环境 npm run dev --- 构建正式环境为 npm run build

## vuejs ui 库: ##

1. mint-ui 移动端
2. element 饿了么PC端
3. iview PC端

## http请求组件 ##

1. axios
2. resource

## 安装插件 ##
npm i name -s(写入配置文件)
