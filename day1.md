1: vue-cli脚手架初始化项目
前提：node + webpack + 淘宝镜像

脚手架目录介绍
node_modules文件夹：存放项目依赖

public文件夹： 一般放置一些静态资源（图片），需要注意，放在public文件夹中的静态资源，webpack进行打包，会原封不动打包到dist文件夹中。

src文件夹（程序员源代码文件夹）：
    assets文件夹：一般也是放置静态资源（一般放置多个组件共用的静态资源），需要注意，放置在assets文件夹里面静态资源，在webpack打包的时候，webpack会把静态资源当做一个模块，打包到JS文件里面。

    components文件夹：一般放置的是非路由组件（或者全局组件）

    App.vue: 唯一的根组件，Vue当中的组件（.vue）
    main.js: 程序入口文件，也是整个程序当中最先执行的文件

.gitignore: git上传时忽略的文件

babel.config.js: 配置文件（babel相关，可理解为一个翻译官，把es6的语法翻译为es5语法，让兼容性更好）

package.json文件：类似于身份证，记录了本项目的信息，如：项目名称，项目依赖有哪些，项目怎么运行

package-lock.json文件：缓存性文件 （可删除）

README.md：文档说明文件

2:项目的其他配置

2.1 项目运行起来的时候，让浏览器自动打开
---package.json
  "scripts": {
    "serve": "vue-cli-service serve --open",
    "build": "vue-cli-service build",
    "lint": "vue-cli-service lint"
  },

2.2 eslint校验功能关闭
---在根目录下，创建一个vue.config.js
比如：声明变量但是没有使用eslint校验工具报错

2.3 src文件夹简写方法，配置别名为  @

jsconfig.json配置别名@提示  【@代表的是src文件夹，这样将来文件过多，找的时候方便很多】
{
    "compilerOptions": {
        "baseUrl": "./",
        "paths": {
            "@/*": ["src/*"]
        }
    },
    "exclude": ["node_modules","dist"]
}

3 项目路由的分析
vue-router
前端所谓路由： KV键值对
Key: URL (地址栏中的路径)
value: 相应的路由组件
注意：项目上中下结构

路由组件：
Home首页路由组件、Search路由组件、login登录路由
非路由组件：
Header【首页、搜索页】
Footer【在首页、搜索页】，但是在登录、注册页面是没有的

4. 完成非路由组件Header与Footer业务
在咱们项目中，不再以HTML + CSS 为主，主要搞业务、逻辑
在开发项目的时候：
1: 书写静态页面（HTML + CSS）
2: 拆分组件
3：获取服务器的数据动态展示
4：完成相应的动态业务逻辑

注意1：创建组件的时候，组件结构 + 组件的样式 + 图片资源
注意2：咱们项目采用的less样式，浏览器不识别less样式，需要通过less,less-loader进行处理less,
      把less样式变为css样式，浏览器才可以识别
注意3：如果想让组件识别less样式，需要在style标签的身上加上lang=less
4.1使用组件的步骤（非路由组件）
-创建或者定义
-引入
-注册
-使用