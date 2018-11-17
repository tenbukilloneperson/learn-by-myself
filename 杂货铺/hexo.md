

```html
<1-1>安装hexo
   仓库名称必须以  帐户名.io   

 npm install hexo -g

 开始安装hexo,输入hexo -v 检测是否安装成功

<1>cd到当前盘符根目录下

<2>hexo init -->>初始化

<3>在_Config.yml中设置

 deploy:

	type: git

	repository: 仓库生成的地址

	branch: master

<4>ssh-keygen rsa -C "@qq.com"-->>生成新的ssh文件,绑定到github上

<5>npm install hexo-deployer-git 部署之前需要安装这个扩展!

<6>Hexo发布到github的时候,会丢失reanme和CNAME;

	$ npm install hexo-generator-cname  -->>安装此插件

<7>hexo clean-->>清除缓存!

<8>hexo new test -->>创建文档

<9>最后 hexo g     hexo d提交一次

<10>提交成功后,会在终端显示,Deploy done:git

<11>创建一个新的MD格式的文档,hexo g hexo d进行提交上传更新

```



























<1>卸载hexo: npm uninstall hexo