# Marbles and Boxes : Editorial
This problem can be easily solved with some knowledge of combinatorics and very basic dynamic programming.<br>
<b>Derangement principle : </b> It is a permutation of the elements of a set in which no element appears in its original position. Example : 
  suppose we have a permutation $(1,2,3,4,5)$, then a derangement would be $(2,4,5,1,3)$ as no element is in its original position.<br>
  Clearly, the number of ways in which we can derange a set containing $n$ distinct elements are $n!-N$, where $N$ is the number of ways where atleast 
  one element is in the right place.<br>
  If $D_n$ is the number of ways of deranging a set of n elements, then using the above relation, it can be shown that :<br>
                    $$D_n=n!(1-\frac{1}{1!}+\frac{1}{2!}-\frac{1}{3!}+...+(-1)^n\frac{1}{n!})$$<br><br>
  Calculating $D_n$ from the above formula can severely affect the time complexity, hence, we derive a recursive relation for $D_n$ and use DP to find $D_n$.<br>
  Consider a permutation $(1,2,3...n)$. Let us have $k (1 \lt k \le n)$ such that $k$ occupies the first position. Now two cases arise : <br>
  1. $1$ goes to $k^{th}$ position  : In this case, we are left with a total of $n-2$ numbers to derange, which can be done in $D_{n-2}$ ways.<br>
  2. $1$ does not go to $k^{th}$ position : In this case, All we need to do is to derange the remaining $n-1$ numbers which can be done in $D_{n-1}$ ways.<br>
     Thus, for any $k$, we have $D_{n-1}+D_{n-2}$ ways of deranging the set if $k$ goes to the first place. Since we can chose $k$ in ${n-1} \choose 1$ ways, the total number of ways of deranging the entire set are :
     $$D_n=(n-1)(D_{n-1}+D_{n-2})$$ which is the required recursive relation.<br>
     Now, coming to the actual problem, Clearly, B will win if either no ball falls in the same numbered box, which can happen in $D_n$ ways, or exactly one ball falls into the right box, which can happen in $n \choose 1$ times $D_{n-1}$ ways. Hence, for a given n, if $T_n$ is the number of ways in which B can win, then :
     $$T_n=D_n+nD_{n-1}$$<br><br>
Approach:
For a given $n$, we need $D_n$. Hence we implement dynamic programming to calculate $D_n$ using the recursive relation derived above.(Exact code is given in the solution). Now all we need is $D_n$ and $D_{n-1}$, using which, we output the final answer $T_n$.<br><br>

<b>Time Complexity:</b> $O(n)$ 

  
  
  
