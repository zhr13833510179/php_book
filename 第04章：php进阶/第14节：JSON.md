# 第14节:JSON
本节我们将为大家介绍如何使用 PHP 语言来编码和解码以及 JSON 对象

### 一、学习目标
如何进行编码和解码及JSON函数的定义，参数

### 二、PHP JSON
#### 1.环境配置
在 php5.2.0 及以上版本已经内置 JSON 扩展。

#### 2.JSON 函数
|函数|描述|
|---|---|
|json_encode|对变量进行 JSON 编码|
|json_decode|对 JSON 格式的字符串进行解码，转换为 PHP 变量|
|json_last_error|返回最后发生的错误|

#### 3.json_encode
PHP json_encode() 用于对变量进行 JSON 编码，该函数如果执行成功返回 JSON 数据，否则返回 FALSE 

语法：
``` php
string json_encode ( $value [, $options = 0 ] )
```

参数：
* 1、value: 要编码的值。该函数只对 UTF-8 编码的数据有效。
* 2、options:由以下常量组成的二进制掩码：JSON_HEX_QUOT, JSON_HEX_TAG, JSON_HEX_AMP, JSON_HEX_APOS, JSON_NUMERIC_CHECK,JSON_PRETTY_PRINT, JSON_UNESCAPED_SLASHES, JSON_FORCE_OBJECT

实例：
以下实例演示了如何将 PHP 数组转换为 JSON 格式数据：

``` php
<?php
   $arr = array('a' => 1, 'b' => 2, 'c' => 3, 'd' => 4, 'e' => 5);
   echo json_encode($arr);
?>

//输出：{"a":1,"b":2,"c":3,"d":4,"e":5}
```

以下实例演示了如何将 PHP 对象转换为 JSON 格式数据：

``` php
<?php
   class Emp {
       public $name = "";
       public $hobbies  = "";
       public $birthdate = "";
   }
   $e = new Emp();
   $e->name = "sachin";
   $e->hobbies  = "sports";
   $e->birthdate = date('m/d/Y h:i:s a', "8/5/1974 12:20:03 p");
   $e->birthdate = date('m/d/Y h:i:s a', strtotime("8/5/1974 12:20:03"));

   echo json_encode($e);
?>

//输出：{"name":"sachin","hobbies":"sports",、、"birthdate":"08\/05\/1974 04:20:03 pm"}
```

#### 4.json_decode
PHP json_decode() 函数用于对 JSON 格式的字符串进行解码，并转换为 PHP 变量。

语法：

``` php
mixed json_decode ($json_string [,$assoc = false [, $depth = 512 [, $options = 0 ]]])
```

参数：
* 1、json_string: 待解码的 JSON 字符串，必须是 UTF-8 编码数据
* 2、assoc: 当该参数为 TRUE 时，将返回数组，FALSE 时返回对象。
* 3、depth: 整数类型的参数，它指定递归深度
* 4、options: 二进制掩码，目前只支持 JSON_BIGINT_AS_STRING 。

以下实例演示了如何解码 JSON 数据：

实例如下所示：

``` php
<?php
   $json = '{"a":1,"b":2,"c":3,"d":4,"e":5}';

   var_dump(json_decode($json));
   var_dump(json_decode($json, true));
?>

/*输出：

object(stdClass)#1 (5) {
    ["a"] => int(1)
    ["b"] => int(2)
    ["c"] => int(3)
    ["d"] => int(4)
    ["e"] => int(5)
}

array(5) {
    ["a"] => int(1)
    ["b"] => int(2)
    ["c"] => int(3)
    ["d"] => int(4)
    ["e"] => int(5)
}

*/
```