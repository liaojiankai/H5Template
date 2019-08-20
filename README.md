
## 项目构成
<pre>
├── build                        // webpack配置目录
│   ├── utils.js     		         // 工具文件
│   ├── config.js     		       // 配置文件
│   ├── webpack.config.base.js   // 基础构建
│   ├── webpack.config.dev.js    // 开发模式构建
│   ├── webpack.config.prod.js   // 生产模式构建
├── dist               		       // 生产目录
├── src                		       // 开发目录
├── .babelrc                		 // babel配置
├── .editorconfig                // editorconfig配置
├── .eslintignore                // eslint排除的检测范围
├── .eslintrc.js                 // eslint配置
├── postcss.config.js            // postcss配置
</pre>


## 使用说明

1. 克隆库到本地

2.  进入项目目录

3. 打开build/config.js文件根据自身要求进行自定义设置
```javascript
const config = {
  projectPath: utils.resolve('/'),                                  // 项目根目录
  srcPath: utils.resolve('/src/'),                                  // 源文件目录
  node_modulesPath: utils.resolve('/node_modules/'),                // node_modules目录

  htmlPath: utils.resolve('/src/'),                                 // HTML目录
  jsPath: utils.resolve('/src/main/'),                              // JS目录

  ignoreJs: ['test'],                                               // 没有入口js文件的html名
  assetsSubDirectory: utils.resolve('/src/static/'),                // 静态资源目录(不处理的第三方代码)

  dev: {
    host: 'localhost',
    port: '3002',

    useEslint: false,                                                // 是否使用ESlint
    showEslintErrorsInOverlay: true,                                 // 设置为true，ESlint-loader将始终返回警告。

    devSourceMap: false,                                             // 是否开启SourceMap
    devtool: 'eval-source-map',

    assetsPublicPath: '/',                                           // 相对于服务器根目录的路径，用于加载资源。

    proxyTable: {                                                    // proxy代理
      '/api': 'http://localhost:3000'
    }
  },

  build: {
    prodSourceMap: false,                                             // 是否开启SourcMap
    devtool: 'source-map',

    assetsRoot: path.resolve(__dirname, '../dist'),                  // 构建根目录
    assetsPublicPath: '/'                                            // 相对于服务器根目录的路径，用于加载构建好的资源。
  }
}
```
4. npm run build 构建dist生产目录

5. npm run dev   构建热更新服务

6. 开始进行开发
