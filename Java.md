# Java Study

### 1. Path Environment Configuration

### 2. Comments for code

- one line comment
  + type // to leave a comment

- mutiple line comments
  + type /* comment*/ to leave a comment

- file comment
  + --

### 3. Type - transfer

- byte --> short --> int --> long --> float --> double
- ----------> char -->

### 4. Operand "+"

​		`int i = 10;`

​		`char c = 'A';`

​		`System.out.println (i + C);`

This can be complied and no mistake with the code, char c here has a int value using ASCLL. The out put is 75.

### 5.Operand "+" work with String

`System.out.println("HelloWorld" + 666)`

`System.out.println(666 + "HelloWorld")`

`System.out.println(6 + 66 + "HelloWorld")`

- This prints 72HelloWorld

`System.out.println("HelloWorld" + 66 + 6)`

- But this one prints "HelloWorld666"

### 6. Special Operand

We have a case like `a > b ? c : d`, this represents a special scenario. If `a > b` turns to be `true`5, we got `c` as a result, if `a > b` turns to be `false`, we have d as a result.

### 7. Data collect

How to use Scanner:

- Import
  + `import java.util.Scanner;`
- Create a object
  + `Scanner sc = new Scanner(System.in);`
  + `sc` is just a name and it can be changed, the rest of part cannot be changed.

- Receive the data from the object
  + `int i = sc.nextInt();`

### 8. Order Structure - if

- Configuration:

  if (content - 1){

  ​	content - 2;

  }

1. We first calculate the value of the content - 1.
2. if the result of 1 is `true` , we carry on to the content - 2.
3. if the result of 1 turns to be `false` , we don't do content - 2, instead, we continue to the next content.

```java
public class IfDemo{
	public static void main(String[] args){
		System.out.println("Start");
		
		//Define two variables
		int a = 10;
		int b = 20;
		
		//Need: if a is equal to b, we print out "a is equal to b", else we continue.
		if (a == b){
			System.out.println("a is equal to b");
		}
		System.out.println("a is not equal to b");
	}
}
```

### 9. If else Structure

- Configuration:

  + if (Content - 1){

    ​	Content - 2;

    } else {

    ​	Content - 3;

    }

### 10. Example TIME

Need: Give a random integer, create a program to identity whether it is a odd or even number, and print the result.

- Steps:
  - Using Scanner to catch the input

```java
import java.util.Scanner;

public class App{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        int number = sc.nextInt();
        
        if ( 95 <= number){
            System.out.println("Bike");
        }else if( 90 <= number &&  number <= 95){
            System.out.println("Ticket");
        }else if( 80 <= number &&  number <= 89){
            System.out.println("Robot");
        }else if(number <= 60){
            System.out.println("Da");
        }
    }
}
	
```



### 11. if Example

Need: the score decided what present I'm gonna give to my kid, write a program take the score as a input and return the present I should give to my kid.

``` Java
import java.util.Scanner;

public class ifexample{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        int number = sc.nextInt();
        
        if ( 95 <= number){
            System.out.println("Bike");
        }else if( 90 <= number <= 95){
            System.out.println("Ticket");
        }else if( 80 <= number <= 89){
            System.out.println("Robot");
        }else if( 80 <= number <= 89){
            System.out.println("Da");
        }
    }
}
```

### 12. Switch Structure

Configuration:

``` java
switch (表达式){
    case 值 1:
        语句体1;
        break;
    case 值 2:
        语句体2;
        break;
    ...
    default:
        语句体n+1;
        [break;]
} 
```



### 13. Switch Example

Need: There are 12 months within a year, 4 seasons of course, we want to have a print out of what season if we have a valid input between 1- 12.

``` Java
import java.util.Scanner;

public class switchDemo{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        int month = sc.nextInt();
        
        switch(month){
            case 1:
                System.out.println("Winter");
         		break;
            case 2:
                System.out.println("Winter");
         		break;
            ...
            default:
                System.out.println("Wrong input");
                break;
        }
    }
}
```

**Case 穿透**

