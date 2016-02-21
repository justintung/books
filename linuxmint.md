- markdown 编辑器  
[haroopad](http://pad.haroopress.com/) 跨平台
- vim 配置  
[https://github.com/VundleVim/Vundle.vim](https://github.com/VundleVim/Vundle.vim)  
配置文件
[https://github.com/justintung/Vundle.vim/blob/master/.vimrc](https://github.com/justintung/Vundle.vim/blob/master/.vimrc)  
- 通过update-alternatives 来选择应用的不同版本/或其他可选值  
 1.  `sudo update-alternatives --install /usr/bin/node node /www/itmotu/nodejs/node-v4.2.6-linux-x64/bin/node 90 --slave /usr/bin/npm npm /www/itmotu/nodejs/node-v4.2.6-linux-x64/bin/npm`  
 2.  `sudo update-alternatives --install /usr/bin/node node /www/itmotu/nodejs/node-v5.5.0-linux-x64/bin/node 100 --slave /usr/bin/npm npm /www/itmotu/nodejs/node-v5.5.0-linux-x64/bin/npm`  
这时候可以通过命令 `sudo update-alternatives --config node` 来切换node的版本  
