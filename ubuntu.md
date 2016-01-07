- 由于没有公钥，无法验证下列签名……：  
错误提示如下：  
W: GPG 错误：http://ppa.launchpad.net wily InRelease: 由于没有公钥，无法验证下列签名： NO_PUBKEY 7F73D5BEFC1B6133  
解决办法：  
出现以上错误提示时，只要把**后八位**拷贝一下来，并在[终端]里输入以下命令并加上这八位数字回车即可！  
```bash
sudo apt-key adv --recv-keys --keyserver keyserver.Ubuntu.com FC1B6133
```  
此类问题均可如此解决！
