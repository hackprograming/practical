# Java Practical 
### Q1   Define a class MyDate (day, month, year) with methods to accept and display a MyDate object. Accept date as dd, mm, yyyy. Throw user defined exception “InvalidDateException” if the date is invalid. Examples of invalid dates : 03 15 2019, 31 6 2000, 29 2 2021

```
import java.util.*;
abstract class staff
{
    protected String name,address;
    staff(String name,String address)
    {
        this.name=name;
        this.address=address;   
    }
}
class fulltimestaff extends staff
{
    String dept;
    int salary;
    fulltimestaff(String name,String dept,String address,int salary)
    {
        super(name,address);
        this.dept=dept;
        this.salary=salary;
    }
    void disp()
    {
        System.out.println("name:"+name);
        System.out.println("department:"+dept);
        System.out.println("Address:"+address);   
        System.out.println("Salary:"+salary);   
        
    }
}
class parttimestaff extends staff
{
    int no_of_hrs,rate_pr_hrs;
    parttimestaff(int no_of_hrs,int rate_pr_hrs,String name,String address)
    {
        super(name,address);
        this.no_of_hrs=no_of_hrs;
        this.rate_pr_hrs=rate_pr_hrs;
    }
    void disp()
    {
        System.out.println("name:"+name);
        System.out.println("Address:"+address);   
        System.out.println("No of hours:"+no_of_hrs);   
        System.out.println("Rate per hours:"+rate_pr_hrs);      
    }
}
public class staff1
{
    public static void main(String a[])
    {
    	int ch;
        Scanner sc=new Scanner(System.in);
        System.out.println("Enter the limit:");
        int n=sc.nextInt();
        fulltimestaff ob[]=new fulltimestaff[n];
        parttimestaff ob1[]=new parttimestaff[n];
        do {
        System.out.println("1.Fulltimestaff\n2.Parttimestaff\nEnter the choice:");
        ch=sc.nextInt();
        switch(ch)
        {
        case 1:
        for(int i=0;i<n;i++)
        {
            System.out.println("Enter name:");
            String name=sc.next();
            System.out.println("Enter department:");
            String dept=sc.next();
            System.out.println("Enter address:");
            String address=sc.next();
            System.out.println("Enter salary:");
            int salary=sc.nextInt();
            ob[i]=new fulltimestaff(name,dept,address,salary);
            ob[i].disp();
        }break;
        case 2:
        for(int i=0;i<n;i++)
        {
        	System.out.println("Enter no_of_hrs:");
            int no_of_hrs=sc.nextInt();
        	System.out.println("Enter rate per hours:");
            int rate_pr_hrs=sc.nextInt();
        	System.out.println("Enter name:");
            String name=sc.next();
            System.out.println("Enter address:");
            String address=sc.next();
            ob1[i]=new parttimestaff(no_of_hrs,rate_pr_hrs,name,address);
            ob1[i].disp();
        }
        break;
        default:System.out.println("Wrong choice");
                System.exit(0);
        }
        }while(ch<3);
    }
}

```
### Q2  Define a class patient (patient_name, patient_age, patient_oxy_level,patient_HRCT_report). Create an object of patient. Handle appropriate exception while patient oxygen level less than 95% and HRCT scan report greater than 10, then throw user defined Exception “Patient is Covid Positive(+) and Need to Hospitalized” otherwise display its information.
```

import java.util.*;
class CovidException extends Exception
{
    public String toString()
    {
        return "Patient is Covid Positive and need to Hospitilized";
    }
}
public class patient
{
    String pname;
    int age,olevel,hrct;
    void accept()
    {
        try
        {
            Scanner sc=new Scanner(System.in);
            System.out.println("Enter Patient Name::");
            pname=sc.next();
            System.out.println("Enter Patient AGE::");
            age=sc.nextInt();
            System.out.println("Enter Oxygen Level::");
            olevel=sc.nextInt();
            System.out.println("Enter HRCT Score::");
            hrct=sc.nextInt();
            if(olevel<=95 && hrct>=10)
            {
                throw new CovidException();
            }
            disp();
        }catch(Exception e)
        {
            System.out.println("Errorrrrr=="+e);
        }
    }
void disp()
{
    System.out.println("Patient Name::"+pname);
    System.out.println("Patient AGE::"+age);
    System.out.println("Oxygen Level::"+olevel);
    System.out.println("HRCT Level::"+hrct);
}
public static void main(String args[])
{
    patient ob=new patient();
    ob.accept();
}

}
```
