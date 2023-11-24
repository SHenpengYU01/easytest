# The Recursion Algrithm (in C language)

## **Introduction**

I recently started to study the recursion algorithm , a tough and highly abstract thing for me to take in. So I decided to write about my own study process and opinion about it ,so as to comprehend it more thoroughly and clearly and develop my basic working model and habits in VScode.

----

## Basic definition

Recursion is somekind like iretation , both of which use one thing for many times , in most cases function probably , especially the former. And this algrithm can often solve some problems in a very concise and condensed way . It can even ignore the specific details of its realization .

 There are some basic elements for the recursion : the base case or the turning point , the progress forward and backward , the outcome( return / printf ).

My understandings of it are mainly based on some specific examples . Here are some :

## Examples

### *non-void type*

```C
// gcd : 
int gcd (int x , int y)
{
    if(y==0)
    {
        return x;
    }
    gcd (y , x % y);
}
```

----

```C
// fibnacci:
int f ( int n )
{
    if(n==1||n==0)
    {
        return n;
    }
    return f (n-1) + f(n-2);
}
```

```C
// factorial
int fac (int n)
{
    if (n==1)
    {
        return 1;
    }
    return  n * fac (n-1);
}
```

```C
// combination number
double comnum(int n , int m)
{
    if( m == 0 )
    {
        return 1;
    }
    else
    {
        return n*comnum(n-1,n-1)/m;    
    }         //here we use an important formula   
}
// we can simplify the caculation by using another combination number formula
// just add 'if(m>n-m) m=n-m;' before the first 'if'
```

#### Analyses1

All the 3 cases are int or double functions which contain two parts : judgement and two ( or more ) return , one to recall the function , one to give value for the basic case , which puts an end to the process of recalling ( di ) and start the process of assignment ( gui ).

However, in order to avail the later modification process,we should change it into one return by adding one argument,like res or ret (abbr of result) ,wihch ensures the only exit of the funtion.

The key idea is that if we want to get the final outcome from the function , we have to recall it to get the outcome of the former case until we reach the base case , where the process of recalling ( di ) ends , and the process of computing ( gui ) with the basic value starts .

It doesn't necessarily mean that we cannot do calculations when recalling , like in the gcd . But when we do , this recursion is not a pure recursion but a pseudo one .

And almost all pseudo recursion can be changed into the loop statement in a mechanical way.

### *printf type ( void function )*

```C
// reversed number (print ou a number in a reversed order)
void reversenum ( int n )
{
    if( n!=0 )
    printf("%d",n%10);
    reversenum( n/10 );
}
```

```C
// sequential number (print out a number in a sequential order)
void printdigits ( int n )
{
    if( n<10 )
    printf( "%d", n );
    printdigits( n/10 );
    printf( "%d" , n%10 );
}
```

```C
// hanoi (print out the moving steps)
void hanoi( int n , char src , char aug , char tar )
{
    if( n>0 )
    {
    hanoi( n-1 , src , tar , aug );
    printf("%d : %c -> %c" , n , src , tar );
    hanoi( n-1 , aug , src , tar );
    }
}

/*we can also compute the least steps it takes to get to tar from src by using recursion , from the above procedure*/

int hanum( int n )
{
    if( n==1 )
    {
        return 1;
    }
    return 2 * hanum ( n-1 ) + 1;
}
```

#### Analyses2

It seems to be more abstract to understand the printf type recursion because we can't easily write the math piecewise form of the function , which means it is difficult to complete the code in a mechanical way. But we should pay attention to the logic of the process ,but not the specific details.The process goes on on the assumption that we are capable of doing the (n-1)th case,and all we need to do is think how we can finish the n th case, by building connection with the (n-1)th case.

## Conclusion

The recursion algrithm is a very powerful tool in programming, we need to get accustomed to it in practice . Read more , type more and more importantly , think more.
