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

### 20241107
    *   CrudRepository 中的 save 方法不只是新增，還有修改的功能
    *   application.properties : spring.jap.show-sql=true 可查看JPA生成的sql 語法。

### 20241108
    *   JPA findBy... ex findByNameAndGender(name,gender) 
    *   findByLastName(String lastname)
    *   要在StudentCrudRepository 新增此方法。
    *   Optional<T> 可以用isPresent 判斷是否沒值
### 20241109
    *   測試的程式要放在TEST 資料夾裡
    *   package 要和正式的package 相同

### 20241110
*   課程 7-5 下載的範例不能用，因為它用java 11 and spring boot version 2.3.x , 要符合自已電腦環境改成java 17 和 spring boot 3.3.4
*   @Transactional 在 main 資料夾底下是有一個發生錯誤，就會rollback ，而如果在test 資料夾就是單元測試結束後就會恢復所有更動的設定。可以加在方法上也可以加在class 上
*   這個寫法可以回傳寫入的Object
```java
        return ResponseEntity.status(HttpStatus.CREATED).body(newStudent);
```
### 20241111
*   RequestBuilder requestBuilder = MockMvcRequestBuilders.
*   MvcResult mvcResult = mockMvc.perform(resultBuilder).andExpect....

### 20241112
*   @SpyBean : 如果測試方法裡面有提到Mockito.when(studentDao) 才會使用假的，沒提到就用真的Bean
*   @MockBean ︰ 全部都是給假的Bean

### 20241119    
*   H2 資料庫︰嵌入資料庫
*   啟動spring boot 被創建，運行結束被銷毀
*   常用在單元測試
*   application.properties 在 test 和 src 裡的設定是完全獨立的

### 20241121
*   創建資料庫要放在schema.sql
*   塞資料要放在data.sql
*   Convention over Configuration 約定大於配置, 就是什麼檔案就是幹什麼事，不要使用者再去配置設定
*   Run Test with coverage 測試覆蓋率
  
### 20241127
*   7-12 Test Driven Development
*   7-13 總結
*   8-1 pom.xml dependency , group id 為 spring boot starter 開頭不可指定Version
### 20241129
*   Maven-project建構︰打包spring boot project 程式
*   Maven標籤可運行clean指令
*   java -jar xxx.jar ，spring boot build 出來的jar 檔就可以直接run 了
### 20241203
*   SNAPSHOT 不穩定版可無限次覆蓋 xxx-1.0.0-SNAPSHOT.jar
*   release 穩定版只能上傳一次，沒有後綴詞 xxx-1.0.0.jar
*   8-5 使用intellij 創建 project 
    *   groupId 公司名字
    *   artifactId 功能名稱
### 20241204
* 8-6 ObjectMapper
### 20241205
*   8-7 RestTemplate
    *   getForObject 帶 parameter 
    *   postForObject 帶 request Body
    *   exchange 可以帶 header 
### 20241208 
*   create project ->Template Engines -->Thymeleaf
*   model.addAttributes("myStudent":student)
```Java
如果不用bean 的話
Printer printer; 這寫法是不成立的
就算要寫也要指明道姓的寫 Printer printer = new HPPrinter();
所以控制反轉，依賴注入就會讓這個寫法比較簡訊
Printer printer;
```
*   8-10 Spring boot 3 , 支援java 17 以後的版本
*   javax-->jarkarta 
*   持續優化GraalVM 技術。

### 20241209
*   9-1 Debug 上
*   9-2 Debug 下
*   9-3 實用方法
    *   ctrl + 滑鼠左鍵可選使用此方法的地方
    *   ctrl +　alt + F 跳回游標的進入點
    *   視窗點兩下可以放大
    *   ctrl + alt + O 移除多餘的import 


##  JetBrains
*   我在9/29 用cv86092@gmail.com買了一個月的jetbrain，日期到10/29
*   hahow 10/2 才寄給我折扣碼，但不能用在gmail , 所以我用cv86092@plantynet.com.tw 這個email 去使用這個折扣碼
##  Hugo
雖然 GitHub Pages 推薦使用 Jekyll 生成靜態網頁，但在 Windows 環境下 Jekyll 似乎比較不友善，而 Hugo 入門相對容易、官方文件有完整的教學，還有編譯速度快等優點，眾多因素考慮下，我選擇了 Hugo。

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
