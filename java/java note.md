# 耿瓦的Java笔记😒  
  
### 1.面向对象  
  
面向对象：利用对象进行软件开发。  
  
对象：顾名思义，创建的东西。<u>把相关的数据和方法组织为一个整体来看待。</u>eg：  
  
```Java  
public class Note{  
      
    public class man{  
        String name;  
        int age;  
        char sex;  
    }  
      
    public static void main(String[] args){  
        System.out.println("这里创造的man就是对象,name，age，sex为创建的属性。  
                           注意，同一类事物的属性必须是一致的。");  
    }  
}   
```  
  
  
  
#### 1.类和对象  
  
1. 类中所有的属性只定义，不赋值。  
  
2. 创建对象，记录单独个体的所有信息。（即new一个对象）  
  
3. 格式：  
  
   ```java  
   public class Dog{  
       String name;  
       ......  
   }  
     
     
   public class Test{  
       public static void main(String[] args){  
           Dog xuewei = new Dog;  
           xuewei.name = "周友翔";  
           ......  
       }  
   }  
   ```  
  
#### 2.Javabean  
  
描述一类事物的类叫Javabean类（无main方法，仅创造对象）。（记住就行了别问我也不知道这什么玩意）  
  
Javabean类可以写属性和行为。  
  
  
  
#### 3.面向对象中的数据安全（private关键字）  
  
