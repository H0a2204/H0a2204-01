# 第八单元  Java基础知识-一维数组

## 一、昨日知识点回顾

## 二、本单元知识点概述

### 知识点概述

![](img/01.png)

****

## 三、本单元教学目标

### （I）重点知识目标

```
1.什么是数组
2.数组的格式
3.数组的注意事项
4.数组的几种常见使用
```

### （II）能力目标

```
1.掌握数组的定义格式
2.掌握数组的使用方法
3.掌握数组的遍历方式
4.熟悉数组的常见异常
```

*****

## 四、本单元知识详解

### 8.1 数组的定义和访问

#### 8.1.1 容器的概念

【引入案例】现在需要统计某公司员工的工资情况。假设该公司有50名员工，用前面所学的知识，程序首先需要声明50个变量来分别记住每位员工的工资，然后进行操作。

```java
public class ArraysTest {
    public static void main(String[] args) {
        int salary1=8000;
        int salary2=7800;
        int salary3=5999;
        ......
        int salary50=9856;
    }
}
```

这样做会显得很麻烦，而且错误率也会很高。因此我们可以使用容器进行操作。将所有的数据全部存储到一个容器中，统一操作。 

**容器**：是将多个数据存储到一起，每个数据称为该容器的元素。

生活中的容器：水杯，衣柜，教室

#### 8.1.2 数组的概念

数组：相同类型数据的集合，它在内存空间的存储是连续的。数组其实也是一个容器,用来存储固定个数相同类型的数据，数组中存储的数据叫做元素。

#### 8.1.3 数组定义的格式

方式一

格式： 

```java
数组存储的数据类型[] 数组名字 = new 数组存储的数据类型[长度];
数组存储的数据类型 数组名字[] = new 数组存储的数据类型[长度];
```

数组定义格式详解： 

- 数组存储的数据类型： 创建的数组容器可以存储什么数据类型。
- [] : 表示数组。
- 数组名字：为定义的数组起个名称，满足标识符规范，可以使用名字操作数组。 
- new：关键字，创建数组使用的关键字。
- 数组存储的数据类型： 创建的数组容器可以存储什么数据类型。
- [长度]：数组的长度，表示数组容器中可以存储多少个元素。 
  注意：数组有定长特性，长度一旦指定，不可更改。	  

例如：定义可以存储3个整数的数组容器，代码如下：

```java
int[] arr = new int[3];
int arr[] = new int[3];
```

方式二

格式： 

```java
数据类型[] 数组名 = new 数据类型[]{元素1,元素2,元素3...};
```

数组定义格式详解： 

- 在定义数组的时候，直接将数组元素的值传入
- 采用这种方式定义数组，那么一定不要定义长度，数组的长度是由具体元素的个数决定

例如：定义存储1，2，3，4，5整数的数组容器，代码如下：

```java
int[] arr = new int[]{1,2,3,4,5};
```

方式三

格式： 

```java
数据类型[] 数组名 = {元素1,元素2,元素3...};
```

数组定义格式详解： 

- 这种方式第一数组，直接传入要操作数组元素的值
- 这种定义数组的方式使用的比较少

例如：定义存储1，2，3，4，5整数的数组容器 ，代码如下：

```java
int[] arr = {1,2,3,4,5};
```

#### 8.1.4 数组的索引

由于数组是存储相同数组类型的集合，并且在内存中连续存储，所以我们就会给数组元素进行编号，那么这个编号就是数组的索引。

索引： 每一个存储到数组的元素，都会自动的拥有一个编号，从0开始，这个自动编号称为数组索引 (index)，可以通过数组的索引访问到数组中的元素。

#### 8.1.5 访问数组的格式

格式： 

```java
数组名[索引]
```

我们通过数组的索引访问数组的元素。

例如：访问名称为arr，长度为9的int类型数组的第3个元素，代码如下

```java
arr[2]
```

#### 8.1.6 数组的长度属性

每个数组都具有长度，并且在定义数组之后就是固定的，Java中赋予了数组的一个属性，可以获取到数组的长度。

格式： 

