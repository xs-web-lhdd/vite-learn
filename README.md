vite

###### 安装：

```bash
npm init @vitejs/app
```

然后 vite 会询问包名称（默认是 vite-project）,然后会让你选择一个框架（vue React 等），这里默认选 vue，然后询问选 vue 还是 vue-TS，在这里选 vue，然后 vite 就会构建一个基础的 vue 项目，下面是项目目录：

```bash
vite-project
  public
  src
    assets
    components
    App.vue
    main.js
  .gitignore
  index.html
  package.json
  vite.config.js
```

但这个基础项目是不能运行的，因为没有安装包依赖，因此运行前需要先安装包依赖：

```bash
npm install
```
安装完成之后```npm run dev```即可运行，但有时可能会爆这样一个错误：
```bash
events.js:292
      throw er; // Unhandled 'error' event
      ^

Error: spawn C:\Users\LiuHao\Desktop\vite\vite-project\node_modules\esbuild\esbuild.exe ENOENT
    at Process.ChildProcess._handle.onexit (internal/child_process.js:269:19)        
    at onErrorNT (internal/child_process.js:465:16)
    at processTicksAndRejections (internal/process/task_queues.js:80:21)
Emitted 'error' event on ChildProcess instance at:
    at Process.ChildProcess._handle.onexit (internal/child_process.js:275:12)        
    at onErrorNT (internal/child_process.js:465:16)
    at processTicksAndRejections (internal/process/task_queues.js:80:21) {
  errno: -4058,
  code: 'ENOENT',
  syscall: 'spawn C:\\Users\\LiuHao\\Desktop\\vite\\vite-project\\node_modules\\esbuild\\esbuild.exe',
  path: 'C:\\Users\\LiuHao\\Desktop\\vite\\vite-project\\node_modules\\esbuild\\esbuild.exe',
  spawnargs: [ '--service=0.12.21', '--ping' ]
}
```
不要慌，执行```node node_modules/esbuild/install.js```然后再执行```npm run dev```即可


vite中可以使用sass、less等css预处理器，但是需要安装sass、less这些依赖



vite的配置文件：
有一个vite.config.js
```js
import { defineConfig } from 'vite'  // 用来提示
import vue from '@vitejs/plugin-vue' // 官方配置---使用vue

// https://vitejs.dev/config/
export default defineConfig({
  server: {
    host: 'localhost',
    port: 8080
  },
  plugins: [vue()]
})

```

使用webpack时会进行重新编译，需要花费好几秒，但使用vite几乎就是秒开，很快，vite想必webpack并不是功能强了多少，而是vite的开发体验太好了！！！

vite VS Vue-Cli:
1、vite在开发模式下不需要打包可以直接运行，使用的是ES6的模块化加载规则
2、vue-cli开发模式下必须对项目打包才可以运行
3、vite基于缓存的热更新
4、vue-cli基于webpack的热更新

总结：
    快速编译、按需编译、模块热更新
  
哔哩哔哩教程：https://www.bilibili.com/video/BV15K4y1T7Nj?p=4&spm_id_from=pageDriver
掘金相关介绍： https://juejin.cn/post/6992200385561624607#heading-0
              https://juejin.cn/post/6913812233382264846
              https://juejin.cn/post/6910014283707318279#heading-21