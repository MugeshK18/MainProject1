# MainProject1
interface Company
{
	String COMPANYNAME= "ABC";   
	static void getCompanyName()
	{
		System.out.println("Company Name is : " +COMPANYNAME);
	}
}

class Employee                                             //Single Inheritance
{  
	static String companyCeo;
	private int empId;
	private String empName;
	private int empSalary; 
	public void setEmpDetails(int empId,String empName,int empSalary)
	{
		this.empId=empId;
		this.empName=empName;
		this.empSalary=empSalary;	
	}
	public void getEmpDetails()
	{
		System.out.println("Employee's ID & Name & Salary are: "+empId+", "+empName+", "+empSalary);
	}
} 
class Department extends Employee                            //Multilevel inheritance             
{
	private String empDepart;
	private String empDesignation;	
	public void setCeoDetails(String name)
	{
		companyCeo=name;
	}
	public void setEmpDetails(String empDepart,String empDesignation)
	{
		this.empDepart=empDepart;
		this.empDesignation=empDesignation;
	}
	public static void getCeoDetails()
	{
		System.out.println("Company's CEO is: " +companyCeo);
	}
	public void getEmpDetails()
	{
		super.getEmpDetails();
		System.out.println("Employee's Department & Designation are: "+empDepart+", "+empDesignation);
	}
	
}


class Display extends Department implements Company           //Multiple inheritance
{
	public void getCompanyName()
	{
		Company.getCompanyName();
	}
	public void getEmpDetails()
	{
		Display.getCeoDetails();
		super.getEmpDetails();
	}
}
public class MainProject1 {
	public static void main(String[] args) {
  
		String name[]= {"Mugesh","Navin","Mani"};
		int id[]= {01,02,03};
		int salary[]= {1000,2000,3000};
		String depart[]= {"Developing","Human Resources","Management"};
		String designation[]= {"System Engineer","HR Manager","Manager"};
		
		Display emp[]= {new Display(),new Display(),new Display()};
		
		for(int i=0;i<3;i++)
		{
			emp[i].setCeoDetails("Rahul");
			
			emp[i].setEmpDetails(depart[i],designation[i]);
			emp[i].setEmpDetails(id[i],name[i],salary[i]);
			if(i>1)
			{
				//Company.COMPANYNAME="XYZ";       //changing the company name from "ABC" to "XYZ"
				emp[i].setCeoDetails("Preeti");    //changing the company ceo from "Rahul" to "Preeti"
				
			}
		}
		for(int j=0;j<3;j++)
		{
			emp[j].getCompanyName();
			emp[j].getEmpDetails();
			System.out.println();
		}	
	}

}
