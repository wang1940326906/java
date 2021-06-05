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
- 





