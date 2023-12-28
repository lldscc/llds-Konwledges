# Http协议

https://developer.mozilla.org/zh-CN/docs/Web/HTTP

## 请求协议

#### 请求行：请求方式，资源路径，协议

#### 请求头：    key：value（浏览器版本....）

#### 请求体： POST请求的请求参数,GET无

## 响应协议

#### 响应行：协议，[HTTP 响应状态码](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Status)，描述

#### 响应头：   key：value（数据类型..）

#### 响应体： 响应数据

![image-20231202180807812](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20231202180807812.png)

## 协议解析

# 请求

## 分类

BS架构：浏览器-服务器

CS架构：客户端-服务器

## 简单参数

controller控制

参数少

+ controller层

```java
//测试请求参数的接受,springboot项目
@RestController
public class RequearController {
    @RequestMapping("/simpleParam")
    public String simpleParam(String username,Integer password){
        System.out.println(username+":"+password);
        return "okokokok!";
    }
}

```

+ 请求

```
//GET请求参数写在地址中
http://localhost:8080/simpleParam?username=llds&password=123456

//POST请求请求参数写在请求体中
http://localhost:8080/simpleParam
```

+ 返回

```
llds:123456
```



## 实体参数

![image-20231203215650545](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20231203215650545.png)

### 简单实体参数

参数多，请求参数封装一个实体类中，实体类的参数名与形参对象的属性名相同，定义pojo类

+ 封装pojo下的User类

  ```java
  public class User {
      private String username;
      private Integer password;
    	//空参实参tostring方法省略....  
  
  }
  ```

  

+ controllor

  ```java
  @RestController
  public class RequearController {
  //简单实体参数的请求
      @RequestMapping("/simplePojo")
          public String simplePojo(User user){
          System.out.println(user);
           return "okokokok!";
      }
  }
  ```

  

+ 请求

  ```
  http://localhost:8080/simplePojo?username=LLDS&password=654321
  ```

+ 返回

  ```
  User{username='LLDS', password=654321'}
  ```



### 复杂实体对象

请求参数名与形参属性名相同，按照对象层次结构关系即可接受嵌套POJO属性参数.



+ 创建pojo下Address类封装字段

  ```java
  public class Address {
      private String province;
      private String city;
  }
  ```

  

+ 封装pojo下的User类，中有Address对象

  ```java
  public class User {
      private String username;
      private Integer password;
      //Address对象
      private Address address;
    	//空参实参getset，tostring方法省略....  
  
  }
  ```

  

+ 请求

  ```
  http://localhost:8080/complexPojo?username=LLDS&password=654321&Address.province=河北&Address.city=邯郸
  ```

+ 返回

  ```json
  User{username='LLDS', password=654321, address=Address{province='河北', city='邯郸'}}
  ```

  

### 数组集合参数

 **数组**：请求参数名与形参数组名相同且请求参数为多个，定义数组类型形参即可接收参数

```
 //数组集合参数的请求
    @RequestMapping("/arrayParam")
    public String arrayParam(String[] hobby){
        System.out.println(Arrays.toString(hobby));
        return "okokokok!";
}
```

```
http://localhost:8080/arrayParam?hobby=LLDS&hobby=llds&hobby=LLds
```

```
[LLDS, llds, LLds]
```

**集合**：请求参数名与形参集合名称相同且请求参数为多个，`@RequestParam`绑定参数关系

```
//集合参数的请求
 @RequestMapping("/listParam")
    public String listParam(@RequestParam List<String> hobby){
        System.out.println(hobby);
        return "okokok!";
}
```

```
http://localhost:8080/listParam?hobby=LLDS&hobby=llds&hobby=LLds
```

```
[LLDS, llds, LLds]
```



### 日期参数

```
//日期参数的请求
 @RequestMapping("/dateParam")
public String dateParam(@DateTimeFormat(pattern = "yyyy-MM-dd HH:mm:ss") LocalDate updateTime){
        System.out.println(updateTime);
        return "ok date!";
}
```

```
http://localhost:8080/dateParam?updateTime=2023-12-12 10:10:09
```

```
2023-12-12
```

### json参数

json请求：POST请求，在请求体中：

```json
{
    "username":"LLds",
    "password":"123456",
    "address":{
        "province":"河北",
        "city":"邯郸"
    }

}
```

```
http://localhost:8080/jsonparam
```

+ 接受的数据封装到实体类中，JSON数据键名与形参对象属性名相同，定义POjO类型形参即可接收参数，需要使用`@RequestBody`标识

```
User{username='LLds', password=123456, address=Address{province='河北', city='邯郸'}}

```

### 路径参数

```
  //路径参数的请求
    @RequestMapping("/pathparam/{id}")
    public String pathparam(@PathVariable Integer id){
        System.out.println(id);
        return "ok date!";
    }
```

```
http://localhost:8080/pathparam/2
```

```
2
```







# 响应

![image-20231203215935889](C:\Users\Lenovo\Pictures\tempPic\image-20231203215935889.png)

## 简单封装

+ controller层

```java
//测试响应数据
@RestController
public class ResponseController {

    @RequestMapping("/hello")
    public String hello() {
        System.out.println("hello");
        return "hello";
    }

    @RequestMapping("/getAddr")
    public Address getAddr() {
        Address address = new Address();
        address.setProvince("河北");
        address.setCity("邯郸");
        return address;
    }

    @RequestMapping("/listAddr")
    public List<Address> listAddr() {
        List<Address> list = new ArrayList<>();

        Address address1 = new Address();
        address1.setProvince("河北");
        address1.setCity("邯郸");

        Address address2 = new Address();
        address2.setProvince("河北");
        address2.setCity("邢台");

        list.add(address1);
        list.add(address2);
        return list;

    }
}
```

+ 请求

  ```
  http://localhost:8080/listAddr
  ```

  



## 统一封装

+ 统一响应结果，创建result类

```java
//统一响应结果封装类
public class Result {


    private static Integer code;
    private static String msg;
    private Object data;


	//空参实参getset，tostring方法省略....  
    
    //    提供静态方法
    public static Result success(Object data){
        return new Result(1,"success",data);
    }
    public static Result success(){
        return new Result(1,"success",null);
    }
    public static Result error(){
        return new Result(0,msg,null);
    }

}

```



+ controller

  ```java
  //测试响应数据
  @RestController
  public class ResponseController {
      @RequestMapping("/hello")
      public Result hello() {
          System.out.println("hello");
          return Result.success("Hello code!");
      }
  
      @RequestMapping("/getAddr")
      public Result getAddr() {
          Address address = new Address();
          address.setProvince("河北");
          address.setCity("邯郸");
          return Result.success(address);
      }
  
      @RequestMapping("/listAddr")
      public Result listAddr() {
          List<Address> list = new ArrayList<>();
  
          Address address1 = new Address();
          address1.setProvince("河北");
          address1.setCity("邯郸");
  
          Address address2 = new Address();
          address2.setProvince("河北");
          address2.setCity("邢台");
  
          list.add(address1);
          list.add(address2);
          return Result.success(list);
      }
  ```

  响应数据

+ 响应数据

  ```
  {
      "data": "Hello code!",
      "code": 1,
      "msg": "success"
  }
  ```

  

  ```
  {
      "data": {
          "province": "河北",
          "city": "邯郸"
      },
      "code": 1,
      "msg": "success"
  }
  ```

  

  ```
  {
      "data": [
          {
              "province": "河北",
              "city": "邯郸"
          },
          {
              "province": "河北",
              "city": "邢台"
          }
      ],
      "code": 1,
      "msg": "success"
  }
  ```

  



































