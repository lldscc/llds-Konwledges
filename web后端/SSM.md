# SSM

"Spring、SpringMVC、MyBatis"，它是一种用于构建Java企业级应用程序的技术栈。

1. Spring：Spring框架提供了轻量级的容器，用于管理Java对象的生命周期和依赖注入。它还提供了各种企业服务，如事务管理、安全性和AOP（面向切面编程）等。

2. SpringMVC：SpringMVC是Spring框架的一部分，用于构建Web应用程序。它提供了模型-视图-控制器（MVC）架构，使开发人员能够更轻松地构建和管理Web应用程序。

3. MyBatis：MyBatis是一种**持久性**框架，用于与数据库交互。它允许开发人员通过XML配置或注解将SQL查询映射到Java对象，从而简化了数据访问层的开发。javaEE三层架构：表现层(页面展示);业务层(逻辑处理);持久层(对数据的处理)jdbc的简化

![02](F:\Github-lldscc\PicGo_bed\img\studypic\02.jpg)

![01](F:\Github-lldscc\PicGo_bed\img\studypic\01.jpg)



## IOC-DI

IOC控制反转：对象的创建控制权由程序自身转移到外部（容器），这种思想称为控制反转。`@Component`

DI依赖注入：容器为应用程序提供运行时，所依赖的资源，称之为依赖注入。`@Autowored`

Bean对象：IOC容器中创建、管理的对象，称之为bean。

**controller控制层——serivce业务层——dao持久层**

controller层需要编写service的实现类，service层需要编写dao的实现类，有耦合，需要把实现类放到一个容器内，用的时候调用实现类.

![image-20231204145045111](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20231204145045111.png)

### IOC

![image-20231204151633370](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20231204151633370.png)

`@RestController`结合了 `@Controller` 和 `@ResponseBody` 的功能。

@ResponseBody:处理 HTTP 请求并返回 JSON 格式数据

@RequestMapping：用于定义处理请求的路径和请求方法

也可以使用请求方法注解

```
@GetMapping: 处理 GET 请求。示例：@GetMapping("/users")

@PostMapping: 处理 POST 请求。示例：@PostMapping("/users")

@PutMapping: 处理 PUT 请求。示例：@PutMapping("/users/{id}")

@DeleteMapping: 处理 DELETE 请求。示例：@DeleteMapping("/users/{id}")
```



### DI

`@Autowired`

![image-20231204153152568](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20231204153152568.png)

## Spring









## SpringMVC









## SpringBoot

















## MyBatis

**dao持久层框架，简化JDBC的开发**（mybatis的dao层叫Mapper）

https://mybatis.net.cn/

<img src="C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20231204155017544.png" alt="image-20231204155017544" style="zoom:50%;" />

### MyBatis入门(springboot工程)

1. 准备工作（创建springboot.工程，数据库表user、实体类User)

   `MyBatis Framework依赖` `MySQL Driver依赖`

   创建实体类与数据库字段对应，在pojo包下创建User类封装字段

2.  引入Mybatis的相关依赖，配置Mybatis：数据库连接信息

   ```properties
   #在application.properties配置数据库连接信息
   spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
   spring.datasource.url=jdbc:mysql://localhost:3306/boot_crm
   spring.datasource.username=root
   spring.datasource.password=123456
   ```

3. 编写SQL语句（注解/XML)

   在mapper(相当于dao)包下创建UserMapper接口，并用`@Mapper`注解，

   ```java
   //@Mapper注解表示这是一个mybatis的mapper类
   //运行时会自动为接口创建一个代理对象，并且将对象交给IOC容器管理，代理对象会去执行对应的sql语句
   @Mapper
   public interface UserMapper {
   //    查询所有用户
       @Select("select * from sys_user")
       public List<User> list();
   }
   ```

4. 测试

   test包下的`SpringbootMybatisQuickstartApplicationTests.java`

   ```java
   @SpringBootTest //表示这是一个测试类
   class SpringbootMybatisQuickstartApplicationTests {
   
   //@Autowired通过依赖注入的方式注入UserMapper
       @Autowired
       private UserMapper userMapper;
   
       @Test
       public void testListUser(){
           List<User> userList = userMapper.list();
           userList.stream().forEach(user -> {
               System.out.println(user);
           });
       }
   }
   ```



