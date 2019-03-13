import java.io.*;
import java.util.*;
import java.text.*;
import java.math.*;
import java.util.regex.*;
public class TestClass {
	 public static void main(String[] args) { 
	Scanner sc=new Scanner(System.in);
       int T=sc.nextInt();
       TreeSet<Student> t=new TreeSet<Student>();
       while(T>0)
       {
         String e=sc.next();
         if(e.equalsIgnoreCase("ENTER"))
         {
           String name=sc.next();
           double cgpa=sc.nextDouble();
           int token=sc.nextInt();
           t.add(new Student(token, name, cgpa));
         }
         else if(e.equalsIgnoreCase("SERVED"))
         {
           if(t.size()>0)
           {
             Student s=t.first();
             t.remove(s);
           }
         }
         T--;
       }
       if(t.size()==0)
       {
         System.out.println("EMPTY");
       }
       for(Student student : t)
       {
         System.out.println(student.getFname());
       }
       sc.close();
     }
}

class Student implements Comparable<Student>
{
  private int token;
  private String fname;
  private double cgpa;
  public Student(int id,String fname,double cgpa)
  {
    super();
    this.token=id;
    this.fname=fname;
    this.cgpa=cgpa;
  }
  
  public int getToken()
  {
    return token;
  }
  public String getFname()
  {
    return fname;
  }
  public double getCgpa()
  {
    return cgpa;
  }
  
  @Override
  public int compareTo(Student arg0)
  {
    int out=0;
    out=-1*(new Double(cgpa)).compareTo(new Double(arg0.cgpa));
    if(out==0)
    {
      out=fname.compareTo(arg0.fname);
      if(out==0)
      {
        out=(new Integer(token).compareTo(new Integer(arg0.token)));
      }
    }
    return out;
  }
}
