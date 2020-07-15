# happy-number-and-prime-no-intersection
CodeVita 2013 : Solution of Game of Primes



import java.util.*;
import java.io.*;

public class HelloWorld
{

     public static void main(String []args)
     {
         Scanner sc=new Scanner(System.in);
         int l=sc.nextInt();
         int h=sc.nextInt();
         int n=sc.nextInt();
         System.out.println(check(l,h,n));
     }
     static int check(int l,int h,int n)
     {
         List<Integer> li=prime(l,h);
          
         List<Integer> li1=happy(li);
         for(int j=0;j<li1.size();j++)
          {
              System.out.println(li1.get(j));
          }
        
         
        return  li1.get(n-1);
     }
     static List<Integer> prime(int l,int h)
     {
        List<Integer> li=new ArrayList<>();
        int count=0;
        for(int i=l;i<=h;i++)
        {
            count=0;
            for(int j=2;j<Math.sqrt(i)+1;j++)
            {
                if(i==2)
                {
                    break;
                }
                if(i%j==0 )
                {
                    count++;
                    break;
                }
            }
            if(count==0)
            {
                li.add(i);
            }
        }
        return li;
     }
     static List<Integer> happy(List<Integer> li)
     {
        List<Integer> li1=new ArrayList<>();
        for(int i=0;i<li.size();i++)
       {
           int temp=li.get(i);
           int sum=0;
           int rem=0;
           while(sum!=1 && sum!=4)
           {
               sum=0;
               while(temp!=0)
               {
                   rem=temp%10;
                   sum=sum+rem*rem;
                   temp=temp/10;
                   
               }
               temp=sum;
           }
           if(sum==1 )
           {
               li1.add(li.get(i));
           }
       }
         
       return li1;  
     }
}
