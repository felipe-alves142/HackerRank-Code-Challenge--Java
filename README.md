# HackerRank-Code-Challenge--Java

Na minha opinião, aprender fazendo é sempre mais efetivo, não que eu descarte cursos ou livros, mas ir aprendendo enquanto desenvolvo transforma todo aquele conhecimento abstrato em algo mais visível e concreto. Uma maneira ainda melhor de aprender é explicando e este repositório tem esse objetivo de aprender a mostrar  aquilo que aprendi ,minhas anotações, jeito de pensar,etc.     



## Java Loops II

Esse desafio está tentando testar meu entendimento sobre loops, input de dados e manipulação aritméticas desses dados. 
É usado o for loop para coletar todos os dados de entrada , com base em um valor de linha denominado q, e está tirando somando o valor dinâmico A com a potenciação e  retornando uma saída formatada.

Nessa solução é usado múltiplos loops, o primeiro usa o valor de q para pegar ir passando em cada linha e pegando os valores, enquanto o faz as operações,  e referenciamento de dados para o referenciado nunca ser mudado. A potenciação é multiplicada pelo valor b digitado pelo usuário.

### 1- Solução
Use a classe `Scanner` para coletar os dados de entrada e o método `nextInt()` para pegar o próximo valor inteiro que é a quantidade de linhas.
```
 public class Solution{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        
        int t = sc.nextInt();
```

Em seguida, declaramos todos os valores que precisamos coletar dentro do loop.
O valor de *c* é igual a *a*,pois *c* será mudado, mas não o valor de *a*. *c* é uma referência de *a*.
   ```
   for(int i=0;i<t;i++){
            int a = sc.nextInt();
            int b = sc.nextInt();
            int n = sc.nextInt();
            int c = a;
  ```
O loop secundário terá duas operações: a potenciação de *c* usando `Math.pow(2,j)`, nessa operação o valor de *c* vai ser somado com a potenciação de *j* vezes o valor de *b*, e a saída formada de *c* usando o `printf com %s` demonstrando a saída formatada será uma string com um espaço entre cada resultado.. 
 ```
            for(int j=0;j<n;j++){
              c+= Math.pow(2,j)*b;
              System.out.printf("%s ",c);
            }
            System.out.println();
        }
            
        sc.close();
        }
}
```
### 2 - Solução 

A segunda solução basicamente começa do mesmo jeito que a primeira.
`Scanner` para pegar dados, `nextInt()` para saber o número de linhas e a declaração de variáveis. Apesar de preferir a declaração das variáveis na mesma linha, assim como na solução dois, é uma prática mais comum declarar em linhas separadas. 

```
import java.io.*;
import java.util.*;
 
public class Solution{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        
        int t = sc.nextInt();
        int a,b,n;

```

O loop principal e suas operações continuam igual a da solução um, com a única diferença sendo que em vez de ter um loop secundário todos os valores são mandados diretos para outra classe onde serão manipuladas.
```
  for(int i=0;i<t;i++){
            a = sc.nextInt();
            b = sc.nextInt();
            n = sc.nextInt();
        
            loop(a,b,n);
        }
 ```
Na classe loop o valor de sum é uma referência de *a*, o loop está pegando o valor de *sum* somando com *b* vezes a potenciação. 
 ```
 static void loop(int a,int b,int n){
        int sum =a;
        for(int x=0;x<n;x++){
            sum+= b *(1<<x);
            System.out.print(sum + " ");
        }
        System.out.println();
    }
```

`(1<<x)` é uma solução que usa de algo chamado de `Bitwise left shift` operator que move o valor binário de x uma casa para esquerda. é um pouco vago, mas é o que eu entendi.  

No final da solução usa um `System.out.println()` vazio para que se o resultado ocupar mais de uma linha, então terá um espaço para separar as linhas.


## Java Datatypes

Esse desafio tem como propósito testar meus conhecimentos em tipos de dados , como manipulá-los e usá-los corretamente.  Utiliza de tipos de dados , fórmulas, exception tratativa e usa da potenciação para calcular todos os números possíveis para cada tipo inteiro.

Quando temos um temos um valor para ser a referência utilizamos aquelas operações básicas, `Scanner` para pegar os dados e `nextInt` para pegar a nossa referência.
```
import java.io.*;
import java.util.*;
 
public class Solution {
 
    public static void main(String[] args) {
        /* Enter your code here. Read input from STDIN. Print output to STDOUT. Your class should be named Solution. */
        Scanner sc = new Scanner(System.in);
        
        int t = sc.nextInt();
```

Dentro do `for` abre um `error handling`, use o `nextLong` para pegar o valor de qualquer tipo, print a primeira string e vá alterando o tipo de acordo com `Mathpow();`

