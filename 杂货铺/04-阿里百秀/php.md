```php
1.添加新的域名
	phpstudy其他选项菜单-域名管理-添加域名-修改hosts文件-	修改vhosts-cof文件

2.Apache服务出现问题：命令行单独启动Apache，查看错误信息。
	启动：Apache/bin/httpd

3.检测受影响行数
mysqli_affected_rows($link);

4.in_arrary(要检测的值，要检测的数组) 不存在返回false  存在返回true

5. 检测字符串 mb_strpos(要检测的值，要检测的字符串)  不存在返回-1

6.file_get_contents(url) 服务端代理跨域

7.Access-Control-Allow-origin:*

8.S_SERVER['HTTP_ORIGIN']  获取跨域的地址

9.count（$count）用来获取数组的长度（元素个数）

10.strlen($str)  用来获取字符串的长度

11.uniqid() 用来生成随机字符串   time() 时间戳

12.move_uploaded_file($files['tmp_name'][$i],最终路径)；

12.strrchr($file['name'][$i],'.')  从右侧开始查找，找到指定部分后取出后半部分内容（包括查找的参数）；

13.检测参数是否存在使用  isset($_GET['id']);  true 或者false
```

