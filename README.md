# NumberAnalysisClass
public class NumberAnalysisClass {
    
    
	private double[] numbers;
        private String file;
	
	public NumberAnalysisClass(String fileName) throws IOException
	{
                file = fileName;
		numbers = new double[getLines(file)];
		readFile(file);
	}
	
	public double getTotal()
	{
		double total = 0;
		
		for(int index = 0; index < numbers.length; index++)
		{
			total += numbers[index];
		}
		
		return total;
	}
	
	public double getMinimum()
	{
		double minimum = numbers[0];
		
		for(int index = 0; index < numbers.length; index++)
		{
			if(minimum > numbers[index])
			{
				minimum = numbers[index];
			}
		}
		
		return minimum;
	}
	
	public double getMaximum()
	{
		double maximum = numbers[0];
		
		for(int index = 0; index < numbers.length; index++)
		{
			if(maximum < numbers[index])
			{
				maximum = numbers[index];
			}
		}
		
		return maximum;
	}
	
	public double getAverage()
	{
		return getTotal()/numbers.length;
	}
	
	private void readFile(String fileName) throws IOException
	{
		File inputFile = new File(fileName);
                Scanner readFile = new Scanner(inputFile);
                int index = 0;
                
		while(readFile.hasNext() && index < numbers.length)
		{
			numbers[index] = readFile.nextInt();
		}
            System.out.println(Arrays.toString(numbers));
            readFile.close();
	}
	
        public static int getLines(String filename) throws IOException 
        {
                File file =new File(filename);
                int linenumber = 0;

    		if(file.exists())
                {

    		    FileReader fr = new FileReader(file);
    		    LineNumberReader lnr = new LineNumberReader(fr);

    		    

    	            while (lnr.readLine() != null)
                    {
    	        	linenumber++;
    	            }
                    
                    System.out.println("The total number of lines is: " + linenumber);
                    lnr.close();
                }
                else
                {
    			 System.out.println("File does not exists!");
    		}
            return linenumber;    
        }
	
}