```
数组名.length
```

属性length的执行结果是数组的长度，int类型结果。由次可以推断出，数组的最大索引值为 **数组名.length-1** 。 

【案例】：定义一个数组，获得数组的长度

```java
public class Demo1 {
    public static void main(String[] args) {
        int[] arr1 = new int[]{1,2,3,4,5};
        //输出结果是5
        System.out.println("arr1的长度是："+arr1.length);
        int[] arr2=new int[9];
        //输出结果是9
        System.out.println("arr2的长度是："+arr2.length);
    }
}
```

运行结果如图所示：

![](img/02.png)

#### 8.1.7 索引访问数组中的元素

在数组中可以通过索引赋值，也可以通过索引得到数组元素的值。

为数组元素赋值格式：

```java
数组名[索引] = 值；
```

获得数组元素

```
变量 = 数组名[索引];
```

【案例】：为数组元素赋值和获得值。存储5名学生的成绩，将第3名的学生成绩输出。

方式1：静态初始化

```java
public class Demo2 {
    public static void main(String[] args) {
        //定义长度为5的int类型数组存入学生成绩
        int[] score = new int[5];
        //通过索引赋值
        score[0]=98;
        score[1]=77;
        score[2]=88;
        score[3]=76;
        score[4]=100;
        //通过索引访问数组元素
        System.out.println("第三名学生的成绩是："+score[2]);
    }
}
```

运行结果如图所示：

![](img/03.png)

方式2：通过键盘录入赋值（动态初始化）

```java
import java.util.Scanner;
public class Demo3 {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        //定义长度为5的int类型数组存入学生成绩
        int[] score = new int[5];
        //通过循环赋值
        for (int i = 0; i < score.length; i++) {
			 System.out.println("请输入第"+(i+1)+"名学生成绩：");
            score[i]=input.nextInt();
        }
        //通过索引访问数组元素
        System.out.println("第三名学生的成绩是："+score[2]);
    }
}

```

运行结果如图所示：

![](img/04.png)

**数组创建之后，内存会分配默认值：**

**byte 、short、 int 、long**类型的默认值是：0

**float、 double**类型的默认值是0.0

**String**类型的默认值是：null

**char**类型的默认值是：'\u0000'  即 0

**boolean**类型的默认值是：false

**小结：**

```markdown
1. 定义数组的常用方式：数据类型[] 数组名=new 数据类型[长度]。
2. 数组的长度为：数组名.length。
3. 数组是通过索引名称赋值，也是通过索引访问。
```

### 8.2 数组原理内存图

#### 8.2.1 内存的概述

内存是计算机中的重要原件，临时存储区域，作用是运行程序。我们编写的程序是存放在硬盘中的，在硬盘中的程 

序是不会运行的，必须放进内存中才能运行，运行完毕后会清空内存。 

Java虚拟机要运行程序，必须要对内存进行空间的分配和管理。 

#### 8.2.2 JVM的内存划分

为了提高运算效率，就对空间进行了不同区域的划分，每片区域都有特定的处理数据方式和内存管理方式。 

JVM的内存划分：

![](img\05.png)

#### 8.2.3 一个数组内存图

我们是通过数组的索引访问数组，那么如果我们直接打印数字名，会不会把所有的数组元素全部显示呢？

【案例】：使用代码实现直接打印数字名称

```java
public class Demo4 {
    public static void main(String[] args) {
        int[] arr = new int[3]{1,2,3};
        System.out.println(arr);
    }
}
```

运行结果如图所示：

![](img\06.png)

