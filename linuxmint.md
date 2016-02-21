- markdown 编辑器  
[haroopad](http://pad.haroopress.com/) 跨平台
- vim 配置  
[https://github.com/VundleVim/Vundle.vim](https://github.com/VundleVim/Vundle.vim)  
配置文件
[https://github.com/justintung/Vundle.vim/blob/master/.vimrc](https://github.com/justintung/Vundle.vim/blob/master/.vimrc)  
- 通过update-alternatives 来选择应用的不同版本/或其他可选值  
    1. display参数列出一个命令的所有可选命令  
        `sudo update-alternatives --display java`
    2. config参数用于给某个命令选择一个link值，相当于在可用值之中进行切换吧。

        `sudo update-alternatives --config java`  //有 2 个候选项可用于替换 java (提供 /usr/bin/java)  
        | 选择 	| 路径 	| 优先级 	| 状态 	|
        |--------|--------|--------|--------|
        |0|/usr/lib/jvm/java-6-openjdk/jre/bin/java|1061|自动模式|
        |1|/home/wuekzhu/download/jdk1.6.0_23/bin/java|1|手动模式|
    3. install参数用于添加一个命令的link值，相当于添加一个可用值，其中slave非常有用。

        `sudo update-alternatives --install /usr/bin/java java /usr/local/jre1.6.0_20/bin/javac 100`  
        `sudo update-alternatives –install /usr/bin/java java /usr/local/jre1.6.0_20/bin/javac 100 –slave /usr/bin/javac javac /usr/local/jre1.6.0_20/bin/javac`  
    4. remove参数用于删除一个命令的link值，其附带的slave也将一起删除。
        `sudo update-alternatives –remove java /usr/local/jre1.6.0_20/bin/java` 
        
    eg :  
     a.  `sudo update-alternatives --install /usr/bin/node node /www/itmotu/nodejs/node-v4.2.6-linux-x64/bin/node 90 --slave /usr/bin/npm npm /www/itmotu/nodejs/node-v4.2.6-linux-x64/bin/npm`  
     b.  `sudo update-alternatives --install /usr/bin/node node /www/itmotu/nodejs/node-v5.5.0-linux-x64/bin/node 100 --slave /usr/bin/npm npm /www/itmotu/nodejs/node-v5.5.0-linux-x64/bin/npm`  
    这时候可以通过命令 `sudo update-alternatives --config node` 来切换node的版本  
