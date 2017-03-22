## 简介

深圳大学本科毕业论文Latex模板

## 安装

### Windows

先安装 [Texlive](http://mirror.lzu.edu.cn/CTAN/systems/texlive/Images/texlive.iso)，安装的位置是在
`C:\texlive`
然后把下面这个路径加到 PATH 当中
`C:\texlive\2015\bin\win32;`
这时候你在终端输入 `tlmgr --version` 应该会有输出。
这样 Texlive 2015 这边就算配置完成了。

再安装 [SumatraPDF](http://www.sumatrapdfreader.org/download-free-pdf-viewer-cn.html) , 安装位置是在
`C:\Program Files\SumatraPDF`
然后把下面这个路径加到 PATH 当中
`C:\Program Files\SumatraPDF;`

接下来就是安装 [Sublime](https://www.sublimetext.com/)，[Package Control](https://packagecontrol.io/installation)，还有 [LaTeXTools](https://github.com/SublimeText/LaTeXTools)。
然后配置一下 LaTexTools，打开 `Preferences | Package Settings | LaTeXTools | Settings - User`，然后定位到 `Platform settings` 这一节，改成下面像这样

```
// ------------------------------------------------------------------
// Platform settings: adapt as needed for your machine
// ------------------------------------------------------------------

"windows": {
        "texpath" : "C:\\texlive\\2015\\bin\\win32;$PATH",
        "distro" : "texlive",
        // Command to invoke Sumatra. If blank, "SumatraPDF.exe" is used (it has to be on your PATH)
        "sumatra": "",
        "sublime_executable": "",
        "keep_focus_delay": 0.5
    },
```

用 Sublime 打开这个项目，在 `main.tex` 文件下按 `Ctrl - b` 应该就可以顺利编译了。

配置 SumatraPDF 反向搜索
我们在编译 LaTeX 文件时，经常需要用到反向搜索，也即从 PDF 的内容跳到代码的内容， SumatraPDF 是 LaTeXTools 默认使用的预览工具。
在 SumatraPDF 上方的菜单栏选择 `设置 | 选项`，将下面的代码添加到 SumatraPDF 选项的最下面方的反向搜索设置框内即可。
`"C:\Program Files\Sublime Text 2\sublime_text.exe" "%f:%l"`
详情参见 [Sublime Text 搭建 LaTeX 编写环境](http://www.latexstudio.net/archives/1169) 

### OS X

先安装 [MacTex Basic](http://tug.org/cgi-bin/mactex-download/BasicTeX.pkg)，安装的位置是在

```
/usr/local/texlive/2015basic
```

然后把下面这个路径加到 PATH 当中

```
/usr/local/texlive/2015basic/bin/x86_64-darwin
```

这时候你在终端输入 `tlmgr` 应该会有输出。因为 MacTex 我们装的是基础版，所以还要安装一些第三方库，执行

```
$ sudo tlmgr update --self
$ sudo tlmgr install latexmk lastpage
```

这样 MacTex 这边就算配置完成了。接下来就是安装 [Sublime](https://www.sublimetext.com/)，[Package Control](https://packagecontrol.io/)，还有 [LaTeXTools](https://github.com/SublimeText/LaTeXTools)。

然后配置一下 LaTexTools，打开 `Preferences | Package Settings | LaTeXTools | Settings - User`，然后定位到 `Platform settings` 这一节，改成下面像这样

```
// ------------------------------------------------------------------
// Platform settings: adapt as needed for your machine
// ------------------------------------------------------------------

    "osx":  {
        // Path used when invoking tex & friends; MUST include $PATH
        "texpath" : "/usr/local/texlive/2015basic/bin/x86_64-darwin:$PATH"
        // Path to PDF viewer, if needed
        // TODO think about it. Also, maybe configure it here!
    },
```

用 Sublime 打开这个项目，按 `Ctrl - b` 应该就可以顺利编译了。

到这里编译工作就算完成了，不过还可以再安装一个软件 [Skim](http://skim-app.sourceforge.net/)，用于编译后立即预览 pdf 文件。一般直接安装就可以了，不过这里我们还想设置一下反向搜索，所以打开 Skim，选择 `选项 ｜ 同步`，在预设里面选择 `Sublime Text`。然后再用 Skim 重新打开我们的 pdf 文件，按住 `command + shift` 的同时用鼠标点击正文的任意一处，就可以很方便地跳回到我们的 LaTex 源码了。
