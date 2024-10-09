import java.io.File; // for File
import java.io.FileNotFoundException;//to deal with errors
import java.util.Scanner;//for user input


public class New {
	public static void main(String[] args) throws FileNotFoundException{
		
		Scanner console = new Scanner (System.in);// Reads user input
		
		System.out.println("Please enter the file name: ");//asks user for the file name
		String filename = console.next();//declaring a variable "filename", stores user's input  
		
		try {
			Scanner input = new Scanner (new File(filename)); //reads from file
			int size = input.nextInt();//reads number form file
			
			double[] numbers = new double[size];//declare array numbers of type double of size 20		
					for (int i = 0; i < size; i++) { //for loop in reading in array
						numbers [i] = input.nextDouble(); //putting data int; read from the file 
					}//end for loop
					
			//finding mean
					double sum1 = 0.0;
					for (double num : numbers) {
						sum1 += num;
					}
					double mean = sum1 / size;
			
			//finding standard deviation
			double sum2 = 0.0;
					for (double num : numbers) {
						sum2 += Math.pow(num - mean,  2);
					}
					double standardDeviation = Math.sqrt (sum2 / size);
					
			//Printing out the results		
					System.out.println("The file " + filename + " has " + size + " numbers in it.");
			        System.out.println("The numbers are:");
			        for (double num : numbers) {
			            System.out.print(num + " ");
			        }
			        System.out.println("\nThe mean is " + mean);
			        System.out.printf("The standard deviation is " + "%.2f",standardDeviation);
			        System.out.println();
			        System.out.print("Thanks!");
			
			 input.close();//Scanner closed
		}catch (FileNotFoundException e) {
			System.out.println("Not available: " + filename);//the exception
		}//end FileNotFound try/catch method
		console.close();
		
	}//end main
}//end class

