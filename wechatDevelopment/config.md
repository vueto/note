# 微信配置文件


## 服务器连接微信服务器的配置文件

``` php

<?php  
define("TOKEN", "xxxxxxxxxx");//这里修改为上图中自己配制的Token  
$wechatObj = new wechatCallbackapiTest();  
//接入时使用该验证方法  
$wechatObj->valid();  
  
class wechatCallbackapiTest  
{  
    public function valid()  
    {  
        $echoStr = $_GET["echostr"];  
        if($this->checkSignature()){  
            echo $echoStr;  
            exit;  
        }  
    }  
          
    private function checkSignature()  
    {  
        $signature = $_GET["signature"];  
        $timestamp = $_GET["timestamp"];  
        $nonce = $_GET["nonce"];      
                  
        $token = TOKEN;  //微信中配置的Token
        $tmpArr = array($token, $timestamp, $nonce);  
        sort($tmpArr, SORT_STRING);  
        $tmpStr = implode( $tmpArr );  
        $tmpStr = sha1( $tmpStr );  
          
        if( $tmpStr == $signature ){  
            return true;  
        }else{  
            return false;  
        }  
    }  
}  
?>  

```