``` Java
import java.util.Scanner;

public class App{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        int month = sc.nextInt();
        
        switch(month){
            case 1:
            case 2:
            case 12:
                System.out.println("Winter");
            	break;
            case 3:
            case 4:
            case 5:
                System.out.println("Spring");
            	break;
            case 6:
            case 7:
            case 8:
                System.out.println("Summer");
                break;
            case 9:
            case 10:
            case 11:
                System.out.println("Fall");
                break;
            default:
                System.out.println("Wrong input");
                break;
        }
        sc.close();
    }
}
```

### 14. for 语句

Configuration:

``` Java
for (初始化语句; 条件判断语句; 条件控制语句){
    循环体语句;
}
```



 Example 1:

``` Java
输出5 -- 1
public class App{
    public static void main(String[] args){
    for(int i = 5; i >= 1; i--){
        System.out.println(i);
        }
    }
}
输出1 -- 5
public class App{
    public static void main(String[] args){
    for(int i = 1; i <= 5; i++){
        System.out.println(i);
        }
    }
}
```



Example 2:

Need: Sum of even number from 1 to 100;

``` Java
public class App{
    public static void main(String[] args){
    int sum = 0;
    for(int i = 1; i <= 100; i++){
        if (i % 2 == 0){
            sum += i;
            }
        }
    System.out.println(sum);
    }
}
```



### 15.水仙花

``` Java
public class App{
    public static void main(String[] args){
   
        for (int i = 100; i <= 999; i ++){
            //个位
            int a = i % 10;
            //十位
            int b = (i / 10) % 10;
            //百位
            int c = i / 100;
            if (a*a*a + b*b*b + c*c*c == i){
                System.out.println(i);
            }
        }
    }
}
```

### 16. While Structure

Configuration:

``` java
while(条件判断语句){
    循环体语句;
}
```

Print "HelloWorld" five times:

``` Java
public class App{
    public static void main(String[] args) {
        int a = 0;
        while(a < 5){
            a++;
            System.out.println("HelloWorld");
        }
    }
}
```

Example:

珠穆朗玛峰：

### 17. Difference between 3 kinds of Statements

``` java
for(int i = 3; i<3; i++){
    System.out.println("I love Java");
}

int j = 3;
while(j<3){
    System.out.println("I love Java");
}

int k =3;
do{
    System.out.println("I love Java");
    k++;
}while(k<3)
```

For the do while statement, we can say that only the do while statement first do the `System.out.println("I love Java")`.

```java
for(int i = 3; i<3; i++){
    System.out.println("I love Java");
}
\\System.out.println(i);

int j = 3;
while(j<3){
    System.out.println("I love Java");
}
\\System.out.println(j);
```

We cannot print out the value of the i, because i is only the partial variable, it is not a global variable as we define j, we do have a concrete value for j, as it changed through  the while statement.

**DEAD CIRCLE**

``` java
for(;;){
    System.out.println("I love Java");
}
```

This gonna keep printing "I love Java" forever.

``` java
while(true){
    System.out.println("I love Java");
}
```

### 18.for loop 嵌套

``` java
public class radioExample{
    public static void main (String[] args) {
        for(int a=0; a<24; a++){
            for(int b = 0; b<60;b++){
                System.out.println(a + " " +"hour" + b + " " + "minute");
            }
        }
    }
}
```

### 19.猜数字

``` java
import java.util.Random;
import java.util.Scanner;

public class radioExample{
    public static void main (String[] args) {
        //导入猜想
        System.out.println("Let's guess a number");
        Scanner sc = new Scanner(System.in);
        String guessD = sc.nextLine();
        int guess = Integer.valueOf(guessD);
        
        //生成数字
        Random a = new Random();
        int ap = a.nextInt(100);

        while(guess != ap){
            if(guess > ap){
                System.out.println("Too big");
                System.out.println("Try again");
                guessD = sc.nextLine();
                guess = Integer.valueOf(guessD);
            }else if(guess < ap){
                System.out.println("Too small");
                System.out.println("Try again");
                guessD = sc.nextLine();
                guess = Integer.valueOf(guessD);
            }else{
                ;
            }
        }
        System.out.println("You got it");
        sc.close();
    }
}
```

