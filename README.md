# structuring-OCR-text
Converts unstructured OCR text to structured Python dictionary

The code I have written, accomplishes the following:

Reads through all files one by one, looking for occurrences of float numbers.

Looks for parameter names in the starting index of every line cross referenced by data from 'X1.json', and if found, appends that line to the data

To look for latest data for a parameter: it considers the last value in the string as the latest parameter. This is an implicit assumption I am making because dates appear to be arranged chronologically. Therefore by default, the last value will be the latest one.

Lastly, I have filtered data and added it to a dictionary as required.

I have also assumed the files that are going to read as source data are present in the current working directory of the user.

Helper Functions I used: 
a) Time pattern matching 
b) Date pattern matching 
c) float detection 
d) file reading 
e) searching in json file for reading through X1.json

Some things I have not been able to accomplish due to the shortage of time:

Correct for OCR errors - I had planned on utilising Levenshtein Distance to correct for OCR errors.

Unable to extract the 'unit' key for the dicitonary to non uniformity of unit values. A potential approach: A dictionary listing all kinds of units would have been helpful in extracting the unit keys.