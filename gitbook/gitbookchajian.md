# gitbook插件
自己常用的gitbook插件
code                     代码复制
splitter                 文件和目录自己调整
hide-element             隐藏不必要的链接
page-toc-button          目录悬浮
back-to-top-button       回到顶部
chapter-fold 导航目录折叠
tbfed-pagefooter 页面底部添加信息

prism插件 
系统自带插件的高亮功能并不完善，可使用prism插件增强，该插件需要先禁用highlight插件
## 插件安装
```
gitbook install
```
## 整个代码如下：
```
{
    "plugins": [
        "code", 
        "-lunr", 
        "-search", 
        "search-pro",
        "splitter",
        "hide-element",
        "page-toc-button",
        "back-to-top-button"
    ],
    "pluginsConfig": {
        "hide-element": {
            "elements": [
                ".gitbook-link"
            ]
        },
        "page-toc-button": {
            "maxTocDepth": 2,
            "minTocSize": 2
           }
    }
}

```