我们发现并没有打印出所有的数组元素，而是打印出了   [I@15db9742   ，那么这是什么呢？

是数组在内存中的地址。new出来的内容，都是在堆内存中存储的，而数组arr保存的是数组的地址。 

可以通过下图解析：

![](img\07.png)

#### 8.2.4 两个数组内存图

那么同样的，如果是两个数组，就会在内存空间的堆内存中开辟两个地址。

【案例】：打印两个数组的地址

```java
public class Demo5 {
	public static void main(String[] args) { 
		int[] arr = new int[3]; 
		int[] arr2 = new int[2]; 
		System.out.println(arr); 
		System.out.println(arr2); 
	}
}
```

运行结果如图所示：

![](img\08.png)

可以通过下图解析：

![](img\09.png)

#### 8.2.5 两个数组指向一个地址

【案例】：使用代码实现两个数组指向相同地址

```java
public class Demo6 {
    public static void main(String[] args) {
        // 定义数组，存储3个元素
        int[] arr = new int[3];
        //数组索引进行赋值
        arr[0] = 5;
        arr[1] = 6;
        arr[2] = 7;
        //输出3个索引上的元素值
        System.out.println(arr[0]);
        System.out.println(arr[1]);
        System.out.println(arr[2]);
        //定义数组变量arr2，将arr的地址赋值给arr2
        int[] arr2 = arr;
        arr2[1] = 9;
        System.out.println(arr[1]);
    }
}
```

运行结果如图所示：

![](img\10.png)

可以通过下图解析：

![](img\11.png)

通过代码我们可知，数组arr赋值给arr2，即将arr的值和地址全部给arr2，所以arr2和arr指向同一个地址，那么将arr2中数组元素的值改变就是改变arr的数组元素。

**小结：**

```markdown
1. 数组是引用数据类型。
2. 引用数据类型的值存在堆空间中，由地址指向值。
```

### 8.3 数组的常见操作

#### 8.3.1 数组越界异常

【案例】：代码实现数组下标越界

```java
public class Demo7 {
    public static void main(String[] args) {
        int arr[] = new int[]{1,2,3};
        System.out.println(arr[3]);
    }
}
```

运行结果如图所示：

![](img\12.png)

创建数组，赋值3个元素，数组的索引就是0，1，2，没有3索引，因此我们不能访问数组中不存在的索引，程序运 行后，将会抛出 ArrayIndexOutOfBoundsException 数组越界异常。在开发中，数组的越界异常是不能出现的，一 旦出现了，就必须要修改我们编写的代码。 

#### 8.3.2 数组空指针异常

【案例】：使用代码实现数组的空指针异常

```java
public class Demo8 {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3};
        arr = null;
        System.out.println(arr[0]);
    }
}
```

运行结果如图所示：

![](img\13.png)

arr = null 这行代码，意味着变量arr将不会在保存数组的内存地址，也就不允许再操作数组了，因此运行的时候 

会抛出 NullPointerException 空指针异常。在开发中，数组的越界异常是不能出现的，一旦出现了，就必须要修 

改我们编写的代码。 

可以通过下图解析：

![](img\14.png)

#### 8.3.3 数组的遍历

【案例】：将数组中的元素显示

```java
public class Demo9 {
    public static void main(String[] args) {
        int[] arr=new int[]{77,88,66,55,99};
        //将数组元素显示
        System.out.println(arr[0]);
        System.out.println(arr[1]);
        System.out.println(arr[2]);
        System.out.println(arr[3]);
        System.out.println(arr[4]);
    }
}
```

通过访问索引，可以将数组中的元素值显示，但是如果数组中存储的数据太多怎么办，一个一个的输出很明显很麻烦，会大大降低代码的执行效率，所有我们可以采用for循环的方式将数组中的元素显示出来。

```java
public class Demo9 {
    public static void main(String[] args) {
        int[] arr=new int[]{77,88,66,55,99};
        //将数组元素显示
        System.out.println("数组元素的值是：");
        for (int i=0;i< arr.length;i++){
            System.out.println(arr[i]);
        }
    }
}
```

运行结果如图所示：

![](img\15.png)

#### 8.3.4 数组获取最大元素值元素

【案例】：找出数组的最大值

方法一：

实现思路： 

- 定义变量，保存数组0索引上的元素 
- 遍历数组，获取出数组中的每个元素 
- 将遍历到的元素和保存数组0索引上值的变量进行比较 
- 如果数组元素的值大于了变量的值，变量记录住新的值
- 数组循环遍历结束，变量保存的就是数组中的最大值 

![](img\16.png)

```java
public class Demo10 {
    public static void main(String[] args) {
        int[] arr = { 5, 15, 2000, 10000, 100, 4000 };
        //定义变量，保存数组中0索引的元素
        int max = arr[0];
        //遍历数组，取出每个元素
        for (int i = 0; i < arr.length; i++) {
            //遍历到的元素和变量max比较
            //如果数组元素大于max
            if (arr[i] > max) {
                //max记录住大值
                max = arr[i];
            }
        }
        System.out.println("数组最大值是： " + max);
    }
}
```

运行结果如图所示：

![](img\17.png)

方法二：

实现思路： 

- 导包：java.util.Arrays; 
- 调用Arrays中的sort()方法，对数组进行升序排序
- 数组中的最后一个元素即为最大值

```java
import java.util.Arrays;//导包
public class Demo11 {
    public static void main(String[] args) {
        int[] arr = { 5, 15, 2000, 10000, 100, 4000 };
        Arrays.sort(arr);//调用Arrays中的方法升序排序
        //最后一个元素就是最大值，索引为：arr.length-1
        System.out.println("数组的最大元素为："+arr[arr.length-1]);
    }
}
```

运行结果如图所示：

![](img\18.png)

#### 8.3.5 数组的反转

数组的反转： 数组中的元素颠倒顺序，例如原始数组为1,2,3,4,5，反转后的数组为5,4,3,2,1 

分析：数组最远端的元素互换位置。 

- 实现反转，就需要将数组最远端元素位置交换 

- 定义两个变量，保存数组的最小索引和最大索引 

- 两个索引上的元素交换位置 

- 最小索引++，最大索引--，再次交换位置 

- 最小索引超过了最大索引，数组反转操作结束 

  ![](img\19.png)

【案例】：实现数组元素的反转

```java
public class Demo12 {
    public static void main(String[] args) {
        int[] arr = { 1, 2, 3, 4, 5 };
		/*循环中定义变量min=0最小索引
		max=arr.length‐1最大索引
		min++,max‐‐
		*/
        for (int min = 0, max = arr.length-1; min <= max; min++,max--) {
            //利用第三方变量完成数组中的元素交换
            int temp = arr[min];
            arr[min] = arr[max];
            arr[max] = temp;
        }
        // 反转后，遍历数组
        for (int i = 0; i < arr.length; i++) {
            System.out.println(arr[i]);
        }
    }
}
```

运行结果如图所示：

![](img\20.png)

#### 8.3.6 冒泡排序，二分法查找

冒泡排序原理：比较两个相邻的元素，将值大的元素交换至右端。

思路：

依次比较相邻的两个数，将小数放在前面，大数放在后面。即在第一趟：首先比较第1个和第2个数，将小数放前，大数放后。然后比较第2个数和第3个数，将小数放前，大数放后，如此继续，直至比较最后两个数，将小数放前，大数放后。重复第一趟步骤，直至全部排序完成。

第一趟比较完成后，最后一个数一定是数组中最大的一个数，所以第二趟比较的时候最后一个数不参与比较；

第二趟比较完成后，倒数第二个数也一定是数组中第二大的数，所以第三趟比较的时候最后两个数不参与比较；

依次类推，每一趟比较次数-1；

![](img/冒泡排序.gif)

【案例】：代码实现冒泡排序

```java
public class Demo13 {
    public static void main(String[] args) {
        int[] arr = {6, 3, 8, 2, 9, 1};
        System.out.println("排序前数组为：");
        for (int num : arr) {
            System.out.print(num + " ");
        }
        for (int i = 0; i < arr.length - 1; i++) {//外层循环控制排序趟数
            for (int j = 0; j < arr.length - 1 - i; j++) {//内层循环控制每一趟排序多少次
                if (arr[j] > arr[j + 1]) {
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }
        System.out.println();
        System.out.println("排序后的数组为：");
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }
}
```

运行结果如图所示：

![](img\21.png)

**【了解】**

二分法查找原理：二分法查找又称折半查找，二分法查找的基本思想是把数组中的元素从小到大有序地放进数组中，首先将给定值与数组中间位置的值作比较，如果相等，则匹配成功。否则，若比较的值小了，则在数组的前半部分继续二分法查找；若比较值大了，则在数组的后半部分进行二分法查找。如此往复，直到比较值与中间值匹配，完成查找。

```java
import java.util.Arrays;

public class Demo14 {
    public static void main(String[] args) {
        int[] arr = {30, 20, 50, 10, 80, 9, 7, 12, 100, 40, 8};
        int searchWord = 20; // 所要查找的数
        Arrays.sort(arr); //二分法查找之前，一定要对数组元素排序
        System.out.println(Arrays.toString(arr));
        System.out.println(searchWord + "元素的索引：" + binarySearch(arr, searchWord));
        System.out.println("========================");
        int errorWord = 66; // 查找不存在的数
        System.out.println(errorWord + "元素的索引：" + binarySearch(arr, errorWord));

    }

    /**
     * 二分查找方法
     * @param arr 数组
     * @param value 要查找的值
     * @return 返回-1，说明没有找到，否则找到
     */
    public static int binarySearch(int[] arr, int value) {
        int low = 0; // 开始位置
        int high = arr.length - 1; // 结束 位置
        while (low <= high) {
            int middle = (low + high) / 2;
            if (value == arr[middle]) {
                return middle; //返回查询到的索引位置
            }
            if (value > arr[middle]) {
                low = middle + 1;
            }
            if (value < arr[middle]) {
                high = middle - 1;
            }
        }
        //上面循环完毕，说明未找到，返回-1
        return -1;
    }
}

```

运行结果如图所示：

![](img\22.png)

**小结：**

```markdown
1. 在操作数组的时候要避免出现数组下标越界异常和空指针异常。
2. 使用for循环遍历数组。
3. 求数组的最大值的前提是参与比较的值必须是数组中的元素。
4. 冒泡排序的规则：外层循环n-1，内层循环n-1-i
```

### 8.4 数组作为方法的参数和返回值

#### 8.4.1 数组作为方法的参数传递的是数组内存的地址

以前的方法中我们学习了方法的参数和返回值，但是使用的都是基本数据类型。那么作为引用类型的数组能否作为 

方法的参数进行传递呢，当然是可以的。 

数组作为方法参数传递，传递的参数是数组内存的地址。 

【案例】：代码实现求任意数组的和，平均值

```java
public class Demo15 {
    public static void main(String[] args) {
        int[] arr = { 1, 3, 5, 7, 9 };
        //调用方法，传递数组
        printArray(arr);
    }
    /**
     * 数组作为方法的参数
     * @param arr 要遍历的数组
     */
    public static void printArray(int[] arr) {
        /* 创建方法，方法接收数组类型的参数 进行数组的遍历 */
        for (int i = 0; i < arr.length; i++) {
            System.out.println(arr[i]);
        }
    }
}
```

运行结果如图所示：

![](img\25.png)

#### 8.4.2 数组作为方法的返回值，返回的是数组的内存地址

数组作为方法的返回值，返回的是数组的内存地址

【案例】：将1-30之间的偶数存入数组中，并打印

```java
public class Demo16 {
    public static void main(String[] args) {
        //调用方法，接收数组的返回值
        //接收到的是数组的内存地址
        int[] arr = getArray();
        for (int i = 0; i < arr.length; i++) {
            System.out.println(arr[i]);
        } }

    /**
     * 数组作为方法的返回值
     * @return 返回数组
     */
    public static int[] getArray() {
        /*创建方法，返回值是数组类型 return返回数组的地址 */
        int[] arr = { 1, 3, 5, 7, 9 };
        //返回数组的地址，返回到调用者
        return arr;
    }
}

```

运行结果如图所示：

![](img\26.png)

**小结：**

```markdown
1. 方法的参数为基本类型时，传递的是数据值。
2. 方法的参数为引用类型时，传递的是地址值。
```

****

## 五、本单元知识总结

```
1. 什么是数组
2. 数组的定义格式
3. 数组的使用
4. 数组的遍历
```

