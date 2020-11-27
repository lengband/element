## Q
1. 文档里面的icon是一个一个写死的吗？
2. src/index.js 是手动引入包进行加载的嘛？


# 解析 `yarn build:file`

### node build/bin/iconInit.js
1. 读取 `packages/theme-chalk/src/icon.scss`
2. 判断如果是icon则生成文件`examples/icon.json`
3. 在`examples/entry.js`里面引入`examples/icon.json`
4. 挂载到`Vue.prototype.$icon`上
5. 在文档页面，以中文举例`examples/docs/zh-CN`文件中会循环$icon动态生成图标


## node build/bin/build-entry.js
> 目的是根据 `components.json` 动态生成 `src/index.js` 文件
1. 提前写死一些动态的模板，如 `IMPORT_TEMPLATE`、`INSTALL_COMPONENT_TEMPLATE`、`MAIN_TEMPLATE`
2. 引入 `components.json` 并循环它得到各个组件的数据
3. 把得到的数据通过`json-templater/string`动态渲染进上面的模板
4. 把生成在内存中的template写入磁盘
