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

'''
(setq make-backup-files nil)
'''

b### 设置emacs主题

先把存放主题文件的目录加载到emacs中

```
;; 主题目录
(add-to-list 'custom-theme-load-path "~/.emacs.d/themes/")
```
把下载好的主题文件(以`.el`结尾的文件)放入该目录中。

```
;;设置默认主题
(load-theme 'monokai t)

```