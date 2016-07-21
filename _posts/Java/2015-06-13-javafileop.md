```
 public static void main(String[] args)  {
  	String name = "C:/Users/luping/Desktop/suggest.csv";
  	 Reader inputStreamReader;
	try {
		inputStreamReader = new InputStreamReader(new FileInputStream(new java.io.File(name)));
		 CSVReader reader = new CSVReader(inputStreamReader); 
		   String[] nextLine;  
		  while (( nextLine = reader.readNext()) != null)  {
			  for (int i = 0; i < nextLine.length; i++) {
				System.out.println(nextLine[i]);
			}
		  }
	} catch (FileNotFoundException e) {
		e.printStackTrace();
	}catch (IOException e) {
		e.printStackTrace();
	}
}
```
