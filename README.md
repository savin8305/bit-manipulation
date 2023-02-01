# Bit Manipulation Cheat Sheet
## You can be asked to On,Off,Toggle,Check (set,unset,update,check) particular bit of a binary number at a certain position. 
```java
 
    int n = scn.nextInt();
    int i = scn.nextInt();
    int j = scn.nextInt();
    int k = scn.nextInt();
    int m = scn.nextInt();

    int mask1 = 1 << i;
    int mask2 = 1 << j;
    int mask3 = 1 << k;
    int mask4 = 1 << m;

    System.out.println(n | mask1);
    System.out.println(n & (~mask2));
    System.out.println(n ^ mask3);
    System.out.println((n & mask4) == 0 ?  false : true);//check the mth bit is on or off 0 means ith bit is not set
    ```
## clear the range i to j 
```java
int a=(~0)<<(j+1);
int b=(1<<i)-1;
int mask=a|b;
int ans=n&mask;
return ans;
```
## find Right Most set bit mask
```java
int rsbm=n&-n;
```
## Kernighan's Algorithm to count set bits in a number
```java
while(n!=0){
  int rsbm=n&-n;
  n-=rsbm;
  counter++;
  }
```
## Check if two integers have opposite signs
```java
if(x^y >0)
    return false;
else
    return true;
```

## Add 1 to a given number
```c++
(-(~x));
```

## Multiply a number by 2
```c++
x<<1;
```

## Divide a number by 2
```c++
x>>1;
```

## Turn off the rightmost set bit
```c++
x&(x-1);
```

## Check whether a given number is a power of 4 or not
```c++
if(!(x & (x-1))){
    if(__builtin_ctz(x)%2==0)
        return true;
```
## Compute modulus division by a power-of-2-number
```c++
x & (powerOf2 - 1);
```
## Rotate bits of a number
```c++
int leftCircularShift(int x,int shiftBy)
    return (x<<shiftBy) | (x>>shiftBy);
int rightCircularShift(int x,int shiftBy)
    return (x>>shiftBy) | (x<<shiftBy);
```
## Count number of bits to be flipped to convert A to B
```c++
__builtin_popcount(a ^ b);
```
## Find whether a no is power of two
```c++
return (n>0 and !(n&(n-1)));
```
## Position of rightmost set bit
```c++
ffs(x);
//another way
log2(x & -x)+1;
//another way
if(x!=0)
    __builtin_ctz(x)+1;
```
## Calculate XOR from 1 to n
```c++
switch(n & 3) // n % 4  
{ 
    case 0: return n;     // if n is multiple of 4 
    case 1: return 1;     // If n % 4 gives remainder 1   
    case 2: return n + 1; // If n % 4 gives remainder 2     
    case 3: return 0;     // If n % 4 gives remainder 3   
} 
```
## Binary representation of a given number
```c++
void bin(unsigned n) 
{ 
    if (n > 1) 
        bin(n>>1); 
      
    cout<<(d & 1)<<endl;
}
```
## Find position of only set bit
```c++
if(!(n&(n-1)))
	ffs(n);
```
## Turn off a particular bit in a number
```c++
x & (~1<<(pos-1));
```
## Check if 2 numbers are equal
```c++
if((x ^ y))
    return false;
else
    return true;
```
## Find XOR of numbers without using xor operator
```c++
(x | y) & (~x | ~y);
```
## Swap three variables
```c++
x = x ^ y ^ z;
y = x ^ y ^ z;
z = x ^ y ^ z;
x = x ^ y ^ z;
```
## Toggle Kth bit of a number
```c++
x = x ^ 1<<(k-1);
```
## Toggle all bits except Kth bit of a number
```c++
x = ~(x ^ 1<<(k-1);)
```
## Set the rightmost unset bit
```c++
x = x | (x+1)
```
## Toggle the last m bits
```c++
x ^ ~(-1<<m);
```
## Maximum XOR-value of at-most k-elements from 1 to n
```c++
int x = log2(n) + 1;
return x<<1 - 1;
//Alt way
int res = 1; 
while (res <= n) 
    res <<= 1; 
// Finding number greater than 
// or equal to n with most significant  
// bit same as n. For example, if n is 
// 4, result is 7. If n is 5 or 6, result  
// is 7 
// Return res - 1 which denotes 
// a number with all bits set to 1 
return res - 1; 
``` 
## Check if a number is divisible by 8 using bitwise operators
```c++
return (((n >> 3) << 3) == n);
```
## Toggle bits of a number except first and last bits
```c++
int size = sizeof(int)*8 - __builtin_clz(n);
int one = (1<<(size-1))-1;
n = n ^ one;
n = n ^ 1;
```
# Toggle all even bits of a number
```c++
int temp = n,i=1;
while(temp){
    n = n ^ 1>>(i*2);
    i++;
    temp = temp>>1;
}
```
## Brian Kernighan’s Algorithm for counting set Bits
```c++
while(n){
    n &=(n-1);
    count++;
}
```
<!-- ///////////////////question practice////////////////////////////// -->
<!-- gray code -->
##  HOW TO FIND SIMILAR WORD IN STRING ARRAY USING MASK
``class Solution {
  public int similarPairs(String[] words) {
    int ans = 0;
    int[] masks = new int[words.length];
 for (int i = 0; i < words.length; ++i)
      masks[i] = getMask(words[i]);
 for (int i = 0; i < masks.length; ++i)
      for (int j = i + 1; j < masks.length; ++j)
        if (masks[i] == masks[j])
          ++ans;  return ans;
  } private int getMask(final String word) {
    int mask = 0;
    for ( char c : word.toCharArray())
      mask |= 1 << c - 'a';
      THIS WILL GIVE YOU MASK OF SIMILAR WORDS
    return mask;
  }
}
}
```
<!-- ///////////////////question practice////////////////////////////// -->
<!-- gray code -->

## Gray code Leetcode -89
```
   ##approach 1 using recursion
<!--    but   this is naive approach  and complexity is height to this approach that is why preferable solution is approach 2-->
   public ArrayList<String>solution(int n){
   if(n==1){
      ArrayList<String>bres=new ArrayList<>();
      bres.add("0");
      bres.add("1");
      return bres;
     }
   ArrayList<String>rres=solution(n-1);
   ArrayList<String>mres=new ArrayList<>():
   for(int i=0;i<rres.size();i++){
     String rstr=rres.get(i);
     mres.add("0"+rstr);
     }
     for(int i=rres.size()-1;i>=0;i--){
     String rstr=rres.get(i);
     mres.add("1"+rstr);
     }
     return mres;
   } 
      ##approach 2 using itertor and simple method i.e without recursion
      In this approach the trick behind this is that 
      for n=2;
      first is 0 starting point
      (0|2^0)or(2^0-1|2^0),
      (1|2^1,0|2^1),
      for n=3;
      first is 0 starting point
      (0|2^0)or(2^0-1|2^0),
      (1|2^1,0|2^1),
      ((2^2-1)|2^2,(2^2-2|2^2),(2^2-3|2^2),(2^2-4|2^2)),
     
     observation :  (2^i-j|2^n) i.e i>=0,j>=0 changing variable size , power of 2 means i
                    size-1 get or(|) by power of 2
     
     
      public List<Integer> grayCode(int n) {
      List<Integer> rs=new ArrayList<Integer>();
      rs.add(0);
      for(int i=0;i<n;i++){
        int size=rs.size();
        for(int k=size-1;k>=0;k--)
            rs.add(rs.get(k) | 1<<i);
       }
    return rs;
}

```

