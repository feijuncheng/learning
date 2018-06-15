## node版本
node版本>=6.11.5，建议
将package.json中
```
  "engines": {
    "node": ">=6.11.5" 
  }
```

## mode 配置
prod生产环境和dev开发环境的配置添加mode属性
```$xslt
module.exports = {
  mode: 'production'
};
```

```$xslt
module.exports = {
  mode: 'development'
};
```

## 公共模块调整

webpack4摒弃了原来的
`webpack.optimize.UglifyJsPlugin`、
`CommonsChunkPlugin`、
将它合并到了`optimization`中

需要单独安装`uglifyjs-webpack-plugin`插件

## css处理
用`mini-css-extract-plugin`替换`ExtractTextWebpackPlugin`

## 更新所有loader包
一些loader包会报错，比如eslint-loader等

## 关于替换中的一些报错记录

```
compilation.mainTemplate.applyPluginsWaterfall is not a function
```
重装了最新版本的`html-webpack-plugin`解决了这个问题

现在已经能打出部分js包了， 
但是出现了一个新问题：

有一个第三方包在js中操作dom添加了link标签

然后 `mini-css-extract-plugin`报错了，` document is not defined`

todo