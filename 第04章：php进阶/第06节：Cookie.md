# 第06节:Cookie
本节我们来学习Cookie的定义及简单使用

### 一、Cookie 是什么？
cookie 常用于识别用户。cookie 是一种服务器留在用户计算机上的小文件。每当同一台计算机通过浏览器请求页面时，这台计算机将会发送 cookie。通过 PHP，您能够创建并取回 cookie 的值。

### 二、如何创建 Cookie？
setcookie() 函数用于设置 cookie。

提示：setcookie() 函数必须位于 <html> 标签之前。

#### 1.语法
``` php
setcookie(name, value, expire, path, domain);
```

#### 2.实例 1
在下面的例子中，我们将创建名为 "user" 的 cookie，并为它赋值 "runoob"。我们也规定了此 cookie 在一小时后过期：

实例如下所示:

``` php
<?php
setcookie("user", "runoob", time()+3600);
?>

<html>
.....
```

提示：在发送 cookie 时，cookie 的值会自动进行 URL 编码，在取回时进行自动解码。（为防止 URL 编码，请使用 setrawcookie() 取而代之。）

#### 3.实例 2
您还可以通过另一种方式设置 cookie 的过期时间。这也许比使用秒表示的方式简单。

实例如下所示:

``` php
<?php
$expire=time()+60*60*24*30;
setcookie("user", "runoob", $expire);
?>

<html>
.....
```

在上面的实例中，过期时间被设置为一个月（60 秒 * 60 分 * 24 小时 * 30 天）。

### 三、如何取回 Cookie 的值？
PHP 的 $_COOKIE 变量用于取回 cookie 的值。

在下面的实例中，我们取回了名为 "user" 的 cookie 的值，并把它显示在了页面上：

实例代码如下:

``` php
<?php
// 输出 cookie 值
echo $_COOKIE["user"];

// 查看所有 cookie
print_r($_COOKIE);
?>
```

在下面的实例中，我们使用 isset() 函数来确认是否已设置了 cookie：

实例代码如下:

``` php
<html>
<head>
<meta charset="utf-8">
<title>晓舟报告(xiaozhou.com)</title>
</head>
<body>

<?php
if (isset($_COOKIE["user"]))
    echo "欢迎 " . $_COOKIE["user"] . "!<br>";
else
    echo "普通访客!<br>";
?>

</body>
</html>
```

### 四、如何删除 Cookie？
当删除 cookie 时，您应当使过期日期变更为过去的时间点。

实例代码如下:

``` php
<?php
// 设置 cookie 过期时间为过去 1 小时
setcookie("user", "", time()-3600);
?>
```