```
for(int i =0;i<t;i++){    
            try{
                long n = sc.nextLong();
                System.out.println(n+ " can be fitted in:");
                if(n >= -128 && n<=127)
                    System.out.println("* byte");
                
                if(n >= -Math.pow(2,15) && n <= Math.pow(2,15)-1)
                    System.out.println("* short");
                    
                if(n>= -Math.pow(2,31) && n <= Math.pow(2,31)-1)
                    System.out.println("* int");
                
                if(n >= -Math.pow(2,63) && n <= Math.pow(2,63)-1)
                    System.out.println("* long");
                
            }catch(Exception e){
                System.out.println(sc.next()+" can't be fitted anywhere.");
            }
        }
        sc.close();
    }
}
 

            }
        }
        sc.close();
    }
}
```

### 2-Solução

Ambas as soluções começam iguais com `Scanner` e `nextint` para a referência no loop.Dentro `try` o mesmo long.

```
import java.util.*;
import java.io.*;



class Solution{
    public static void main(String []argh)
    {



        Scanner sc = new Scanner(System.in);
        int t=sc.nextInt();
```

A principal diferença é que em vez de utilizar o Mathpow para potenciação utiliza a comparação do menor e maior valor daquele número.

```
        for(int i=0;i<t;i++)
        {

            try
            {
                //BigInteger x=sc.nextBigInteger();
                long x=sc.nextLong();
                System.out.println(x+" can be fitted in:");
                if(x>=-128 && x<=127)System.out.println("* byte");
                if(x>=-32768 && x<=32767)System.out.println("* short");
                if(x>=-2147483648 && x<=2147483647)System.out.println("* int");
                if(x>=(-(Math.pow(2,63))) && x<=(Math.pow(2,63)-1))System.out.println("* long");
            }
            catch(Exception e)
            {
                System.out.println(sc.next()+" can't be fitted anywhere.");
            }

        }
    }
}
```

## Java static Initializer


Este desafio está testando minha paciência… digo inicialização estática sendo algo que não conheço e preciso me aprofundar.

Static initializer é, segundo meu entendimento, uma maneira de iniciar blocos de código com resultados estáticos, Apesar de ser parecido com a inicialização estática de variáveis, métodos ou classes, tem como principal diferença a possibilidade de acrescentar lógica ou manuseio de erros(try e catch). 
O bloco estático é iniciado com a palavra reservada static e seguido por {} e N O aceita variáveis externas não estática.

Também existe o final initializer que tem uma sintaxe parecida com o static, mas sem o utilizar a palavra reservada final.Por Exemplo:
```
//Declaração do final initializer

{
	//Lógica
}
```
## Resolvendo o exercício

Link do problema: https://www.hackerrank.com/challenges/java-static-initializer-block/problem?isFullScreen=true

O `Static` só aceita valores externos que sejam estáticos, então todos os valores devem ter uma inicialização estática. 
```
import java.io.*;
import java.util.*;
 
public class Solution {
 
      /* Enter your code here. Read input from STDIN. Print output to STDOUT. Your class should be named Solution. */
        static Scanner sc = new Scanner(System.in);
        
        static int b = sc.nextInt();
        static int h = sc.nextInt();
        static Boolean flag = false; 
```

Esse desafio só tem que checar se os valores recebidos estão de acordo, se não estiver o `throw new exception` lançará um erro ou se tudo estiver de acordo o *flag* virá true. O *flag* é nossa referência de saida.
```
import java.io.*;
import java.util.*;
 
public class Solution {
 
      /* Enter your code here. Read input from STDIN. Print output to STDOUT. Your class should be named Solution. */
        static Scanner sc = new Scanner(System.in);
        
        static int b = sc.nextInt();
        static int h = sc.nextInt();
        static Boolean flag = false; 
        static{
            try{
                if(b<=0||h<=0){
                    throw new Exception("Breadth and height must be positive");
                }else{    
                  flag =true;
                }
            }catch(Exception e){
              
                System.out.println(e);
        }
}
public static void main(String[] args) {
    if(flag){
        System.out.println(h*b);   
        }
    }      
}
 
```

## Java Date and Time 



### Solução 1

Use a classe `Scanner` para pegar o valor do mês,dia, ano.
```
Scanner sc = new Scanner(System.in);
            int month = sc.nextInt();
            int day = sc.nextInt();
            int year = sc.nextInt();
```

O desafio pedia para usar a classe `calendar`, mas pensando em utilizar práticas mais modernas resolvi usar o `LocalDate`. O LocalDate possui um método chamado `of()` e nele podemos setar o mês, ano e dia que quisermos.
```
 sc.close();
            LocalDate dt = LocalDate.of(year,month,day);
                
            System.out.println(dt.getDayOfWeek());
```

Uma mudança que posso fazer é simplificar o resultado em uma só linha . 
`LocalDate.of(year,month,day).getDatOfWeek().name();`

### Solução 2

A solução mais votada foi essa, é muito parecida com 1, sua principal diferença sendo que usa o `in`. 

```
import java.time.LocalDate;

//String month = in.next();
int mm = in.nextInt();
//String day = in.next();
int dd = in.nextInt();
//String year = in.next();
int yy = in.nextInt();
in.close();
LocalDate dt = LocalDate.of(yy, mm, dd);
System.out.print(dt.getDayOfWeek());
```
