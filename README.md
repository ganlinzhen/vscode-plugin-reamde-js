### 项目创建
#### 1. 使用的是微软官方的项目模板 - vscode-generator-code
```
npm install -g yo generator-code
yo code
```
#### 2. 项目结构说明
##### 2.1 package.json 文件清单
* main： 入口文件
* activationEvents：扩展的激活事件
* contributes：贡献点，vscode插件大部分功能配置都在这里
##### 2.2 extension.ts 为入口文件
```javascript
const vscode = require('vscode');

/**
 * 插件被激活时触发，所有代码总入口
 * @param {*} context 插件上下文
 */
exports.activate = function(context) {
    console.log('恭喜，您的扩展“vscode-plugin-demo”已被激活！');
    // 注册命令
    context.subscriptions.push(vscode.commands.registerCommand('extension.sayHello', function () {
        vscode.window.showInformationMessage('Hello World!');
    }));
};

/**
 * 插件被释放时触发
 */
exports.deactivate = function() {
    console.log('您的扩展“vscode-plugin-demo”已被释放！')
};
```
#### 3.命令注册

```javascript
// extension.js
// 定义命令并返回
let disposable = vscode.commands.registerCommand('vsplugin.helloWorld', () => {
    // The code you place here will be executed every time your command is executed

    // Display a message box to the user
    vscode.window.showInformationMessage('Hello World from my-vs-plugin!');
})
// 注册命令
context.subscriptions.push(disposable);
```

[
		"onCommand:readme.helloWorld"
	],