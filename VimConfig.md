# Mac的Vim配置

mac系统已经默认安装了macvim，在terminal命令行直接输入[vim](https://so.csdn.net/so/search?q=vim&spm=1001.2101.3001.7020)，可以直接启用。

说起配置 Vim，就不得不提到vimrc文件，**vimrc是Vim最主要的配置文件，它有两个版本：全局版本和用户版本。**全局vimrc文件在Vim的安装目录中，其路径是 /usr/share/vim/vimrc；用户版本的vimrc文件在当前用户的主目录下，但是 Mac下默认是没有用户vimrc的，所以需要自己创建一个。

不管怎么改用户版的vimrc文件，其中的内容都是是覆盖在全局vimrc文件中设置的内容，这就意味着可以不需要去改变全局vimrc文件来进行配置vim，只需要修改用户vimrc文件。

在mac终端上使用vi或者vim来写代码时，vim本身的配置十分不方便，我们可以通过修改vim的配置文件vimrc文件，该文件的位置在 /usr/share/vim，切换到该目录下，vim vimrc 修改该文件，但此时会发现该文件是只读文件，不能修改，可以用 chmod +w vimrc 来修改该文件的权限，使其可写，修改成功，即可直接更改vimrc文件；若提示没有权限执行该命令，那么可以换一种方法：



将全局版vimrc文件复制到用户主目录下做为用户版vimrc：

```
cp /usr/share/vim/vimrc ~/.vimrc
```


将vimrc文件拷贝到当前用户主目录下（.vimrc为隐藏文件，防止以后使用过程中不小心删除或修改该文件），现在可以直接修改新的.vimrc文件，向文件中添加新的配置代码即可，如下：


```
"********************************基本设置******************************"
set tabstop=4                " 设置tab键的宽度
set shiftwidth=4             " 换行时行间交错使用4个空格
set autoindent               " 自动对齐
set backspace=2              " 设置退格键可用
set shiftwidth=4     		 " 自动缩进4空格
set smartindent              " 智能自动缩进
set number                   " 在每一行最前面显示行号
set showmatch                " 高亮显示对应的括号
set mouse=a                  " 启用鼠标
set ruler                    " 在编辑过程中，在右下角显示光标位置的状态行
set cursorline               " 突出显示当前行
set noswapfile               " 设置无交换区文件"
set writebackup              " 设置无备份文件
set nobackup                 " 设置无备份文件
set autochdir                " 设定文件浏览器目录为当前目录
set foldmethod=syntax        " 选择代码折叠类型
set laststatus=2             " 开启状态栏信息
set cmdheight=2              " 命令行的高度，默认为1，这里设为2
set autoread                 " 当文件在外部被修改，自动更新该文件
set autoread                 " 自动检测并加载外部对文件的修改
set autowrite                " 自动检测并加载外部对文件的修改
set showcmd                  " 在状态行显示目前所执行的命令，未完成的指令片段亦会显示出来
syntax enable                " 打开语法高亮


if has("gui_running")
    set guioptions+=b        " 显示底部滚动条
    set nowrap               " 设置不自动换行
endif

"********************************设置编码*******************************"
" 设置换行编码
set fileformats=unix,dos,mac
" 设置Vim 内部使用的字符编码方式
set encoding=utf-8
" 设置文件编码
if has("win32")
	set fileencoding=chinese
else
	set fileencoding=utf-8
endif
" 解决consle输出乱码
language messages zh_CN.utf-8
```

