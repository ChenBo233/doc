# Vue + UEditor #

## 1.放入静态资源并配置 ##

1. 首先把官网下载的Ueditor资源，放入静态资源src/static/UE/中。
2. 修改ueditor.config.js中的window.UEDITOR_HOME_URL
     window.UEDITOR_HOME_URL = "/static/UE/"

## 2.引入 ##

     import '../../static/UE/ueditor.config.js';
     import '../../static/UE/ueditor.all.min.js';
     import '../../static/UE/lang/zh-cn/zh-cn.js';
     import '../../static/UE/ueditor.parse.min.js';

## 3.开发组件 ##
创建组件：src/components/UEditor.vue
     <template>
       <div>
         <script id="editor" type="text/plain"></script>
       </div>
     </template>
     <script>
       export default {
         name: "UE",
         data () {
           return {
             editor: null,
             config: {
               enableAutoSave: false //关闭自动保存，1.4.3.3版本中尚未实现（不知道咋回事），需要自己去修改一下ueditor.all.js中的源码autosave
               ...//其他配置参数请阅读官方api文档
             }
           }
         }，
         mounted () {
           //新注册一个按钮（ex:重写单图上传）
           UE.registerUI('imgUpload', (editor, uiName) => {
             //创建一个button
             var btn = new UE.ui.Button({
               name: uiName,
               title: '插入图片',
               cssRules: 'background-position: -381px 0;',
               onclick: _ => {
                 //执行插入图片事件
                 editor.execCommand( 'insertimage', {
                   src: "图片路径",
                   width: "图片宽度",
                   height: "图片高度"
                 });
               }
             });
             return btn;
             // 初始化UE
             this.editor = UE.getEditor('editor', this.config);
             this.editor.addListener("ready", _ => {
               this.editor.setContent("内容");
             }); 
           }
         }
       }
     </script>

## 4.使用组件 ##

当我们需要使用富文本编辑器时，直接调用公共组件即可

     js: 
       import UE from '@/components/UEditor';
       export default {
         components: {
           UE
         }
       }
     template:
       <UE></UE>

## 5.注意事项 ##

1. 由于要防范xss攻击，编辑器会过滤掉大部分标签的属性，要是想取消过滤，需要在ueditor.config.js内修改白名单whiteList（很多时候报获取不到某个属性的错误基本上都是这个原因），另外可以设置section的class和style加入白名单，之后就可以像微信公众号内的编辑器一样从其他第三方公众号编辑器复制样式过来了。
2. 顺便推荐另一个比较简单好用的vue富文本编辑器QuillEditor