private关键字是一个权限修饰符，可以修饰<u>成员变量</u>（变量）和<u>成员方法</u>(行为）。  
  
```Java  
public class xueWei{  
    String name; //成员变量  
    ...  
}  
  
  
public void Print(){  
    System.out.print("zyx is a renji"); //成员方法  
}  
```  
  
特点：一旦被private修饰，只能在本类中访问，外界无法访问。  
  
使用get/set方法  
  
get方法：取值       set方法：赋值  
  
  
  
#### 4.就近原则与this关键字  
  
就近原则：在方法当中直接使用变量查找顺序：先找局部变量，再找成员变量。  
  
若想直接使用成员变量，则格式为：this.局部变量  
  
```java  
System.out.print(age); //局部变量  
System.out.print(this.age); //成员变量  
```  
  
  
  
#### 5.构造方法  
  
构造方法也叫做构造器、构造函数  
  
作用：在创建对象的时候给成员变量进行初始化的  
  
格式：  
  
```  
修饰符  类名（参数）  {  
       方法体；  
}  
```  
  
```Java  
Student s1 = new Student(); //调用空参方法  
Student s2 = new Student(); //调用有参方法  
```  
  
特点：  
  
- 方法名与类名相同，大小写也要一致  
- 没有返回值类型，连void都没有  
- 没有具体的返回值（不能由return带回结果数据）  
  
执行时机：  
  
- 创建对象的时候由虚拟机调用，不能手动调用构造方法  
- 每创建一次对象，就会调用一次构造方法  
  
*注意事项：*  
  
- *如果没有定义构造方法，系统将给出一个默认的无参构数构造方法*  
- *如果自己写了任意构造方法，系统将不再提供默认的构造方法*  
- *带参构造方法和无参构造方法，两者方法名相同，但是参数不同，这叫做构造方法的<u>重载</u>*  
- *习惯：无论是否使用，都手动书写无参数构造方法，和带全部参数的构造方法*  
  
  
  
#### 6.重写toString方法  
  
```java  
@Override  
    public String toString(){  
        syso("返回语句")  
    }  
```  
  
toString方法一般都会重写，返回输出语句。  
  
  
  
### 2.面向对象进阶  
  
#### 1.static修饰成员变量  
  
static：<u>表示静态</u>，是Java的修饰符，用来修饰成员变量/成员方法（多用于测试类和工具类中，Javabean类中很少会用）  
  
  
  
> 补充  
>  
> 工具类：不是用来描述一类事物的，也没有main方法，而是帮我们做一些事情的类  
>  
> ```java  
> public class Test{  
>     public static void main(String[] args){  
>         int[] arr = {1,2,3,4,5};  
>         //遍历数组  
>         //求最大值  
>         //求最小值  
>         ...  
>     }  
> }  
> ```  
>  
> 将遍历数组等功能单拉出来组成一个新的<u>public class Tools{}</u>，就是工具类，需要时可随时调用  
  
> 工具类书写方式：  
>  
> 1. 类名见名之意  
> 2. 私有化构造方法  
>  
> ```Java  
> public class ArrayUtil{  
>   private ArrUtil(){  
>      public static int getMax(){}  
>         public static int getSum(){}  
>         public static int getMin(){}  
>   }  
> }  
> ```  
>  
>   3.方法定义为静态  
  
特点：叫做静态变量，被该类所有对象<u>*共享*</u>  
  
调用方式：  
  
1. 类名调用（推荐and常用）  
2. 对象名调用  
  
注意事项：  
  
1. 静态方法只能访问静态变量和其他的静态方法  
2. 非静态方法可以访问静态变量或静态方法，也可以访问非静态的成员变量和非静态的成员方法  
3. 静态方法中<u>没有this关键字</u>  
  
#### 2.final关键字  
  
final：表示最终，不可变。可以修饰变量、类、方法  
  
特点：  
  
- 只能赋值一次，数据不可变  
- 名字大写，多个单词下划线隔开  
  
#### 3.枚举  
  
枚举是一个特殊的Javabean类，这个类的对象是有限个  
  
使用场景：订单的状态、月份、星期......  
  
枚举关键字：enum  
  
```Java  
//枚举的定义格式  
public enum 枚举类型{  
  枚举项1，枚举项2，枚举项3；  
    属性    行为}  
  
//使用枚举对象，不要自己创建，直接调用就可以了  
枚举类名.枚举项；  
    eg：  
    //PAYMENT_PENDING：待支付  
    //SHIPPED：已发货  
    //CANCELLED：已取消  
public enum 类{  
    //这个类所有的对象  
    PAYMENT_PENDING("待支付")，SHIPPED("已发货")，CANCELLED("已取消")，PROCESSING("处理中");  
      
    private String name;  
      
    private 类(String name){  
        sout("看看我执行了吗？" + name)  
        this.name = name;  
    }  
}  
  
public class Test{  
    public static void main(String[] args){  
        类 o1 = 类.PROCESSING;  
        sout(o1.getName());  
    }  
}  
  
//执行结果：看看我执行了吗？待支付  
       //看看我执行了吗？已发货  
       //看看我执行了吗？已取消  
       //看看我执行了吗？处理中  
       //处理中  
```  
  
注意事项  
  
- 每一个枚举项，都是该枚举类的对象，每一个对象都是通过构造方法创造出来的  
- 枚举类在底层其实就是常量，默认用public static final 修饰  
- 枚举类的第一行必须是枚举项，枚举项之间用逗号隔开，以分号作为结尾  
- 枚举项的构造方法必须是private修饰，不让外界创建本类的对象  
- 编译器会给枚举类新增两个默认存在的方法：values（），valusOf（）  
  
### 3.面向对象高级  
  
#### 1.封装  
  
将零散的数据整合为一个整体  
  
#### 2.继承  
  
继承是类与类之间的一种父子关系，Java中提供关键字<u>*extends*</u>，用于建立类与类之间的关系。  
  
```java  
//继承格式  
public class 子类 extends 父类（超类）{  
}  
```  
  
继承的好处：可以把多个子类中重复的代码抽取到父类中，提高代码的复用性；子类可以在父类的基础上，增加其他的功能，使子类更强大。  
  
![image-20260330223158883](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20260330223158883.png)  
  
  
  
##### 如何设计继承体系  
  
​   当类与类之间，存在相同（共性）的内容，并满足子类是父类中的一种，就可以考虑使用继承来优化代码。    ![image-20260330223501108](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20260330223501108.png)  
  
​   设计流程图：  
  
![image-20260330223609272](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20260330223609272.png)  
  
继承的特点：  
  
​   Java只支持单继承，不支持多继承，但支持多层继承。  
  
​      直接继承的父类叫做直接父类，间接继承的爷爷叫做间接父类  
  
​      Java中的顶级父类为：Object，每一个类都直接或间接的继承于Object。  
  
![image-20260330223735930](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20260330223735930.png)  
  
顶级父类Object：所有类默认的最高级父类。  
  
![image-20260330223903739|230](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20260330223903739.png)  
  
##### 继承中的成员特点  
  
######  成员变量  
  
- 书写规则：把多个子类中相同的属性抽取到父类当中(抽取共性)  
- 调用规则：遵守就近原则  
  
|            关键字            | 作用 |  
| :--------------------------: | :--: |  
| this(先访问本类，在访问父类) | 本类 |  
|     super(直接访问父类)      | 父类 |  
  
```java  
public class Fu{  
    String name = "Fu";  
}  
  
public class Zi extends Fu{  
    String name = "Zi";  
    public void show(){  
        String name = "ziShow";  
        sout(name);       //ziShow   从局部位置开始往上找  
        sout(this.name);    //Zi      从本类成员位置往上找  
        sout(super.name);   //Fu      从父类成员位置往上找  
    }  
}  
```  
  
######  成员方法  
  
**方法的重写**  
  
​   方法重写：在子类中，把父类的方法再写一遍，方法申明保持一致  
  
​   使用场景：如果父类的方法不能满足子类的要求了，子类中可以把该方法再重写一遍。  
  
​   `重写的方法上需要加@Override注解，校验重写的语法是否争取`  
  
***注意事项和要求***  
  
1. 重写方法的名称、形参列表必须与父类中的一致，方法体按照实际需求书写  
2. **子类重写父类方法时，访问权限子类必须大于等于父类（空着不写<protected<public）**  
3. **子类重写父类方法时，返回值类型子类必须小于等于父类**。  
4. <u>建议：重写的方法申明和父类保持一致即可</u>  
5. final修饰类为最终类，里面所有的方法不能被重写  
6. private私有方法、static静态方法、final最终方法不能被重写  
  
##### 构造方法  
  
​   父类中的构造方法不会被子类继承，只能通过super关键字调用  
  
```java  
public class Zi extends Fu{  
    public Zi(){  
        super();             //调用无参构造  
    }  
    public Zi(String name,int age){  
        super(name,age);       //调用带参构造  
    }  
}  
```  
  
​   若子类的构造方法不写super，JVM也会加一个默认的super（），先访问父类的无参构造  
  
![image-20260330230319228](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20260330230319228.png)  
  
> 虚方法  
>  
> 就是普通的成员方法，非final、非static、非private修饰的方法  
  
##### Java中的权限修饰符  
  
​   权限修饰符：Java中的关键字，用来控制一个成员被访问的范围  
  
​   作用范围：private<空着不写<protected<public  
  
|  修饰符   | 同一个类 | 本包中其他类 | 不同包下的子类 | 不同包下的无关类 |  
| :-------: | :------: | :----------: | :------------: | :--------------: |  
|  private  |    √     |              |                |                  |  
| 空着不写  |    √     |      √       |                |                  |  
| protected |    √     |      √       |       √        |                  |  
|  public   |    √     |      √       |       √        |        √         |  
  
#### 3.多态  
  
​   多态：事物的多种形态  
  
​   表现形式：父类类型  对象名称 = new  子类对象；  
  
​   <!--eg：Fu f = new Zi（）；-->  
  
​   <!--eg：Ye f = new Fu（）；-->  
  
​   多态的前提：  
  
- 有继承/实现关系（必须的）  
- 有父类引用指向子类对象（必须的）  
- 有方法重写（可选的）  
  
```java  
public boolean register(Person per){  
    per.show();  
    //根据传递的对象，调用不同的show方法  
}  
```  
  
​   多态的好处:  
  
- 方法中使用父类型作为参数，可接收父类对象+所有子类对象  
- 如果进行方法重写，利用多态调用方法，可以调用不同子类中重写的方法  
  
###### 多态调用成员的特点★  
  
​   变量调用：编译看左边，运行也看左边  
  
    >编译看左边：在把Java文件编译成class文件的时候，看父类当中有没有这个**变量**，若有则编译成功，否则编译失败  
    >  
    >运行看左边：在代码真正运行的时候，使用父类中的变量  
  
​   方法调用：编译看左边，运行看右边  
  
> 编译看左边：在把Java文件编译成class文件的时候，看父类当中有没有这个**方法**，若有则编译成功，否则编译失败  
>  
> 运行看右边：在代码真正运行的时候，运行的是子类里面的方法，如果子类没有重写父类里的方法，使用的还是父类中的方法  
  
多态弊端：无法调用子类的特有方法  
  
解决方法——类型转换：  
  
- 自动类型转换（从子到父，向上转换）：子类对象赋值给父类类型的变量  
- 强制类型转换（从父到子，向下转换）：对象  对象变量  =  （子类）父类类型的变量  
  
```java  
Person p = new Student();  
Student s = (Student)p;  
```  
  
作用：可以解决多态的弊端，可以实现调用子类独有的功能  
  
###### 强制类型转换  
  
能解决的问题：可以转换成真正的子类类型，从而调用子类独有的功能  
  
转换时需要注意：转换类型与真实对象类型不一致会报错  
  
**解决方法：转换的时候使用instanceof关键字进行判断**  
  
```java  
class Test{  
    psvm{  
        //定义爷爷，父亲，儿子三个类型  
        Ye y = new Fu();  
        if(y instanceof Fu){    //判断一下y是不是父类类型的  
            Fu f = (Fu)y;  
        }  
        else{  
            sout("请确定好类型，再进行转换");  
        }  
    }  
}  
```  
  
#### 4.抽象类  
  
##### 抽象方法  
  
​   将共性的行为（方法）抽取到父类之后。因为每一个子类的方法体是不一样的，所以在父类中**不能确定具体的方法体**，该方法就可以定义为抽象方法  
  
##### 抽象类  
  
​   如果一个类中存在抽象方法，那么该类就必须声明为抽象类  
  
- 抽象类：public abstract class 类名{。。。}  
- 抽象方法：public abstract 返回值类型 方法名（参数列表）**；**  
  
注意事项：  
  
1. 抽象类不能实例化  
  
   ​       如果可以创建抽象类的对象的话，用对象调用一个没有方法体的抽象方法，没有任何意义  
  
2. 抽象类中不一定有抽象方法  
  
   ​       作用：为了不让外界创建本类的对象；有抽象方法的类一定是抽象类（正常的内容）  
  
3. 抽象类中可以有构造方法  
  
   ​       作用：给成员变量赋初值  
  
4. 抽象类的子类  
  
   ​       要么重写抽象类中所有的抽象方法  
  
   ​       要么子类也是抽象类  
  
   ​    `该行为意义不大，还要写一个孙子类继承子类，并且重写所有的抽象方法，在外界才可以创造孙子类的对象，调用里面的方法`  
  
#### 5.接口  
  
接口：接口就是一个规则，而且是独立于继承体系以外的规则（可以理解为干爹）  
  
格式：关键字interface来定义  
  
使用：接口和类之间的是实现关系，通过implements关键字实现  
  
```java  
public interface 接口名{...}  
public class 类名 implements 接口1，接口2，···{...}  
public class 类名 extends 父类{...}  
public class 子类 extends 父类 implements 接口{...}  
```  
  
注意点：  
  
1. 接口不能实例化  
2. 接口的子类（实现类），要么重写接口中所有的抽象方法，要么实现类是一个抽象类  
3. 一个类可以实现多个接口，也可以在继承一个类的同时，实现多个接口  
4. 如果一个类实现了多个接口，那么就要重写多个接口中所有的抽象方法  
  
###### 接口中成员的特点  
  
成员变量：只能是常量。默认修饰符：public static final  
  
构造方法：无  
  
成员方法：只能是抽象方法。默认修饰符：public abstract  
  
###### 接口和类之间的关系  
  
- 类和类之间的关系  
  - 继承关系，只能单继承，不能多继承，但是可以多层继承  
  
- 类和接口之间的关系  
  - 实现关系，可以单实现，也可以多实现，还可以在继承一个类的同时实现多个接口  
  - 注意点：  
    - 如果父类也是一个抽象类的话，那么在子类当中，需要把所有的抽象方法进行抽象，要么子类本身也是一个抽象类  
    - 如果在重写的时候出现了重复的抽象方法，此时我们只要重写一次就可以了  
  
- 接口和接口的关系  
  - 继承关系，可以单继承，也可以多继承  
  - 注意点  
    - 如果有一个接口A继承了多个接口，此时相当于是把接口中的抽象方法全部继承下来了，在以后实现类实现接口A的时候，就要把所有的抽象方法进行重写  
  
#### 6.内部类  
  
​   内部类：在一个类的里面，再定义一个类  
  
```Java  
public class Outer{       //外部類  
    public class Inner{    //内部類  
    }  
}  
```  
  
​   内部類存在的意義：内部類表示的事物是外部類的一部分，内部類單獨出現沒有任何意義  
  
​     
  
```Java  
public class Car{            //外部類  
    String caarBrand;  
    int carAge;  
    String carColor;  
      
    class Engine{            //内部類∈外部類  
        String engineBrand;  
        int engineAge;  
    }  
}  
```  
  
​     
  
##### 内部類的分類  
  
- 成員内部類    寫在成員位置的，屬於外部類的成員，可以被一些修飾符所修飾，也可以定義靜態變量  
  
  定義靜態變量格式：外部類名.内部類名 對象名 = 外部類對象.内部類對象；  
  
  eg:Outer.Inner oi = new Outer().new Inner();  
  
- 靜態内部類  
  
- 局部内部類  
  
  匿名内部類    Lambda表達式  方法引用（待续）  
      
  
### 异常处理  
  
#####   异常体系结构  
  
> Throwable  
> ├── Error（严重问题，如OutOfMemoryError，通常不捕获）  
> └── Exception  
>     ├── IOException（受检异常）  
>     ├── SQLException（受检异常）  
>     └── RuntimeException（非受检异常）  
>         ├── NullPointerException  
>         ├── ArrayIndexOutOfBoundsException  
>         ├── ClassCastException  
>         ├── IllegalArgumentException  
>         └── ArithmeticException  
  
- 受检异常：除了RuntimeException及其子类外的Exception。编译时必须处理（try-catch或throws）  
  
- 非受检异常：RuntimeException及其子类、Error。编译时不强制处理  
  
  ##### 异常处理关键字  
  
| 关键字  | 作用                                   | 使用位置       |  
| ------- | -------------------------------------- | -------------- |  
| try     | 监控可能抛出异常的代码块               | 方法内         |  
| catch   | 捕获并处理特定类型的异常               | 紧接try后      |  
| finally | 无论是否异常都执行的代码（清理资源）   | 可选，最多一个 |  
| throw   | 手动抛出异常对象                       | 方法体或代码块 |  
| throws  | 声明方法可能抛出的异常，交给调用者处理 | 方法声明后     |  
  
> 注意事项：异常对象被catch后，后续catch不会执行  
>  
> finally中的return会覆盖try/catch中的return（除非System.exit（））  
  
#####   **自定义异常**  
  
```java  
class MyException extends Exception { // 受检自定义异常  
    public MyException(String msg) { super(msg); }  
}  
// 使用时：throw new MyException("错误信息");  
```  
  
eg：编写一个方法，从键盘读入两个整数并计算它们的商。要求：1）捕获可能发生的算术异常和输入异常；2）无论是否异常，最后都输出“计算结束”。  
  
```java  
import java.util.Scanner;  
  
public class Division {  
    public static void main(String[] args) {  
        Scanner sc = new Scanner(System.in);  
        try {  
            System.out.print("请输入被除数: ");  
            int a = sc.nextInt();  
            System.out.print("请输入除数: ");  
            int b = sc.nextInt();  
            int result = a / b;  
            System.out.println("商: " + result);  
        } catch (ArithmeticException e) {  
            System.out.println("除数不能为零");  
        } catch (java.util.InputMismatchException e) {  
            System.out.println("输入格式错误，必须是整数");  
        } finally {  
            System.out.println("计算结束");  
            sc.close();  
        }  
    }  
}  
```  
  
  
  
### 集合框架  
  
#####   核心接口概览  
  
- Collection（单元素）  
  - List：有序、可重复；实现类：ArrayList（数组，查询快）、LinkedList（链表、增删快）  
  - Set：无序、不可重复；实现类：HashSet（哈希表，快速）、TreeSet（红黑树，排序）  
  - Queue：队列；实现类：LinkedList（双端）、PriorityQueue（优先级）  
  
- Map（键值对）  
  
  - HashMap：基于哈希表，无序  
  - TreeMap：基于红黑树，按键排序  
  - LinkedHashMap：基于哈希表+双向链表，按插入/访问顺序  
  
  ##### 常用方法  
  
  | 方法                | 说明              | 适用于     |  
  | ------------------- | ----------------- | ---------- |  
  | add(E e)            | 添加元素          | Collection |  
  | remove(Object o)    | 移除元素          | Collection |  
  | size()              | 元素个数          | Collection |  
  | contains(Object o)  | 是否包含          | Collection |  
  | get(int index)      | 获取指定索引元素  | List       |  
  | put(K key, V value) | 放入键值对        | Map        |  
  | get(Object key)     | 根据键获取值      | Map        |  
  | keySet()            | 返回键的Set视图   | Map        |  
  | entrySet()          | 返回键值对Set视图 | Map        |  
  
  ##### 遍历方式  
  
  List/Set：增强for循环、Iterator迭代器  
  
  Map：map.keySet（） + for-each；map.entrySet（）+ 增强for；map.forEach（（k，v）—>{}）（JDK8）  
  
  ##### 比较器  
  
  | 比较     | Comparable         | Comparator              |  
  | -------- | ------------------ | ----------------------- |  
  | 位置     | 实体类内部实现     | 外部单独类或Lambda      |  
  | 方法     | int compareTo(T o) | int compare(T o1, T o2) |  
  | 排序方式 | 自然排序（唯一）   | 定制排序（可多个）      |  
  
  ```java  
  // 实现Comparable  
  class Student implements Comparable<Student> {  
      int score;  
      public int compareTo(Student o) { return this.score - o.score; }  
  }  
    
  // 使用Comparator排序  
  list.sort((s1, s2) -> s2.score - s1.score); // 降序  
  ```  
  
  ##### 集合与数组互转  
  
  ```java  
  // 数组 → List  
  String[] arr = {"a","b"};  
  List<String> list = Arrays.asList(arr); // 注意：不能增删，但可改  
  // 可变List  
  List<String> list2 = new ArrayList<>(Arrays.asList(arr));  
    
  // List → 数组  
  String[] arr2 = list.toArray(new String[0]);  
  ```  
  
  eg：有一个Student类（属性name, score），要求：1）创建一个TreeSet，按score从高到低排序（如果score相同按name自然排序）；2）添加若干学生；3）使用增强for遍历并输出。  
  
  ```java  
  import java.util.*;  
    
  class Student {  
      String name;  
      int score;  
      Student(String name, int score) { this.name = name; this.score = score; }  
      public String toString() { return name + ": " + score; }  
  }  
    
  public class Test {  
      public static void main(String[] args) {  
          // 使用Comparator定制排序  
          Set<Student> set = new TreeSet<>((s1, s2) -> {  
              int cmp = s2.score - s1.score; // 降序  
              if (cmp == 0) cmp = s1.name.compareTo(s2.name); // 同名次按姓名升序  
              return cmp;  
          });  
            
          set.add(new Student("Tom", 85));  
          set.add(new Student("Alice", 90));  
          set.add(new Student("Bob", 85));  
            
          for (Student s : set) {  
              System.out.println(s);  
          }  
      }  
  }  
  // 输出：Alice: 90  Tom: 85  Bob: 85  
  ```  
  
  
  
### 多线程开发  
  
#####   线程的创建方式  
  
1. 继承Thread类：重写run（），直接new MyThread（）.start（）  
2. 实现Runnable接口：作为任务传入new Thread（new MyRunnable（））.start（）  
3. 实现Callable接口（配合FuterTask）：带返回值，可抛异常  
4. 使用线程池：ExecutorService 提交Runnable或Callable  
  
推荐：实现Runnable和Callable，避免单继承限制，更灵活。  
  
#####   线程生命周期  
  
​   NEW → RUNNABLE → BLOCKED/WAITING/TIMED_WAITING → TERMINATED  
  
- NEW：新建未启动  
  
- RUNNABLE：可运行（包含就绪和运行）  
  
- BLOCKED：无限等待（wait/join/park）  
  
- TIMED_WAITING：有等待时限（sleep/wait（timeout））  
  
- TERMINARED：执行结束  
  
  ##### 线程同步  
  
  1.synchronized关键字  
  
- 修饰实例方法：锁是当前实例对象this  
  
- 修饰静态方法：锁是类的class对象  
  
- 同步代码块：可指定任意对象作为锁  
  
  作用：保证原子性、可见性、有序性  
  2.Lock接口  
  
```java  
Lock lock = new ReentrantLock();  
lock.lock();  
try { // 临界区 } finally { lock.unlock(); }  
```  
  
​      区别：可中断、可超时、公平锁、多个Condition条件  
  
​      3.volatile关键字  
  
- 保证可见性（每次读从主存刷新，写立即刷回）  
  
- 不保证原子性  
  
- 使用场景：状态标志位、单例双重检查锁中的instance  
  
  ##### 线程间通信  
  
- wait/notify/notifyAll：必须在同步块内调用；wait释放锁，notify随机唤醒一个等待线程  
  
- Condition：配合Lock，更灵活  
  
- BlockingQueue：阻塞队列，自动实现生产者-消费者  
  
  ##### 线程池  
  
  核心参数：  
```java  
new ThreadPoolExecutor(corePoolSize, maximumPoolSize, keepAliveTime, unit, workQueue, threadFactory, handler);  
```  
  
​      **工作流程**：  
  
1. 核心线程未满 → 创建核心线程执行  
2. 队列未满 → 入队等待  
3. 线程数未达最大 → 创建非核心线程  
4. 触发拒绝策略  
  
**四种拒绝策略**：  
  
- AbortPolicy：抛异常（默认）  
- CallerRunsPolicy：调用者线程执行  
- DiscardPolicy：直接丢弃  
- DiscardOldestPolicy：丢弃最旧任务  
  
**常用线程池**（不推荐Executors快速创建，可能OOM）：  
  
```java  
ExecutorService pool = new ThreadPoolExecutor(5, 10, 60L, TimeUnit.SECONDS,  
    new LinkedBlockingQueue<>(100));  
```  
  
#####         死锁  
  
​   四个必要条件：互斥、持有并等待、不可剥夺、循环等待  
  
​   预防：锁排序、尝试超时锁、避免嵌套  
  
​   eg：编写程序，模拟银行账户取款操作：两个线程同时从一个初始余额为1000的账户中取款500元，要求线程安全，避免超取。使用synchronized实现。  
  
```java  
class Account {  
    private int balance = 1000;  
    public synchronized void withdraw(int amount) {  
        if (balance >= amount) {  
            System.out.println(Thread.currentThread().getName() + " 开始取款");  
            try { Thread.sleep(100); } catch (InterruptedException e) {}  
            balance -= amount;  
            System.out.println("取款成功，余额: " + balance);  
        } else {  
            System.out.println("余额不足");  
        }  
    }  
}  
  
public class BankTest {  
    public static void main(String[] args) {  
        Account account = new Account();  
        Runnable task = () -> account.withdraw(500);  
        new Thread(task, "线程A").start();  
        new Thread(task, "线程B").start();  
    }  
}  
```# 耿瓦的Java笔记😒  
  
### 1.面向对象  
  
面向对象：利用对象进行软件开发。  
  
对象：顾名思义，创建的东西。<u>把相关的数据和方法组织为一个整体来看待。</u>eg：  
  
```Java  
public class Note{  
      
    public class man{  
        String name;  
        int age;  
        char sex;  
    }  
      
    public static void main(String[] args){  
        System.out.println("这里创造的man就是对象,name，age，sex为创建的属性。  
                           注意，同一类事物的属性必须是一致的。");  
    }  
}   
```  
  
  
  
#### 1.类和对象  
  
1. 类中所有的属性只定义，不赋值。  
  
2. 创建对象，记录单独个体的所有信息。（即new一个对象）  
  
3. 格式：  
  
   ```java  
   public class Dog{  
       String name;  
       ......  
   }  
     
     
   public class Test{  
       public static void main(String[] args){  
           Dog xuewei = new Dog;  
           xuewei.name = "周友翔";  
           ......  
       }  
   }  
   ```  
  
#### 2.Javabean  
  
描述一类事物的类叫Javabean类（无main方法，仅创造对象）。（记住就行了别问我也不知道这什么玩意）  
  
Javabean类可以写属性和行为。  
  
  
  
#### 3.面向对象中的数据安全（private关键字）  
  
private关键字是一个权限修饰符，可以修饰<u>成员变量</u>（变量）和<u>成员方法</u>(行为）。  
  
```Java  
public class xueWei{  
    String name; //成员变量  
    ...  
}  
  
  
public void Print(){  
    System.out.print("zyx is a renji"); //成员方法  
}  
```  
  
特点：一旦被private修饰，只能在本类中访问，外界无法访问。  
  
使用get/set方法  
  
get方法：取值       set方法：赋值  
  
  
  
#### 4.就近原则与this关键字  
  
就近原则：在方法当中直接使用变量查找顺序：先找局部变量，再找成员变量。  
  
若想直接使用成员变量，则格式为：this.局部变量  
  
```java  
System.out.print(age); //局部变量  
System.out.print(this.age); //成员变量  
```  
  
  
  
#### 5.构造方法  
  
构造方法也叫做构造器、构造函数  
  
作用：在创建对象的时候给成员变量进行初始化的  
  
格式：  
  
```  
修饰符  类名（参数）  {  
       方法体；  
}  
```  
  
```Java  
Student s1 = new Student(); //调用空参方法  
Student s2 = new Student(); //调用有参方法  
```  
  
特点：  
  
- 方法名与类名相同，大小写也要一致  
- 没有返回值类型，连void都没有  
- 没有具体的返回值（不能由return带回结果数据）  
  
执行时机：  
  
- 创建对象的时候由虚拟机调用，不能手动调用构造方法  
- 每创建一次对象，就会调用一次构造方法  
  
*注意事项：*  
  
- *如果没有定义构造方法，系统将给出一个默认的无参构数构造方法*  
- *如果自己写了任意构造方法，系统将不再提供默认的构造方法*  
- *带参构造方法和无参构造方法，两者方法名相同，但是参数不同，这叫做构造方法的<u>重载</u>*  
- *习惯：无论是否使用，都手动书写无参数构造方法，和带全部参数的构造方法*  
  
  
  
#### 6.重写toString方法  
  
```java  
@Override  
    public String toString(){  
        syso("返回语句")  
    }  
```  
  
toString方法一般都会重写，返回输出语句。  
  
  
  
### 2.面向对象进阶  
  
#### 1.static修饰成员变量  
  
static：<u>表示静态</u>，是Java的修饰符，用来修饰成员变量/成员方法（多用于测试类和工具类中，Javabean类中很少会用）  
  
  
  
> 补充  
>  
> 工具类：不是用来描述一类事物的，也没有main方法，而是帮我们做一些事情的类  
>  
> ```java  
> public class Test{  
>     public static void main(String[] args){  
>         int[] arr = {1,2,3,4,5};  
>         //遍历数组  
>         //求最大值  
>         //求最小值  
>         ...  
>     }  
> }  
> ```  
>  
> 将遍历数组等功能单拉出来组成一个新的<u>public class Tools{}</u>，就是工具类，需要时可随时调用  
  
> 工具类书写方式：  
>  
> 1. 类名见名之意  
> 2. 私有化构造方法  
>  
> ```Java  
> public class ArrayUtil{  
>   private ArrUtil(){  
>      public static int getMax(){}  
>         public static int getSum(){}  
>         public static int getMin(){}  
>   }  
> }  
> ```  
>  
>   3.方法定义为静态  
  
特点：叫做静态变量，被该类所有对象<u>*共享*</u>  
  
调用方式：  
  
1. 类名调用（推荐and常用）  
2. 对象名调用  
  
注意事项：  
  
1. 静态方法只能访问静态变量和其他的静态方法  
2. 非静态方法可以访问静态变量或静态方法，也可以访问非静态的成员变量和非静态的成员方法  
3. 静态方法中<u>没有this关键字</u>  
  
#### 2.final关键字  
  
final：表示最终，不可变。可以修饰变量、类、方法  
  
特点：  
  
- 只能赋值一次，数据不可变  
- 名字大写，多个单词下划线隔开  
  
#### 3.枚举  
  
枚举是一个特殊的Javabean类，这个类的对象是有限个  
  
使用场景：订单的状态、月份、星期......  
  
枚举关键字：enum  
  
```Java  
//枚举的定义格式  
public enum 枚举类型{  
  枚举项1，枚举项2，枚举项3；  
    属性    行为}  
  
//使用枚举对象，不要自己创建，直接调用就可以了  
枚举类名.枚举项；  
    eg：  
    //PAYMENT_PENDING：待支付  
    //SHIPPED：已发货  
    //CANCELLED：已取消  
public enum 类{  
    //这个类所有的对象  
    PAYMENT_PENDING("待支付")，SHIPPED("已发货")，CANCELLED("已取消")，PROCESSING("处理中");  
      
    private String name;  
      
    private 类(String name){  
        sout("看看我执行了吗？" + name)  
        this.name = name;  
    }  
}  
  
public class Test{  
    public static void main(String[] args){  
        类 o1 = 类.PROCESSING;  
        sout(o1.getName());  
    }  
}  
  
//执行结果：看看我执行了吗？待支付  
       //看看我执行了吗？已发货  
       //看看我执行了吗？已取消  
       //看看我执行了吗？处理中  
       //处理中  
```  
  
注意事项  
  
- 每一个枚举项，都是该枚举类的对象，每一个对象都是通过构造方法创造出来的  
- 枚举类在底层其实就是常量，默认用public static final 修饰  
- 枚举类的第一行必须是枚举项，枚举项之间用逗号隔开，以分号作为结尾  
- 枚举项的构造方法必须是private修饰，不让外界创建本类的对象  
- 编译器会给枚举类新增两个默认存在的方法：values（），valusOf（）  
  
### 3.面向对象高级  
  
#### 1.封装  
  
将零散的数据整合为一个整体  
  
#### 2.继承  
  
继承是类与类之间的一种父子关系，Java中提供关键字<u>*extends*</u>，用于建立类与类之间的关系。  
  
```java  
//继承格式  
public class 子类 extends 父类（超类）{  
}  
```  
  
继承的好处：可以把多个子类中重复的代码抽取到父类中，提高代码的复用性；子类可以在父类的基础上，增加其他的功能，使子类更强大。  
  
![image-20260330223158883](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20260330223158883.png)  
  
  
  
##### 如何设计继承体系  
  
​   当类与类之间，存在相同（共性）的内容，并满足子类是父类中的一种，就可以考虑使用继承来优化代码。    ![image-20260330223501108](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20260330223501108.png)  
  
​   设计流程图：  
  
![image-20260330223609272](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20260330223609272.png)  
  
继承的特点：  
  
​   Java只支持单继承，不支持多继承，但支持多层继承。  
  
​      直接继承的父类叫做直接父类，间接继承的爷爷叫做间接父类  
  
​      Java中的顶级父类为：Object，每一个类都直接或间接的继承于Object。  
  
![image-20260330223735930](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20260330223735930.png)  
  
顶级父类Object：所有类默认的最高级父类。  
  
![image-20260330223903739](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20260330223903739.png)  
  
##### 继承中的成员特点  
  
######  成员变量  
  
- 书写规则：把多个子类中相同的属性抽取到父类当中(抽取共性)  
- 调用规则：遵守就近原则  
  
|            关键字            | 作用 |  
| :--------------------------: | :--: |  
| this(先访问本类，在访问父类) | 本类 |  
|     super(直接访问父类)      | 父类 |  
  
```java  
public class Fu{  
    String name = "Fu";  
}  
  
public class Zi extends Fu{  
    String name = "Zi";  
    public void show(){  
        String name = "ziShow";  
        sout(name);       //ziShow   从局部位置开始往上找  
        sout(this.name);    //Zi      从本类成员位置往上找  
        sout(super.name);   //Fu      从父类成员位置往上找  
    }  
}  
```  
  
######  成员方法  
  
**方法的重写**  
  
​   方法重写：在子类中，把父类的方法再写一遍，方法申明保持一致  
  
​   使用场景：如果父类的方法不能满足子类的要求了，子类中可以把该方法再重写一遍。  
  
​   `重写的方法上需要加@Override注解，校验重写的语法是否争取`  
  
***注意事项和要求***  
  
1. 重写方法的名称、形参列表必须与父类中的一致，方法体按照实际需求书写  
2. **子类重写父类方法时，访问权限子类必须大于等于父类（空着不写<protected<public）**  
3. **子类重写父类方法时，返回值类型子类必须小于等于父类**。  
4. <u>建议：重写的方法申明和父类保持一致即可</u>  
5. final修饰类为最终类，里面所有的方法不能被重写  
6. private私有方法、static静态方法、final最终方法不能被重写  
  
##### 构造方法  
  
​   父类中的构造方法不会被子类继承，只能通过super关键字调用  
  
```java  
public class Zi extends Fu{  
    public Zi(){  
        super();             //调用无参构造  
    }  
    public Zi(String name,int age){  
        super(name,age);       //调用带参构造  
    }  
}  
```  
  
​   若子类的构造方法不写super，JVM也会加一个默认的super（），先访问父类的无参构造  
  
![image-20260330230319228](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20260330230319228.png)  
  
> 虚方法  
>  
> 就是普通的成员方法，非final、非static、非private修饰的方法  
  
##### Java中的权限修饰符  
  
​   权限修饰符：Java中的关键字，用来控制一个成员被访问的范围  
  
​   作用范围：private<空着不写<protected<public  
  
|  修饰符   | 同一个类 | 本包中其他类 | 不同包下的子类 | 不同包下的无关类 |  
| :-------: | :------: | :----------: | :------------: | :--------------: |  
|  private  |    √     |              |                |                  |  
| 空着不写  |    √     |      √       |                |                  |  
| protected |    √     |      √       |       √        |                  |  
|  public   |    √     |      √       |       √        |        √         |  
  
#### 3.多态  
  
​   多态：事物的多种形态  
  
​   表现形式：父类类型  对象名称 = new  子类对象；  
  
​   <!--eg：Fu f = new Zi（）；-->  
  
​   <!--eg：Ye f = new Fu（）；-->  
  
​   多态的前提：  
  
- 有继承/实现关系（必须的）  
- 有父类引用指向子类对象（必须的）  
- 有方法重写（可选的）  
  
```java  
public boolean register(Person per){  
    per.show();  
    //根据传递的对象，调用不同的show方法  
}  
```  
  
​   多态的好处:  
  
- 方法中使用父类型作为参数，可接收父类对象+所有子类对象  
- 如果进行方法重写，利用多态调用方法，可以调用不同子类中重写的方法  
  
###### 多态调用成员的特点★  
  
​   变量调用：编译看左边，运行也看左边  
  
    >编译看左边：在把Java文件编译成class文件的时候，看父类当中有没有这个**变量**，若有则编译成功，否则编译失败  
    >  
    >运行看左边：在代码真正运行的时候，使用父类中的变量  
  
​   方法调用：编译看左边，运行看右边  
  
> 编译看左边：在把Java文件编译成class文件的时候，看父类当中有没有这个**方法**，若有则编译成功，否则编译失败  
>  
> 运行看右边：在代码真正运行的时候，运行的是子类里面的方法，如果子类没有重写父类里的方法，使用的还是父类中的方法  
  
多态弊端：无法调用子类的特有方法  
  
解决方法——类型转换：  
  
- 自动类型转换（从子到父，向上转换）：子类对象赋值给父类类型的变量  
- 强制类型转换（从父到子，向下转换）：对象  对象变量  =  （子类）父类类型的变量  
  
```java  
Person p = new Student();  
Student s = (Student)p;  
```  
  
作用：可以解决多态的弊端，可以实现调用子类独有的功能  
  
###### 强制类型转换  
  
能解决的问题：可以转换成真正的子类类型，从而调用子类独有的功能  
  
转换时需要注意：转换类型与真实对象类型不一致会报错  
  
**解决方法：转换的时候使用instanceof关键字进行判断**  
  
```java  
class Test{  
    psvm{  
        //定义爷爷，父亲，儿子三个类型  
        Ye y = new Fu();  
        if(y instanceof Fu){    //判断一下y是不是父类类型的  
            Fu f = (Fu)y;  
        }  
        else{  
            sout("请确定好类型，再进行转换");  
        }  
    }  
}  
```  
  
#### 4.抽象类  
  
##### 抽象方法  
  
​   将共性的行为（方法）抽取到父类之后。因为每一个子类的方法体是不一样的，所以在父类中**不能确定具体的方法体**，该方法就可以定义为抽象方法  
  
##### 抽象类  
  
​   如果一个类中存在抽象方法，那么该类就必须声明为抽象类  
  
- 抽象类：public abstract class 类名{。。。}  
- 抽象方法：public abstract 返回值类型 方法名（参数列表）**；**  
  
注意事项：  
  
1. 抽象类不能实例化  
  
   ​       如果可以创建抽象类的对象的话，用对象调用一个没有方法体的抽象方法，没有任何意义  
  
2. 抽象类中不一定有抽象方法  
  
   ​       作用：为了不让外界创建本类的对象；有抽象方法的类一定是抽象类（正常的内容）  
  
3. 抽象类中可以有构造方法  
  
   ​       作用：给成员变量赋初值  
  
4. 抽象类的子类  
  
   ​       要么重写抽象类中所有的抽象方法  
  
   ​       要么子类也是抽象类  
  
   ​    `该行为意义不大，还要写一个孙子类继承子类，并且重写所有的抽象方法，在外界才可以创造孙子类的对象，调用里面的方法`  
  
#### 5.接口  
  
接口：接口就是一个规则，而且是独立于继承体系以外的规则（可以理解为干爹）  
  
格式：关键字interface来定义  
  
使用：接口和类之间的是实现关系，通过implements关键字实现  
  
```java  
public interface 接口名{...}  
public class 类名 implements 接口1，接口2，···{...}  
public class 类名 extends 父类{...}  
public class 子类 extends 父类 implements 接口{...}  
```  
  
注意点：  
  
1. 接口不能实例化  
2. 接口的子类（实现类），要么重写接口中所有的抽象方法，要么实现类是一个抽象类  
3. 一个类可以实现多个接口，也可以在继承一个类的同时，实现多个接口  
4. 如果一个类实现了多个接口，那么就要重写多个接口中所有的抽象方法  
  
###### 接口中成员的特点  
  
成员变量：只能是常量。默认修饰符：public static final  
  
构造方法：无  
  
成员方法：只能是抽象方法。默认修饰符：public abstract  
  
###### 接口和类之间的关系  
  
- 类和类之间的关系  
  - 继承关系，只能单继承，不能多继承，但是可以多层继承  
  
- 类和接口之间的关系  
  - 实现关系，可以单实现，也可以多实现，还可以在继承一个类的同时实现多个接口  
  - 注意点：  
    - 如果父类也是一个抽象类的话，那么在子类当中，需要把所有的抽象方法进行抽象，要么子类本身也是一个抽象类  
    - 如果在重写的时候出现了重复的抽象方法，此时我们只要重写一次就可以了  
  
- 接口和接口的关系  
  - 继承关系，可以单继承，也可以多继承  
  - 注意点  
    - 如果有一个接口A继承了多个接口，此时相当于是把接口中的抽象方法全部继承下来了，在以后实现类实现接口A的时候，就要把所有的抽象方法进行重写  
  
#### 6.内部类  
  
​   内部类：在一个类的里面，再定义一个类  
  
```Java  
public class Outer{       //外部類  
    public class Inner{    //内部類  
    }  
}  
```  
  
​   内部類存在的意義：内部類表示的事物是外部類的一部分，内部類單獨出現沒有任何意義  
  
​     
  
```Java  
public class Car{            //外部類  
    String caarBrand;  
    int carAge;  
    String carColor;  
      
    class Engine{            //内部類∈外部類  
        String engineBrand;  
        int engineAge;  
    }  
}  
```  
  
​     
  
##### 内部類的分類  
  
- 成員内部類    寫在成員位置的，屬於外部類的成員，可以被一些修飾符所修飾，也可以定義靜態變量  
  
  定義靜態變量格式：外部類名.内部類名 對象名 = 外部類對象.内部類對象；  
  
  eg:Outer.Inner oi = new Outer().new Inner();  
  
- 靜態内部類  
  
- 局部内部類  
  
  匿名内部類    Lambda表達式  方法引用（待续）  
      
  
### 异常处理  
  
#####   异常体系结构  
  
> Throwable  
> ├── Error（严重问题，如OutOfMemoryError，通常不捕获）  
> └── Exception  
>     ├── IOException（受检异常）  
>     ├── SQLException（受检异常）  
>     └── RuntimeException（非受检异常）  
>         ├── NullPointerException  
>         ├── ArrayIndexOutOfBoundsException  
>         ├── ClassCastException  
>         ├── IllegalArgumentException  
>         └── ArithmeticException  
  
- 受检异常：除了RuntimeException及其子类外的Exception。编译时必须处理（try-catch或throws）  
  
- 非受检异常：RuntimeException及其子类、Error。编译时不强制处理  
  
  ##### 异常处理关键字  
  
| 关键字  | 作用                                   | 使用位置       |  
| ------- | -------------------------------------- | -------------- |  
| try     | 监控可能抛出异常的代码块               | 方法内         |  
| catch   | 捕获并处理特定类型的异常               | 紧接try后      |  
| finally | 无论是否异常都执行的代码（清理资源）   | 可选，最多一个 |  
| throw   | 手动抛出异常对象                       | 方法体或代码块 |  
| throws  | 声明方法可能抛出的异常，交给调用者处理 | 方法声明后     |  
  
> 注意事项：异常对象被catch后，后续catch不会执行  
>  
> finally中的return会覆盖try/catch中的return（除非System.exit（））  
  
#####   **自定义异常**  
  
```java  
class MyException extends Exception { // 受检自定义异常  
    public MyException(String msg) { super(msg); }  
}  
// 使用时：throw new MyException("错误信息");  
```  
  
eg：编写一个方法，从键盘读入两个整数并计算它们的商。要求：1）捕获可能发生的算术异常和输入异常；2）无论是否异常，最后都输出“计算结束”。  
  
```java  
import java.util.Scanner;  
  
public class Division {  
    public static void main(String[] args) {  
        Scanner sc = new Scanner(System.in);  
        try {  
            System.out.print("请输入被除数: ");  
            int a = sc.nextInt();  
            System.out.print("请输入除数: ");  
            int b = sc.nextInt();  
            int result = a / b;  
            System.out.println("商: " + result);  
        } catch (ArithmeticException e) {  
            System.out.println("除数不能为零");  
        } catch (java.util.InputMismatchException e) {  
            System.out.println("输入格式错误，必须是整数");  
        } finally {  
            System.out.println("计算结束");  
            sc.close();  
        }  
    }  
}  
```  
  
  
  
### 集合框架  
  
#####   核心接口概览  
  
- Collection（单元素）  
  - List：有序、可重复；实现类：ArrayList（数组，查询快）、LinkedList（链表、增删快）  
  - Set：无序、不可重复；实现类：HashSet（哈希表，快速）、TreeSet（红黑树，排序）  
  - Queue：队列；实现类：LinkedList（双端）、PriorityQueue（优先级）  
  
- Map（键值对）  
  
  - HashMap：基于哈希表，无序  
  - TreeMap：基于红黑树，按键排序  
  - LinkedHashMap：基于哈希表+双向链表，按插入/访问顺序  
  
  ##### 常用方法  
  
  | 方法                | 说明              | 适用于     |  
  | ------------------- | ----------------- | ---------- |  
  | add(E e)            | 添加元素          | Collection |  
  | remove(Object o)    | 移除元素          | Collection |  
  | size()              | 元素个数          | Collection |  
  | contains(Object o)  | 是否包含          | Collection |  
  | get(int index)      | 获取指定索引元素  | List       |  
  | put(K key, V value) | 放入键值对        | Map        |  
  | get(Object key)     | 根据键获取值      | Map        |  
  | keySet()            | 返回键的Set视图   | Map        |  
  | entrySet()          | 返回键值对Set视图 | Map        |  
  
  ##### 遍历方式  
  
  List/Set：增强for循环、Iterator迭代器  
  
  Map：map.keySet（） + for-each；map.entrySet（）+ 增强for；map.forEach（（k，v）—>{}）（JDK8）  
  
  ##### 比较器  
  
  | 比较     | Comparable         | Comparator              |  
  | -------- | ------------------ | ----------------------- |  
  | 位置     | 实体类内部实现     | 外部单独类或Lambda      |  
  | 方法     | int compareTo(T o) | int compare(T o1, T o2) |  
  | 排序方式 | 自然排序（唯一）   | 定制排序（可多个）      |  
  
  ```java  
  // 实现Comparable  
  class Student implements Comparable<Student> {  
      int score;  
      public int compareTo(Student o) { return this.score - o.score; }  
  }  
    
  // 使用Comparator排序  
  list.sort((s1, s2) -> s2.score - s1.score); // 降序  
  ```  
  
  ##### 集合与数组互转  
  
  ```java  
  // 数组 → List  
  String[] arr = {"a","b"};  
  List<String> list = Arrays.asList(arr); // 注意：不能增删，但可改  
  // 可变List  
  List<String> list2 = new ArrayList<>(Arrays.asList(arr));  
    
  // List → 数组  
  String[] arr2 = list.toArray(new String[0]);  
  ```  
  
  eg：有一个Student类（属性name, score），要求：1）创建一个TreeSet，按score从高到低排序（如果score相同按name自然排序）；2）添加若干学生；3）使用增强for遍历并输出。  
  
  ```java  
  import java.util.*;  
    
  class Student {  
      String name;  
      int score;  
      Student(String name, int score) { this.name = name; this.score = score; }  
      public String toString() { return name + ": " + score; }  
  }  
    
  public class Test {  
      public static void main(String[] args) {  
          // 使用Comparator定制排序  
          Set<Student> set = new TreeSet<>((s1, s2) -> {  
              int cmp = s2.score - s1.score; // 降序  
              if (cmp == 0) cmp = s1.name.compareTo(s2.name); // 同名次按姓名升序  
              return cmp;  
          });  
            
          set.add(new Student("Tom", 85));  
          set.add(new Student("Alice", 90));  
          set.add(new Student("Bob", 85));  
            
          for (Student s : set) {  
              System.out.println(s);  
          }  
      }  
  }  
  // 输出：Alice: 90  Tom: 85  Bob: 85  
  ```  
  
  
  
### 多线程开发  
  
#####   线程的创建方式  
  
1. 继承Thread类：重写run（），直接new MyThread（）.start（）  
2. 实现Runnable接口：作为任务传入new Thread（new MyRunnable（））.start（）  
3. 实现Callable接口（配合FuterTask）：带返回值，可抛异常  
4. 使用线程池：ExecutorService 提交Runnable或Callable  
  
推荐：实现Runnable和Callable，避免单继承限制，更灵活。  
  
#####   线程生命周期  
  
​   NEW → RUNNABLE → BLOCKED/WAITING/TIMED_WAITING → TERMINATED  
  
- NEW：新建未启动  
  
- RUNNABLE：可运行（包含就绪和运行）  
  
- BLOCKED：无限等待（wait/join/park）  
  
- TIMED_WAITING：有等待时限（sleep/wait（timeout））  
  
- TERMINARED：执行结束  
  
  ##### 线程同步  
  
  1.synchronized关键字  
  
- 修饰实例方法：锁是当前实例对象this  
  
- 修饰静态方法：锁是类的class对象  
  
- 同步代码块：可指定任意对象作为锁  
  
  作用：保证原子性、可见性、有序性  
  2.Lock接口  
  
```java  
Lock lock = new ReentrantLock();  
lock.lock();  
try { // 临界区 } finally { lock.unlock(); }  
```  
  
​      区别：可中断、可超时、公平锁、多个Condition条件  
  
​      3.volatile关键字  
  
- 保证可见性（每次读从主存刷新，写立即刷回）  
  
- 不保证原子性  
  
- 使用场景：状态标志位、单例双重检查锁中的instance  
  
  ##### 线程间通信  
  
- wait/notify/notifyAll：必须在同步块内调用；wait释放锁，notify随机唤醒一个等待线程  
  
- Condition：配合Lock，更灵活  
  
- BlockingQueue：阻塞队列，自动实现生产者-消费者  
  
  ##### 线程池  
  
  核心参数：  
```java  
new ThreadPoolExecutor(corePoolSize, maximumPoolSize, keepAliveTime, unit, workQueue, threadFactory, handler);  
```  
  
​      **工作流程**：  
  
1. 核心线程未满 → 创建核心线程执行  
2. 队列未满 → 入队等待  
3. 线程数未达最大 → 创建非核心线程  
4. 触发拒绝策略  
  
**四种拒绝策略**：  
  
- AbortPolicy：抛异常（默认）  
- CallerRunsPolicy：调用者线程执行  
- DiscardPolicy：直接丢弃  
- DiscardOldestPolicy：丢弃最旧任务  
  
**常用线程池**（不推荐Executors快速创建，可能OOM）：  
  
```java  
ExecutorService pool = new ThreadPoolExecutor(5, 10, 60L, TimeUnit.SECONDS,  
    new LinkedBlockingQueue<>(100));  
```  
  
#####         死锁  
  
​   四个必要条件：互斥、持有并等待、不可剥夺、循环等待  
  
​   预防：锁排序、尝试超时锁、避免嵌套  
  
​   eg：编写程序，模拟银行账户取款操作：两个线程同时从一个初始余额为1000的账户中取款500元，要求线程安全，避免超取。使用synchronized实现。  
  
```java  
class Account {  
    private int balance = 1000;  
    public synchronized void withdraw(int amount) {  
        if (balance >= amount) {  
            System.out.println(Thread.currentThread().getName() + " 开始取款");  
            try { Thread.sleep(100); } catch (InterruptedException e) {}  
            balance -= amount;  
            System.out.println("取款成功，余额: " + balance);  
        } else {  
            System.out.println("余额不足");  
        }  
    }  
}  
  
public class BankTest {  
    public static void main(String[] args) {  
        Account account = new Account();  
        Runnable task = () -> account.withdraw(500);  
        new Thread(task, "线程A").start();  
        new Thread(task, "线程B").start();  
    }  
}  
```
