# 第一个 Case

# 产品手册指南

[如何更新本手册？](#如何更新本手册？)

[如何生成 HTML 版本的手册？](#如何生成HTML版本的手册？)

[如何生成 PDF 版本的手册？](#如何生成PDF版本的手册？)

[如何安装生成 PDF 的相关环境？](#如何安装生成PDF的相关环境？)

推荐生成 HTML 格式的文档浏览。

## 如何更新本手册？

1. 修改要更新的章节对应的 md 文件
2. 执行根目录下的 bash 文件：`./merge-man.sh`，将最新的各章节内容合并到`mnos-user-manual.md`中
3. 将各个 md 文件修改更新到 git 仓库

## 如何生成 HTML 版本的手册？

前提：已安装 VSCODE、VSCODE 的`Markdown Preview Enhanced`插件

1. clone 本仓库，checkout `mnos-user-nanual`分支
2. 进入`mtnos-doc/mnos-user-manual`目录，修改`0000_0_cover.md`文件中的时间
3. 回到`mtnos-doc目录`执行`./merge-man.sh`生成最新的合集手册`mnos-user-manual.md`
4. VSCODE 打开合集手册的 MD 文件`mnos-user-manual.md`，右键选择`Markdown Preview Enhanced: Open Preview to the Side `
5. 在预览页面，右键选择`HTML > HTML(offline) `即可生成 HTML 文档

注：PDF 版本，表格预览效果较好，列宽度自适应的结果比较好

## 如何生成 PDF 版本的手册？

前提：已安装 VSCODE、VSCODE 的`Markdown Preview Enhanced`插件以及`princexml`

1. clone 本仓库，checkout `mnos-user-nanual`分支
2. 进入`mtnos-doc/mnos-user-manual`目录，修改`0000_0_cover.md`文件中的时间
3. 回到`mtnos-doc目录`执行`./merge-man.sh`生成最新的合集手册`mnos-user-manual.md`
4. VSCODE 打开合集手册的 MD 文件`mnos-user-manual.md`，右键选择`Markdown Preview Enhanced: Open Preview to the Side `
5. 在预览页面，右键选择`PDF(prince)`即可生成 PDF 文档

注：目前 PDF 版本手册，表格宽度是等宽的，暂时无法自适应成最优结果

## 如何安装生成 PDF 的相关环境？

1. 安装 VSCODE，略

2. 安装 VSCODE 的`Markdown Preview Enhanced`插件，略

3. 安装 prince，官网https://www.princexml.com/，brew安装或者官网下载安装

    `brew install Caskroom/cask/prince`

4. 设置 PDF 风格：`cmd-shift-p` 选择 `Markdown Preview Enhanced: Customize Css` 命令，打开 `style.less`文件，将以下内容粘贴至 style.less，保存

    ```

    /* Please visit the URL below for more information: */
    /*   https://shd101wyy.github.io/markdown-preview-enhanced/#/customize-css */
    @font-face {
      font-family: "lanting";
      font-style: normal;
      font-weight: lighter;
      src: prince-lookup("Lantinghei SC")
    }

    @font-face {
      font-family: "powerline";
      src: prince-lookup("Meslo LG S Regular"),
            url("/Users/mtdp/Library/Fonts/Meslo LG S Regular for Powerline.ttf");
    }
    .markdown-preview.markdown-preview {
      // modify your style here
      // eg: background-color: blue;
      font-family: "lanting", "powerline";
      h1 {
        font-size: 2.0em;
        page-break-before: always;
      }
      h2 {
        font-size: 1.5em;
      }
      h3 {
        font-size: 1.2em;
      }
      pre, code {
        font-family: "powerline", "lanting";
        font-size: small;
      }
      blockquote {
        font-family: "powerline", "lanting";
        font-size: small;
      }
      b, strong {
        font-weight: 600;
      }
      table {
        font-size: small;
        table-layout: fixed;
        word-break: break-all;
        width: 100%
      }
      th {
        font-weight: normal;
        background-color: rgb(240,240,240)
      }
      &.prince {
        @page {
          @bottom {
            content: counter(page)
          }
        }
        ol {
          margin-left: 5pt;
        }
     ul {
          margin-left: 5pt;
        }
      }
    }
    ```

# 第二个 Case

# dev-universal

[![lerna](https://img.shields.io/badge/maintained%20with-lerna-cc00ff.svg?style=flat-square)](https://lernajs.io/)
[![Prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://prettier.io/)
[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow.svg?style=flat-square)](https://conventionalcommits.org)

> 统一开发模式相关

## Packages

-   [@mtfe/dev-universal-client](packages/dev-universal-client) - 开发统一相关的客户端工具包
-   [@mtfe/era-api-proxy](packages/era-api-proxy) - 主要用于实现外部接口的代理转发
-   [@mtfe/era-dev-better](packages/era-dev-better) - 为了更好的开发体验，集成各种插件和特性，包括但不限于：错误抛出，点击打开编辑器，文件名大小写敏感，第三方模块热重载
-   [@mtfe/era-react-ssr](packages/era-react-ssr) - era 插件：支持 React SSR / CSR 模式
-   [@mtfe/m-cli](packages/m-cli) - 到餐前端二组新框架初始化命令行

## 开发相关

```bash
npm run new # 新建包
```

### Contributing

-   Fork it!
-   Create your new branch:\
    `git checkout -b feature-new` or `git checkout -b fix-which-bug`
-   Start your magic work now
-   Make sure npm test passes
-   Commit your changes:\
    `git commit -am 'feat: some description (close #123)'` or `git commit -am 'fix: some description (fix #123)'`
-   Push to the branch: `git push`
-   Submit a pull request :)

## Authors

## License

MIT
