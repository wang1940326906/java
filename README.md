# java
## java Learning notes
### 1. 常见DOS命令
- cd 目录路径 | 进入一个子目录
- cd.. | 进入父目录
- dir | 查看本目录下的文件和子目录列表
- cls | 清除屏幕
- 上下键 | 查找敲过的命令
- Tab | 自动补齐命令
### 2. 整形数据类型
- byte 1个字节（1个字节（byte）=8位二进制位（bit）） 表数范围 2的7次方
- short 2个字节  2的15次方（2*8）
- int 4个字节  2的31次方（4*8）
- long 8个字节   2的63次方（8*8）
### 3. 整形常量的四种表示形式
- 十进制整数 
- 八进制整数，要求以0开头，012
- 十六进制整数，要求0x或0X开头，0x12
- 二进制数，以0b或0B开头，0B11100
```

public class TestComment {

	public static void main(String []args) {
		 int age=010;//八进制
		 int a=0b1101;//二进制
		 int b=0x17;//十六进制
		 
		System.out.println(age);
		System.out.println(a);
		System.out.println(b);
	}
  }
```
java语言的整型常数默认为int类型，声明long型常量后面加'l'或'L'
```
long a=740000000//编译不通过，超过了int的表示范围
long a=740000000L//编译通过
long a=74000//编译通过，在int表示的范围内
```
### 4. 浮点型常量、变量
- float 4字节
- double 8字节
没有后缀F/f的浮点数值默认为double类型，可以在浮点数值后添加D/d，明确其为double类型
```
float a=3.14f;
double b=3.14;
double c=3.14d;
```
- 浮点数是不精确的，不能用于比较
如果要比较，可以用java.math包下面两个类，BigInteger和BigDecimal,BigInteger实现了任意精度的整数运算，BigDecimal实现了任意精度的浮点运算
```
import java.math.*;
public class TestComment {

	public static void main(String []args) {
  	BigDecimal a=BigDecimal.valueOf(1.0);
		a=a.subtract(BigDecimal.valueOf(0.1));
		a=a.subtract(BigDecimal.valueOf(0.1));
		a=a.subtract(BigDecimal.valueOf(0.1));
		System.out.println(a);
		
		BigDecimal a2=BigDecimal.valueOf(0.1);
		BigDecimal a3=BigDecimal.valueOf(1.0/10.0);
		System.out.println(a2.equals(a3));
		
	}
}//结果为0.7 true
```
### 5. char字符型常量/变量
- char 2个字节 用来表示在Uncode编码表中的字符
- Unicode具有从0到65535之间的编码，通常用从'\u0000'到'\uFFFF'之间的十六进制值来表示
#### 转义字符 
- \n换行符
- \t制表符
- \b空格
- \r回车
- \"双引号
- \'单引号
- \\反斜杠
```
System.out.println(""+'a'+'\n'+'b');
```
### 6.boolean 
- 占一位，不可使用0或非0的字符代替true或false
```
boolean man=true;
if(man){
System.out.println("man");
}
```
### 6. 二元运算符的运算规则
- 如果两个操作数，有一个为long，则结果为long
- 没有long时，结果为int，即使操作数全为short,byte,结果也是int
- 如果两个操作数有一个为double,则结果为double
- 只有两个数都是float，结果才为float
### 7. 逻辑运算符
- 短路与和短路或采用短路的方式，从左到右计算，如果只通过运算符左边的操作数就能确定该逻辑表达式的值，则不会计算运算符右边的操作数
- ~ 取反
- &按位与
- | 按位或
- ^ 按位异或
- <<左移运算符，左移一位相当于乘2
- >>右移运算符，右移一位相当于除以二取商
### 8. 内存分析
JVM的内存可分为三个区域：栈，堆，方法区
#### 栈：储存基本类型的变量和对象的引用变量（局部变量）
- main及其他方法都有其独立栈帧
- 对象的地址
#### 堆：存放由new创建的对象和数组
- 对象的属性
- 对象的地址（堆和栈通过对象的地址连接起来）
- 所有线程共享一个堆，不连续的存储空间
##### 方法区：储存在堆里，用来存放程序中永远是不变或唯一的内容（类相关的信息）
- 1.代码
- 2.静态变量
- 3.静态方法（static）
- 4.字符串常量
### 9.构造方法
- 1、方法有返回类型，方法名小写，不能和类名相同；构造方法没有返回类型，void也不行，名与类名相同。
- 2、构造方法是初始化对象的重要途径，所以就算你给一个类没有定义构造方法，方法在这个类的加载得时候，会自动提供一个没有参数的构造方法。所以，常见得 Student s=new Student();那么，s这个实例，是通过构造方法初始化的；而普通方法不行
- 3、他们运行顺序不同。一个类在初始化的时候，例如People是Student的父类，有构造方法 public PeoPle(){}那么，当实例化Student p=new Student()得时候，父类的构造方法会隐式执行（你可自己敲代码尝试，父类构造方法中写个输出语句：例如System.out.println("父类构造方法")）。你会发现，没有调用任何父类，也没有实例化父类，但是构造方法却执行了。
- 4、方法仅仅是类成员，构造方法也是类成员，但是，构造方法有对类属性得初始化的功能。所以，常见到 public PeoPle(String name){this.name=name}或者 public PeoPle(){name="wangsan",age=14},完成了对People类属性name或者age的初始化





