# Maximum_Common_Sub_String
This code will find maximum common sub string from given two strings and print the maximum length as well max sub string. The code is well explained with comments!!
<>code
package Advanced_Programming;
//importing java.util.* to use Scanner class 
import java.util.*;
public class LongestCommanSub_String {
   
	public static void main(String[] args) {
		//creating scanner object..
		 Scanner sc=new Scanner(System.in);
		//Taking first string input...
		  System.out.println("Enter the first String: ");
		  String str1=sc.next();
		//Taking second string input...
		  System.out.println("Enter the second String : ");
		   String str2=sc.next();
		//Creating table of one greater row and column, 
		   //one more for base condition
	      int [][]table=new int[str1.length()+1][str2.length()+1];
	      
	      for(int i=0;i<=str1.length();i++){
	    	  for(int j=0;j<=str2.length();j++){
	    		//Base condition...
	    		  if(i==0||j==0){table[i][j]=0;}
	    		  //if char at some index of string1 is equal to char at some index2 than..
	    		  //we will count it as 1+max common at 1 step before i.e: [i-1,j-1]
	    		  else if(str1.charAt(i-1)==str2.charAt(j-1)){table[i][j]=1+table[i-1][j-1];}
	    		  //If char are not equals just put 0 saying they are not equals..
	    		  else if(str1.charAt(i-1)!=str2.charAt(j-1)){table[i][j]=0;}
	    	  }
	      } int max=0,indexi=0,indexj=0;
	      //loop through to get max length
	      for(int i1=0;i1<str1.length()+1;i1++){
	    	  for(int j1=0;j1<str2.length()+1;j1++){
	    		  //Comparison for maximum length
	    		  if(max<=table[i1][j1]){
	    			  max=table[i1][j1];
	    			  //maintaining two indices to use it later while actuall constructing max common sub string  
	    			  indexi=i1;
	    			  indexj=j1;}
	    	  }
	    	 
	      }//printing the maximum length of common sub_string
	      System.out.println("Length of max sub_string is : "+max);
	      //creating an object of StringBuilder class since appending is not possible in string
	      StringBuilder sb=new StringBuilder();
	    //looping with stored indices to create sub_string
	     while(true){
	    	 //loop exit condition when characters are not same or indices becomes 0; 
	    	 if(indexi==0|| indexj==0 ||str1.charAt(indexi-1)!=str2.charAt(indexj-1)){break;}
	    	 indexi--;
	    	  indexj--;
	    	  //appending character by character
	    	  sb.append(str1.charAt(indexi));
	    	  
	     }
	     StringBuilder sb1=new StringBuilder();
	     //reversing the string since we got it in reverse order
	     sb1=sb.reverse();
	     //converting into string to print
	    String s=sb1.toString();
	   //printing the value
	    System.out.println("Max common sub_string is : "+s);

	}

}
