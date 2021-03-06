## 常见问题

<details>
<summary>给组件绑定的事件为什么无法触发？</summary>

在 Vue 2.0 中，为**自定义**组件绑定**原生**事件必须使用 `.native` 修饰符：
```html
<my-component @click.native="handleClick">Click Me</my-component>
```

从易用性的角度出发，我们对 `Button` 组件进行了处理，使它可以监听 `click` 事件：
```html
<el-button @click="handleButtonClick">Click Me</el-button>
```

但是对于其他组件，还是需要添加 `.native` 修饰符。
</details>

<details>
<summary>如何在 Table 组件的每一行添加操作该行数据的按钮？</summary>

使用 inline-template 即可：
```html
<el-table-column label="操作" inline-template>
  <el-button @click.native="showDetail(row)">查看详情</el-button>
</el-table-column>
```
参数 `row` 即为对应行的数据。
</details>

<details>
<summary>Tree 组件的 `render-content` 和 Table 组件的 `render-header` 怎么用？</summary>

请阅读 Vue 文档 [Render Function](http://vuejs.org/v2/guide/render-function.html) 的相关内容。注意，使用 JSX 来写 Render Function 的话，需要安装 `babel-plugin-transform-vue-jsx`，并参照其[文档](https://github.com/vuejs/babel-plugin-transform-vue-jsx)进行配置。
</details>

<details>
<summary>如何使用第三方图标库？</summary>

只要修改第三方图标库的前缀（具体方法参阅第三方库的文档），并编写相应的 CSS，即可在 Element 中像使用内置图标一样使用第三方图标。例如，将第三方库的前缀改为 `el-icon-my`，然后在其 CSS 文件中添加：
```css
[class^="el-icon-my"], [class*=" el-icon-my"] {
  font-family:"your-font-family" !important;
  
  /* 以下内容参照第三方图标库本身的规则 */
  font-size: inherit;
  font-style:normal;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
```
具体使用时，和 Element 内置的图标用法一样。比如在 `el-input` 中：
```html
<el-input icon="my-xxx" />
```
</details>

<details>
<summary>你们的文档怎么偷偷更新了？</summary>

我们只会在 Element 发布新版本时同步更新文档，以体现最新的变化。详细的更新内容可以查看 [changelog](https://github.com/ElemeFE/element/blob/master/CHANGELOG.zh-CN.md)。
</details>

<details>
<summary>在项目中引入 Element，但是 CSS 报错/字体文件报错/组件没有样式是什么原因？</summary>

请参考我们提供的 [starter kit](https://github.com/ElementUI/element-starter)，在 webpack 的 loaders 中正确配置 file-loader、css-loader 和 style-loader。此外，我们还提供了基于 [cooking](https://github.com/ElementUI/element-cooking-starter) 和 [laravel](https://github.com/ElementUI/element-in-laravel-starter) 的项目模板。
</details>

<details>
<summary>将 Element 克隆至本地，运行时为何会报错/跑不起来？</summary>

首先，确保克隆的是 master 分支的最新代码，并且文件完整。其次，确保本地的 node 版本在 4.0 以上，npm 版本在 3.0 以上。最后，可以启动开发环境：

```bash
npm run dev
```

或是直接打包：

```bash
npm run dist
```
</details>

## FAQ

<details>
<summary>Why are my event listeners not working?</summary>

In Vue 2.0, adding **native** event handlers in **custom** components requires a `.native` modifier:
```html
<my-component @click.native="handleClick">Click Me</my-component>
```

For the sake of usability, we processed `Button` so it can listen to `click` events:
```html
<el-button @click="handleButtonClick">Click Me</el-button>
```

For other components, the `.native` modifier is still mandatory.
</details>

<details>
<summary>How do I add buttons in each row of Table to operate data of that row?</summary>

Just use `inline-template`:
```html
<el-table-column label="Operations" inline-template>
  <el-button @click.native="showDetail(row)">Details</el-button>
</el-table-column>
```
The parameter `row` is the data object of corresponding row.
</details>

<details>
<summary>How do `render-content` of Tree and `render-header` of Table work?</summary>

Please refer to [Render Function](http://vuejs.org/v2/guide/render-function.html) in Vue's documentation. In addition, if you are writing render functions with JSX, `babel-plugin-transform-vue-jsx` is required. See [here](https://github.com/vuejs/babel-plugin-transform-vue-jsx) for its configurations.
</details>

<details>
<summary>How do I use third-party icon font library with Element?</summary>

You just need to modify the class name prefix of the third-party library (see their docs for how to do it), and write some CSS, then you can use them just like you use Element built-in icons. For example, change the prefix to `el-icon-my`, and then add the following to its CSS:
```css
[class^="el-icon-my"], [class*=" el-icon-my"] {
  font-family:"your-font-family" !important;
  
  /* The following is based on original CSS rules of third-party library */
  font-size: inherit;
  font-style:normal;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
```
Now you can use them as you do with built-in icons. For example, in `el-input`:
```html
<el-input icon="my-xxx" />
```
</details>

<details>
<summary>When do you update documentations of Element?</summary>

We update documentations only when a new version of Element is published so that it reflects all the changes introduced in that version. Updated changed can be found in the [changelog](https://github.com/ElemeFE/element/blob/master/CHANGELOG.en-US.md)。
</details>

<details>
<summary>I imported Element in my project, but why does it report CSS error/font file error/components have no style?</summary>

Please refer to our [starter kit](https://github.com/ElementUI/element-starter) and correctly configure file-loader, css-loader and style-loader in webpack config file. Besides, we also provide templated based on [cooking](https://github.com/ElementUI/element-cooking-starter) and [laravel](https://github.com/ElementUI/element-in-laravel-starter).
</details>

<details>
<summary>I cloned Element's repo, but failed to run it. How do I solve it?</summary>

First, please make sure to clone the latest code in master branch and cloned files are intact. Then, note that the version of Nodejs should be 4.0+ and npm 3.0+. Finally, activate development:

```bash
npm run dev
```

or build it:

```bash
npm run dist
```
</details>
