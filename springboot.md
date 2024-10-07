#SpringBoot
##  Progress 

###   20240926 
*   買了hahow  的springboot 課
###   20240928
*   說有給我intellij 的六個月訂閱碼，結果我沒有在信箱看到
###   20240929
*   安裝JDK11, JDK17 ，windows 重開才能在 intellij 看到~
*   2024.07 後只能用java 17 和 springboot 3的版本，影片有註解
*   chatpter 2-Unit 2 IOC  and DI
*   @Commponet 只能用在class 上
*   被Spring 容器創建的Object 都叫作Bean
###   20241002
*   在json 裡的 Array 是可以轉換成Java 的List 
*   spring boot 將 object 轉成 json 格式放在 response body 是靠一個叫jackson 的library
*   int default value is 0 , Integer default value is null
### 20241003
*   validation request body , controller 方法的參數前面要加@Valid
*   validation request header , path ,  param , 則要在controller class 前面加@Validated 
*   exception Controller : 如果不寫exception controller , response body 會寫internal server error , 如果寫了 exception controller , response body 就會有明確的訊息。

### 20241006
*   Mysql 可以有兩欄以上的primary key
*   使用keyholder 可以用map 指定兩個primary key 欄位的值
```
    Map<String, Object> keyMap = keyHolder.getKeys();
    System.out.println("Generated order_id: " + keyMap.get("order_id"));
    System.out.println("Generated product_id: " + keyMap.get("product_id"));
```
### 20241007
*   Why You Need to Create Member Instances Explicitly:
    *   Member is a Custom Object: Java doesn't know how to create a Member object by default. You need to explicitly call new Member() to create an instance.
    *   String Literals Are Managed by Java: Java automatically handles String objects for literals, storing them in a string pool and creating them implicitly when they are assigned to variables.

##  JetBrains
*   我在9/29 用cv86092@gmail.com買了一個月的jetbrain，日期到10/29
*   hahow 10/2 才寄給我折扣碼，但不能用在gmail , 所以我用cv86092@plantynet.com.tw 這個email 去使用這個折扣碼