#### 数据封装

+ 实体类属性名和数据库表查询返回的字段名一致，mybatis会自动封装。
+ 如果实体类属性名和数据库表查询返回的字段名不一致，不能自动封装。





#### mybatis日志配置

在application.properties配置，日志输出到控制台.

```
mybatis.configuration.log-impl=org.apache.ibatis.logging.stdout.StdOutImpl
```



####  数据库连接池

![image-20231204174508273](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20231204174508273.png)

标准接口：DataSource

Druid(德鲁伊)：阿里巴巴开源的数据库连接池项目

切换数据库连接池：引入相关的依赖即可



#### lombok工具包

Java类库,通过注解的形式自动生成构造器，getter/setter等方法，自动化生成日志变量。

通过引入依赖使用.

```
@Slf4j  日志注解
```

![image-20231204180355232](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20231204180355232.png)

```
<dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
</dependency>
```



### MyBatis的增删改查(注解)

案例：用户管理面板

![image-20231204183954031](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20231204183954031.png)

#### 1.删除

```sql
# sql语句根据id删除
delete from emp where id = 17
```

+ mapper层的EmpMapper接口

  ```java
  //1.删除操作
  @Delete("delete from emp where id=#{id}")
   public void delete(Integer id);//返回值：影响条数
  ```

+ test的启动类

  ```java
  //    注入测试的对象
      @Autowired
      private EmpMapper empMapper;
      @Test
      public void testDelete(){
          empMapper.delete(17);
          System.out.println("删除成功");
  
  }
  ```

  **预编译SQL**:SQL注入是通过操作输入的数据来修改事先定义好的SQL语句，以达到执行代码对服务器进行攻击的方法，

  ```
  # sql注入攻击：一直成功
  select  count(*) from emp where username = 'llds' and password = '  'or'1'='1   ';
  ```

  ```java
  //mybatis的#{id}开启预编译SQL，占位符？
  @Delete("delete from emp where id=#{id}")
  public void delete(Integer id);
  ```

  ![image-20231204195450834](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20231204195450834.png)

#### 2.新增

```sql
# 2.SQL语句插入数据
insert into emp(username, name, gender, image, job, entrydate, dept_id, create_time, update_time)values ('Tom','汤姆',1,'1.png',1,'2002-01-02',1,now(),now());
```

+ mapper层的EmpMapper接口

  ```java
  //2.插入操作
  //传入Emp类的属性
  @Insert("insert into emp(username, name, gender, image, job, entrydate, dept_id, create_time, update_time)" +
  " values (#{username},#{name},#{gender},#{image},#{job},#{entrydate},#{deptId},#{createTime},#{updateTime})")
  public void insert(Emp emp);
  ```

+ test的启动类

  ```java
  //    2.插入操作
  @Test
  public void testInsert(){
          Emp emp = new Emp();
          emp.setUsername("cat");
          emp.setName("mao");
          emp.setImage("1.jpg");
          emp.setGender((short) 1);
          emp.setJob((short) 1);
          emp.setEntrydate(LocalDate.of(2020, 1, 1));
          emp.setCreateTime(LocalDateTime.now());
          emp.setUpdateTime(LocalDateTime.now());
          emp.setDeptId(1);
  
   //执行插入操作
   empMapper.insert(emp);
  }
  ```

  #### 

  

#### 3.更新

```sql
# 3.sql根据id更新数据
update emp set username='',name='',gender='',image='',job='',entrydate='',dept_id= '',update_time='' where id=22;
```

+ mapper层的EmpMapper接口

  ```java
  // 3.更新数据
  //传入的属性封装到Emp类的属性
  @Update("update emp set username=#{username},name=#{name},gender=#{gender},image=#{image}," +"job=#{job},entrydate=#{entrydate},dept_id=#{deptId},update_time=#{updateTime} where id=22")
  public void update(Emp emp);
  ```

+ test的启动类

  ```java
  //    3.更新操作
      @Test
      public void testUpdate(){
          Emp emp = new Emp();
          emp.setId(22);  //根据id更新数据
          emp.setUsername("cat1");
          emp.setName("mao1");
          emp.setImage("1.jpg");
          emp.setGender((short) 1);
          emp.setJob((short) 1);
          emp.setEntrydate(LocalDate.of(2000, 1, 1));
          emp.setUpdateTime(LocalDateTime.now());
          emp.setDeptId(1);
          //执行更新操作
          empMapper.update(emp);
      }
  
  ```

  

