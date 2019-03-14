
## webpack开发环境与生产环境的区别 

  webpack.config.js本质上是一个 JS 文件，可以在文件里写 JavaScript 业务逻辑，通过读取环境变量 NODE_ENV 来判断当前执行打包任务是应用于开发环境（dev）还是生产环境（production），但是都混写在根目录下的 webpack.config.js文件中，需要通过很多零散的 if...else 来“临时”决定某一个 plugin 或者某一个 loader 的配置项，webpack.config.js文件变得很越冗长，代码的可读性和可维护性也大大下降。
  
### 开发环境
    NODE_ENV 为 development
    启用模块热更新（hot module replacement）
    额外的 webpack-dev-server 配置项，API Proxy 配置项
    输出 Sourcemap

### 生产环境
    NODE_ENV 为 production
    将 React、jQuery 等常用库设置为 external，直接采用 CDN 线上的版本
    样式源文件（如 css、less、scss 等）需要通过 ExtractTextPlugin 独立抽取成 css 文件
    启用 post-css
    启用 optimize-minimize（如 uglify 等）
    中大型的商业网站生产环境下，是绝对不能有 console.log() 的，所以要为 babel 配置 Remove console transform
    
    注意：在开发环境下启用了HMR，是为了让样式的修改也同样能被热替换，如果使用 ExtractTextPlugin 转为随 JS Bundle 一起输出，就不能热更新了
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  参考：https://zhuanlan.zhihu.com/p/29161762
