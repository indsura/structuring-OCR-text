# structuring-OCR-text
## Converts unstructured OCR text to structured Python dictionary

## Initial Data Analysis: 

##### Parameter names are listed at the start of every line (for most cases). For example: 'RCC (3.9-5.8) x10°12 /L 4.1 3.7 4.0 3.8'

##### Test Result Values are float values, not necessarily integers

##### Quite a few OCR errors, hence distorting parameter names and values in some cases: 'Iron' becomes 'Tron'

##### Dates appear to be arranged chronologically in the given corpus. For example: 'Date Collected 12 Sep 17 8 Nov 17 30 Apr 18 10 Dec 18'


## With the help of facts made available from above data analysis, the code I have written, accomplishes the following:

Reads through all files one by one and saves it in a variable 'all_data'

#### In every line that it looks through, it looks for: 
	#### Occurrences of float numbers indicating 'value' key of test results
	
	##### Parameter names 
		###### While reading a line, if a parameter name is found in the first word of the line, it appends that line to the data, assuming that it contains important test result values and units in the same line. 
		
		###### Implicit assumption: that the parameter name is listed as the starting word in the line Potential downside is that it will disregard any sentence containing test result values if that sentence does not start with listing which parameter is being tested for, hence impacting accuracy. Additionally, if parameter name and parameter value are in different lines, my code will disregard those values.
	

#### To look for latest data for a parameter: it considers the last value in the line / sentence as the latest parameter.

For example: if the line is this: 'RCC (3.9-5.8) x10°12 /L 4.1 3.7 4.0 3.8' my code will only consider as value for RCC parameter as 3.8

This is an implicit assumption I am making because dates appear to be arranged chronologically in the given corpus. Therefore by default, the last value will be the latest one.

#### Lastly, I have filtered data and added it to a dictionary as required.

#### I have also assumed the files that are going to read as source data are present in the current working directory of the user.

### Helper Functions I used: 
a) Time pattern matching 
b) Date pattern matching 
c) float detection 
d) file reading 
e) searching in json file for reading through X1.json

## Some things I have not been able to accomplish due to the shortage of time:

Correct for OCR errors - I had planned on utilising Levenshtein Distance to correct for OCR errors.

Unable to extract the 'unit' key for the dicitonary to non uniformity of unit values. A potential approach: A dictionary listing all kinds of units would have been helpful in extracting the unit keys.