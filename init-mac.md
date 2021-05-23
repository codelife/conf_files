##安装brew--> 建议更换镜像源方式
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
如果慢使用以下方法
/bin/bash -c "$(curl -fsSL https://cdn.jsdelivr.net/gh/ineo6/homebrew-install/install.sh)"

更换为清华大学源

git -C "$(brew --repo)" remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git

git -C "$(brew --repo homebrew/core)" remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git

git -C "$(brew --repo homebrew/cask)" remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-cask.git

brew update

设置环境变量需要注意终端Shell的类型: echo $SHELL
echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles/bottles' >> ~/.zshrc
source ~/.zshrc

### 安装iTerm2
brew install --cask iterm2

* install colorscheme for iterm2
git clone git@github.com:mbadolato/iTerm2-Color-Schemes.git
cd iTerm2-Color-Schemes && tools/import-scheme.sh schemes/*

### 调整shell为zsh
* `chsh -s $(which zsh)`
* install ohmyzh  `sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"`

cd ~/.oh-my-zsh/
lib 提供了核心功能的脚本库
tools 提供安装、升级等功能的快捷工具
plugins 自带插件的存在放位置
templates 自带模板的存在放位置
themes  自带主题文件的存在放位置
custom 个性化配置目录，自安装的插件和主题可放这里

**设置shell的配置文件`~/.zshrc` 更改配置切勿修改～/.bashrc
# 自动更新zsh，不提示更新
echo "DISABLE_UPDATE_PROMPT=true" >> ~/.zshrc
echo 'HIST_STAMPS="yyyy-mm-dd"' >> ~/.zshrc

## install neovim

brew install neovim

##install python3
brew install python3
防止使用mac自带的python. 增加一下配置
echo "export PATH=$HOME/bin:/usr/local/bin:$PATH" >> ~/.zshrc  && source ~/.zshrc

修改pip的源，加速
修改配置文件: ~/.pip/pip.conf
[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple

[install]
trusted-host=mirrors.aliyun.com

## 安装python的包
pip3 install pylint flake8 pyflakes black isort autopep8  virtualenv virtualenvwrapper

echo "
export WORKON_HOME=$HOME/.virtualenvs
export PROJECT_HOME=$HOME/Projects
VIRTUALENVWRAPPER_PYTHON=/usr/local/bin/python3
source /usr/local/bin/virtualenvwrapper.sh
# usage:
# mkvirtualenv abc; cpvirtualenv abc abc1; lsvirtualenv;  lssitepackages
# 所有环境都安装jedi
allvirtualenv pip3 install jedi
" >> ~/.zshrc
pip3 install jedi ipython
#top 的替代品
pip3 install glances

## 开发相关的包
brew install ack ripgrep wget ripgrep the_silver_searcher fzf
brew install coreutils lua luarocks
brew install ansible
brew install redis docker git nginx  mysql@5.7

## 做link, 不然找不到mysql mysql_config等命令
brew link mysql@5.7
echo 'export PATH="/usr/local/opt/mysql@5.7/bin:$PATH"' >> ~/.zshrc

## 修改键盘按键映射
~/.config/karabiner/karabiner.json

## 安装nerd-font现实图标. 然后修改iterm中的字体non-ASCII text为nerd-font
```brew tap homebrew/cask-fonts

brew install --cask font-hack-nerd-font```

brew install neovim
echo 'alias vim=neovim' >> ~/.zshrc
pip3 install pynvim

# more coc-extension

```brew install node
brew install npm && npm install --global prettier
npm i eslint eslint-plugin-vue -D
npm install --global htmlhint
npm install yarn
npm install -g neovim

pip3 install pylint
pip3 install flake8
pip3 install pyflakes
pip3 install black
pip3 install isort
pip3 install autopep8
pip3 install pynvim==0.4.3
pip3 install jedi-language-server
(vim 中安装vim-jedi或者coc-jedi)用户代码补全和跳转等功能


vue项目需要执行以下命令coc-vetur才能正常工作
npm i eslint eslint-plugin-vue -D

npm install -g bash-language-server
npm install -g sql-formatter
npm install node-sql-parser --save
```