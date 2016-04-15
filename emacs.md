关于emacs的一些自己用到的配置。

emacs的语法很奇怪，我不想成为emacs的专家，所以根据google来的信息，整理一下适用。

### 添加MELPA安装源

```
(require 'package)
(add-to-list 'package-archives
	     '("melpa-stable" . "https://stable.melpa.org/packages/") t)
```

安装包的时候使用`M-x package-install`

### 不生成尾部带`~`的文件

```
(setq make-backup-files nil)
```

### 设置emacs主题

先把存放主题文件的目录加载到emacs中

```
;; 主题目录
(add-to-list 'custom-theme-load-path "~/.emacs.d/themes/")
```
把下载好的主题文件(以`.el`结尾的文件)放入该目录中。

以monokai为例，设置emacs加载的默认主题。

```
;;设置默认主题
(load-theme 'monokai t)

```

### 设置字体

emacs 字体分为好几个模块，有显示区域的字体，有菜单里的字体，还有buffer里的字体。

以下内容是配置显示区域的字体，不涉及其它区域的字体。

emacs要分别为中文和英文设置字体。

#### 设置英文字体

```
(set-face-attribute 'default nil :font "DejaVu Sans Mono 11")
```

字体后带的数字即字体的大小。

#### 设置中文字体

首先需要安装想要的中文字体，如何安装字体可以参考`linux.md`中的内容。

如果字体安装成功，在init.el中加入以下内容：

```
;;设置中文字体
(dolist (charset '(kana han symbol cjk-misc bopomofo))
  (set-fontset-font (frame-parameter nil 'font)
		    charset
		    (font-spec :family "文泉驿微米黑" :size 15)))
```

就可以将emacs中的**中文字体**设置成**文泉驿微米黑**

## 显示行号

emacs 24中已经原生支持显示行号了。

`M-x linum-mode`就可在当前显示窗口中显示行号。

在init.el中加入

```
;;显示行号
(global-linum-mode 1)
```

就能在全局模式下启用显示行号。

## 安装emmet扩展

通过MELPA源进行安装，`emmet-mode`

通过`hook`在其它模式下启用`emmet-mode`

```
;;在html模式下启用emmet-mode
(add-hook 'html-mode-hook 'emmet-mode)
```

## emacs使用文件树

安装`neotree`可以显示当前文件所在文件夹下的文件树。

通过MELPA源进行安装。

~~# 已经放弃emacs~~

~~html文件中夹杂着javascript, 没办法正常显示javascript的语法样式。~~

~~换到sublime text 3下，结果中文无法正常输入。~~

~~linux下桌面有好多东西要完善。~~

下载了网络上流行的purcell大叔配置的emacs文件，顿时世界美好了许多。

从学习使用先人的emacs配置开始，emacs真的好用，这是我一直不想离开他的原因。
