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

### 20241014 practce
1.  insert  
    *   /family/addMember
2.  batch insert
3.  update
4.  delete 
5.  select

### 20241026  practive
*   try sayHello
*   create Member.java
*   create FamilyController.java
    *   /family/addMember -->17:41
    *   validate key value , if unvalidate and response error message in response body 
        *   限制電話號碼要十碼
    *   if table column type is date , namedparameterjdbctemplate has to input date type as well

### 20241029  practice
*   batch insert 
*   console --> right click table > New > Query Console
```
[
	{
      "name":"Michael",
      "birth":"1979-08-11",
      "role":"Father",
      "phone":"0922478250"
	},
  	{
      "name":"Joan",
      "birth":"1978-02-05",
      "role":"Mother",
      "phone":"098806705"
	}
]
```

### 20241031  practice
3.  update OK
4.  delete OK
5.  select OK

### 20241101 
*   遵行的寫法︰先去創建一個interface , 再寫class 去繼承這個interface 
*   我想的是那要怎麼樣的邏輯和關聯性才會去繼承這個interface 如果是不同的方法也是寫成class 去繼承interface 嗎?~
*   @Configuration 將此class 變成設定Spring 用的class 什麼是設定Spring 用的class
*   @Bean 只能用在帶用@Configuration class 的方法上
*   `大重點︰@Bean 就是去執行這個方法，然後把方法返回的值、物件存起來`，哦原來就是去執行這個方法，因為一般要在主程式去執行方法才會生成，現在加上@Bean 就可以直接運行
* 一定要所有的bean 被放進容器及初始化成功後 spring boot 才會成功啟動

### 20241103
* POSTConstruct
  * 使用建構子不能在constructor 裡去拿到其它Bean , 但是 Postconstruct 可以︰如︰
  ```java
  public class MyBean {

        int path;
        
        @Autowired
        private YourBean yourBean;

        ##這個編譯會錯
        MyBean(){
            this.path = yourBean.getPAth();
        }
        ##這個就沒問題
        @PostConstruct
        public void init() {
            this.path = yourBean.getPath();
        }
    }
  ```   
  
*   變數的類型盡量使用Interface 
*   IOC的精神，繼承Interface 的多型，被刪掉或更改時，注入其該類型的程式不需要去作更動。
  
*   MVC
    *   Model:負責業務邏輯、數據處理事(Service ,DAO)
    *   View:使用Html 模板呈現數據
    *   Controller:負責接收轉發Http Request、驗證參數正確
        *   StudentController --> StudentService --> StudentDAO
    *   DAO 介面和 Service 介面不需要加@Componet ，因為它們是interface ?~
    *   @Service @Repository 沒什麼特殊效果，只是寫程式判斷用那一層，其效果和@Componet 一樣。

### 20241105
    *   單個資料庫連線用spring.datasource.url , 多個資料庫用spring.datasource.xxx.jdbc-url
    *   ORM︰Object-Relational Mapping ︰將Java Object 去對應到資料庫的table , 所以對JAVA OBject 的操作就是對資料庫的操作
    *   JPA︰定義要如何去操作資料庫
    *   Hibernate : 一種ORM 框架，去實現JPA，JPA定義、Hibernate實作

##  JetBrains
*   我在9/29 用cv86092@gmail.com買了一個月的jetbrain，日期到10/29
*   hahow 10/2 才寄給我折扣碼，但不能用在gmail , 所以我用cv86092@plantynet.com.tw 這個email 去使用這個折扣碼
*   

## note
*   @Bean  
     注解 @Bean是一个方法级别的注解，主要用在@Configuration注解的类里，也可以用在@Component注解的类里。添加的bean的id为方法名。
```java
@Configuration
public class AppConfig {

   @Bean
   public TransferService transferService() {
        return new TransferServiceImpl();
   }
#以上方法等於下列這個寫法   
    <beans>
    <bean id="transferService" class="com.acme.TransferServiceImpl"/>
    </beans>
}
```
