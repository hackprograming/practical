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
# PHP (Web Technology Practical)
### 1 ) Write a PHP program to Upload the file and display its information like its name, size, type, etc.
```
<!DOCTYPE html>
<html lang="en">
<head>
 <meta charset="UTF-8">
 <title>File Upload Form</title>
</head>
<body>
 <form method="post" enctype="multipart/form-data">
 <h2>Upload File</h2>
 <label for="fileSelect">Filename:</label>
 <input type="file" name="photo" id="fileSelect">
 <input type="submit" name="submit" value="Upload">
 <p><strong>Note:</strong> Only .jpg, .jpeg, .gif, .png formats allowed to a max size of 5 
MB.</p>
 </form>
</body>
</html>
<?php
if($_SERVER["REQUEST_METHOD"] == "POST")
{
 
 if(isset($_FILES["photo"]) && $_FILES["photo"]["error"] == 0)
 {
 $allowed = array("jpg" => "image/jpg", "jpeg" => "image/jpeg", "gif" => "image/gif", 
"png" => "image/png");
 $filename = $_FILES["photo"]["name"];
 $filetype = $_FILES["photo"]["type"];
 $filesize = $_FILES["photo"]["size"];
 $target_path="F:/programs/";
 
 $ext = pathinfo($filename, PATHINFO_EXTENSION);
 if(!array_key_exists($ext, $allowed)) 
 die("Error: Please select a valid file format.");
 
 
 $maxsize = 5 * 1024 * 1024;
 if($filesize > $maxsize) 
 die("Error: File size is larger than the allowed limit.");
if(in_array($filetype, $allowed))
{ 
move_uploaded_file($_FILES["photo"]["tmp_name"], "F:/programs/".$filename);
 echo "Your file was uploaded successfully.";
 
 } 
 else
 {
echo "Error: There was a problem uploading your file. Please try again."; 
 }
 }
 else
 {
 echo "Error: " . $_FILES["photo"]["error"];
 }
}
?>
```
### 2) Write a PHP program to accept student information like name, address, class, and Upload student photo and display same on form.
```
<html>
<head>
<title>PHP File Upload example</title>
</head>
<body>
<form enctype="multipart/form-data" method="post">
Name: <input type="text" name="name"><br><br>
Address:<input type="text" name="addr"><br><br>
Class:<input type="text" name="class"><br><br>
<input type="file" name="file">
<input type="submit" value="Upload" name="Submit1"> <br/>
</form>
<?php
if(isset($_POST['Submit1']))
{ 
$name=$_POST['name'];
$addr=$_POST['addr'];
$class=$_POST['class'];
$filepath = "images/" . $_FILES["file"]["name"];
move_uploaded_file($_FILES["file"]["tmp_name"], $filepath);
echo"<tableborder=1><tr><th>Name</th><th>class</th><th>Address</th><th
>Photo</th>";
echo "</tr><tr><td>".$name."</td>";
echo "<td>$class</td>";
echo "<td>".$addr."</td>";
echo "<td><img src=".$filepath." height=100 width=100 /></td></tr>";
echo "</table>";
} 
?>
</body>
</html>
```
### 3) Write a PHP program to accept Name, address, Pincode ,Gender information .if any field is blank ,it displays “All fields are required ” .if Pincode is more than 6 digits ,it should give error.
```
<html>
<body><form method="POST">
Name: <input type="text" name="name" required="all fields re"><br><br>
class: <input type="text" name="class" required=""><br><br>
Pincode:<input type="text" name="pincode" required=""><br><br>
Gender:<input type="text" name="gender" required="" ><br><br>
<button >submit</button>
</body>
</html>
<?php
@$name=$_POST['name'];
@$class=$_POST['class'];
@$pincode=$_POST['pincode'];
@$gender=$_POST['gender'];
$size=count_digit($pincode);
if($size>6)
{
echo "Error:it should be less than 6";
}
function count_digit($number)
{
 return strlen((string) $number);
}
?>
```
## Q. 4) : Write a PHP script for the following: Design a form having a text box and a drop down list containing any 3 separators(e.g. #, |, %, @, ! orcomma) accept a strings from the user and also a separator.a. Splitthe string into separate words using the given separator. b. Replace all the occurrences of separator in the given string with some other separator.c. Find the last word in the given string(Use strrstr() function). (Incomplit-program)

```
<html>

<form  method='post'>

<input type="text" name="string" />
<select id="separator" name="separator">                      
<option value="0">--Select separator--</option>
<option value="1">#</option>
<option value="2">|</option>
<option value="3">%</option>
<br /><br/ ><br/ >
<br><input type="radio" name="radio" value="op1"> <b>Splitthe string into separate words using the given separator</b>  <br/ ><br/ >
<input type="radio" name="radio" value="op2"><b>Replace all the occurrences of separator in the given string with some other separator</b> <br/ ><br/ >
<input type="radio" name="radio" value="op3"><b>Find the last word in the given string(Use strrstr() function). <b/><br/ ><br/ >

<input type="submit" name="submit" value="Submit" />
</form>

</body>

</html>
<?php
if(isset($_POST['submit']))
{
    $seprator=$_POST['separator'];
    $string=$_POST['string'];
    if(!empty($_POST['radio'])) {
        $option= $_POST['radio'];
       }
       if($option=="op1")
       {
        option1($seprator,$string);
        //$results=explode($seprator,$string);
        //foreach($results as $result){
        //  echo $result;
        //}
       
       }

     

  
}
function option1($seprator,$string)
{
  
    //var_dump(explode('$seprator', $string ) );
   //print_r(explode($seprator,$string,3));
   $chars = preg_split('*', $string, -1, PREG_SPLIT_NO_EMPTY);
   print_r($chars);
}
?>

```