#### 4.查询

##### 根据ID查询

```sql
# 4.查询操作(根据id)
select * from emp where id = 1;
```

+ mapper层的EmpMapper接口

  ```java
    // 4.查询数据(根据id查询)
      //传入的属性封装到Emp类的属性
      @Select("select * from emp where id=#{id}")
      public Emp select(Integer id);
  ```

+ test的启动类

  ```java
    //    4.查询操作
      @Test
      public void testSelect(){
          Emp emp = empMapper.select(1);
          System.out.println(emp);
      }
  ```

+ 输出

  ```
  Emp(id=1, username=jinyong, password=123456, name=金庸, gender=1, image=1.jpg, job=4, entrydate=2000-01-01, deptId=null, createTime=null, updateTime=null)
  ```

  值为null，说明与实体类的字段名不同，有几种解决方案,**驼峰命名**常用

  1. 可以起别名与字段名相同.

     ```
     //4.1起别名保持属性名和数据库字段名一致
     @Select("select id, username, password, name, gender, image, job, entrydate, dept_id deptId, create_time createTime, update_time updateTime" +
     " from emp where id=#{id}")
     public Emp select(Integer id);
     ```

     

     ```输出
     Emp(id=1, username=jinyong, password=123456, name=金庸, gender=1, image=1.jpg, job=4, entrydate=2000-01-01, deptId=2, createTime=2023-12-04T18:37:53, updateTime=2023-12-04T18:37:53)
     ```

  2. 通过`@results`和`@result`注解

     ```java
     //      4.2使用@results和@result注解
     //property实体类字段名,column表中名
     @Results({
                     @Result(property = "deptId",column = "dept_id"),
                     @Result(property = "createTime",column = "create_time"),
                     @Result(property = "updateTime",column = "update_time")
      })
             @Select("select * from emp where id=#{id}")
             public Emp select(Integer id);
     ```

  3. 在application.properties配置,开启后mybatis的驼峰命名自动映时开关 a cloumn------>aCo1mn

     ```
     mybatis.configuration.map-underscore-to-camel-case=true
     ```

     



##### 条件查询

```sql
# 5.查询操作(条件)
# 姓名(模糊匹配)，性别(精准查询)，入职时间(范围搜索);结果按修改时间倒序
select * from emp where name like '%张%' and gender =1 and entrydate between '2010-01-01' and '2020-01-01' order by update_time desc ;
```

+ mapper层的EmpMapper接口

  ```java
      //5.条件查询
      @Select("select * from emp where name like '%${name}%' and gender =#{gender} " +
              "and entrydate between #{begin} and #{end} order by update_time desc")
      public List<Emp> list(String name, Short gender, LocalDate begin, LocalDate end);
  ```

+ test的启动类

  ```java
      //5.条件查询
      @Test
      public void testList() {
          List<Emp> empList = empMapper.list("张", (short) 1, LocalDate.of(2010, 1, 1), LocalDate.of(2020, 1, 1));
          System.out.println(empList);
      }
  ```

  





### XML映射文件

**复杂SQL语句用XML文件**

![image-20231205093446539](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20231205093446539.png)

EmpMapper接口

```java
//5.1xml配置文件中的条件查询
public List<Emp> list(String name, Short gender, LocalDate begin, LocalDate end);
```

xml

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.llds.mapper.EmpMapper">
     <select id="list" resultType="com.llds.pojo.Emp">
         select * from emp where name like '%${name}%' and gender =#{gender}  and entrydate between #{begin} and #{end} order by update_time desc
     </select>
</mapper>
```



### 动态SQL

随着用户的输入或外部条件的变化而变化的SQL语句，我们称为动态SQL。

+ `<if>`
+ `<foreach>`
+ `<sql> <include>`





## Nginx

查询端口号占用,可以查到PID进程号，在任务管理器查看

```
netstat -ano | findStr 端口号
```

修改Nginx端口号：conf/nginx.conf文件

```
serve{
     listen   端口号
}
```































