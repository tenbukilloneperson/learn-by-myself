

```html
<1-1>��װhexo
   �ֿ����Ʊ�����  �ʻ���.io   

 npm install hexo -g

 ��ʼ��װhexo,����hexo -v ����Ƿ�װ�ɹ�

<1>cd����ǰ�̷���Ŀ¼��

<2>hexo init -->>��ʼ��

<3>��_Config.yml������

 deploy:

	type: git

	repository: �ֿ����ɵĵ�ַ

	branch: master

<4>ssh-keygen rsa -C "@qq.com"-->>�����µ�ssh�ļ�,�󶨵�github��

<5>npm install hexo-deployer-git ����֮ǰ��Ҫ��װ�����չ!

<6>Hexo������github��ʱ��,�ᶪʧreanme��CNAME;

	$ npm install hexo-generator-cname  -->>��װ�˲��

<7>hexo clean-->>�������!

<8>hexo new test -->>�����ĵ�

<9>��� hexo g     hexo d�ύһ��

<10>�ύ�ɹ���,�����ն���ʾ,Deploy done:git

<11>����һ���µ�MD��ʽ���ĵ�,hexo g hexo d�����ύ�ϴ�����

```



























<1>ж��hexo: npm uninstall hexo