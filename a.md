# Vue + UEditor #

## 1.放入静态资源并配置 ##

1. 首先把官网下载的Ueditor资源，放入静态资源src/static中。
2. 修改ueditor.config.js中的window.UEDITOR_HOME_URL配置





    import '../../static/UE/ueditor.config.js';
    import '../../static/UE/ueditor.all.min.js';
    import '../../static/UE/lang/zh-cn/zh-cn.js';
    import '../../static/UE/ueditor.parse.min.js';
