---
title: Java之继承
date: 2017-03-09 09:50:41
tags: Java
---
## 继承
### 定义
继承是类与类的一种关系，是一种“is a”的关系。  
继承是从已有的类中派生出新的类，新的类能吸收已有类的数据属性和行为，并能扩展新能力。
### 语法  
```Java
class 子类 extends 父类{}
```
### 规则
1. 子类继承父类时，子类是不可以继承父类的构造函数，必须调用父类的构造函数  
具有两种情况：  
第一种：隐含super()形式，父类具有无参构造器或默认构造器

```Java
class A{} //父类具有默认的构造器
class B extends A{
    super(); //可以省略
}
```
或者
```
class A{
  public A(){
    System.out.print("父类无参构造器");
  }
}
class B extends A{  	 
  public B(){
    super(); //可以省略
    System.out.print("子类无参构造器");
  }
}
```
 结果显示：父类无参构造器  
　　　　　子类无参构造器  
第二种：显示super()形式，父类具有有参构造器，super(参数)；一定要放在构造方法的首行上。
```
class A{
    public A(String name){
        System.out.print("父类有参构造器");
  	}
}
class B extends A{
    public B(){
        super("lzl"); //不可省略，()中的内容可任意，只要符合String类型，必须在首行
        System.out.print("子类无参构造器");
  	}
 }
public class Test{
    public static void main(String[] args){
        B b = new B();
    }
}
```
结果显示：父类有参构造器  
　　　　　子类无参构造器  
如果要实例化子类对象，会默认先调用父类构造，为父类之中的属性初始化，之后再调用子类构造，为子类之中的属性初始化，即：默认情况下，子类会找到父类之中的无参构造方法。  
2. 继承只能是单继承，但存在多层继承
```
class C extends A,B{}
```
是错的，但是可以这样：

```
class B extends A{}
class C extends B{}
```
3. 子类继承父类时，调用方法时优先选择子类中被重写的方法，若没有，就会调用父类中的方法  
继承时，子类可以创建父类中没有的方法，也可以使用；  
但使用过程中需要注意，在多态里子类创建了自己的方法后，通过向上转型进行动态绑定创建对象后，对象调用子类自己创建的方法会报错  
Animal dog = new Dog();这句表现的是JAVA的多态，表示由一个父类的引用指向子类，因为是引用的是动物类型，而动物类没有getC()方法，所以编译器会认为，这个方法是不存在的。如果要通过编译必须这样写：Dog dog = new Dog();这就没有体现java中的多态，没有父类引用指向子类对象，只是继承。  
好比是：我说要一个动物，你给我一只小狗，这是可以的，但是狗会啃骨头，并不等于其他动物都会啃骨头。所以你给我一个动物，然后告诉我它要啃骨头，然而这只动物未必是小狗，所以我告诉你编译错误了。  
4. 在一个子类继承的时候，实际上会继承父类之中的所有操作（属性、方法），但是需要注意的是，对于所有的非私有（no private）操作属于显式继承（可以直接利用对象操作），而所有的私有操作属于隐式继承（间接完成）。通过利用对象操作调用父类private属性如下所示：
```
class A {
    private String str;
    public void setStr(String str) {
        this.str = str;
    }
    public String getStr() {
        return this.str;
    }
}

class B extends A {
    public void print() {
        //System.out.println(str); // 错误: str定义为private，不可见
    }
}

public class TestDemo {
    public static void main(String args[]) {
        B b = new B();
        b.setStr("hello");
        System.out.println(b.getStr());
    }
}
```
### 作用
实现了代码的复用，减少代码冗余
```
class Animal{
    private String name;
    public void setName(String name){
        this.name = name;
    }
    public String getName(String name){
        return this.name;
    }
}

class Dog{
    private String name;
    private int age;
    public void setName(String name){
        this.name = name;
    }
    public String getName(String name){
        return this.name;
    }
    public void setAge(int age){
        this.name = name;
    }
    public int getAge(int age){
        return this.age;
    }
}
```
若没有继承，这种代码的重复是不可避免的。
