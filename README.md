# CSV_to_JSON_and_JSON_to_CSV_roundtrip_converter
#### data source: Consumer Complaint Database data found at https://catalog.data.gov/dataset/consumer-complaint-database#topic=consumer_navigation
###  Description:
In this week, we examined CSV and JSON file formats. We wrote code to manually convert a specific CSV file to a specific JSON in the process. The code is RAW shown below:
- > import json
- > import csv

### Read CSV file. This wouldn't work well for very large files
- > with open('data_1/scientists.csv') as f:
- >    reader = csv.DictReader(f)
- >    rows = list(reader)
    
### Write JSON file to disk
- > with open('data_1/scientists.json', 'w') as f:
- > json.dump(rows, f)
## Part 1
The comment above the CSV section makes an assumption and says it wouldn't work for large files. Use the following articles to understand the terms eager evaluation and lazy evaluation:

https://en.wikipedia.org/wiki/Eager_evaluation

https://en.wikipedia.org/wiki/Lazy_evaluation

Now answer the following questions:
### In light of the two definitions above, what is the assumption made by that comment?
Considering the two Wikipedia definitions above, along with the comment that this wouldn’t work well with large files, it can lead us to the assumption that the code outlined in the cell is using lazy evaluation. This assumption is likely because the definition of eager evaluation focuses on the ability to be easily replicate/understandable, easy to debug, and requires code optimization processes such as creating a variable for such as pathfile or x, in replace of the actual path that needed to be placed in every cell as demonstrated in this example. The comment is likely used to show that this cell is coded in lazy evaluation technique, as it would be difficult to replicate this code to build out, especially if the programmer needs to change the filepath in every cell rather than simply creating something like: filepath = ‘data_1/scientists.csv’. If the program used eager evaluation, we could simply use the command with open(filepath) as f: -- to place into the reader without the need to keep placing the filename in each individual line that needs to call to that specific file. If eager was used, we could then re-use this code for other dataset and not worry about all the times we called to one dataset throughout the program, with potential to make mistakes while converting datasets. This comment indicates that this is lazy evaluation and could be optimized by updating to eager evaluation for future use of the program that will likely result in higher performance, effective barring of the compiler from performing re-order operations on the code block helping to optimize results. 
### Explain why that assumption is right or wrong.
The assumption that the original code is not in eager evaluation format due to the consideration of abstraction, or putting code into a function to take the code block as a whole to have the filename as the input, read as csv, and output as similarly named file in json/csv format. The original code has the filepath inserted when needed and does not use a variable as used in abstraction which is part of eager evaluation format. With this assumption, we can assume that the code will need to be adjusted to eager evaluation format for easier use of the block in the future. With this assumption, we will be changing that code in this lab which we will demonstrate below. According to the Zoom video posted in this week’s content, abstraction and converting to eager evaluation will help the longevity for reapplying blocks of code for future use without the risk of changing cells that could have been pre-programmed using eager evaluation formatting. 
### Is it safe to use the code above on large files?
According to the Zoom video in this week’s content section, this would not be safe to use on large files as it risks many errors or debugging when repurposing this code. If we store eager evaluation, pre-built blocks of code – it will be simple and less risky to reuse. Also, it will be quicker and more effective to call to the filename once and place at the beginning of the file to easily insert a new filepath if working on new data. The programmer will not need to search for every line of code that has the filepath inserted when needed, as demonstrated in the lazy evaluation method. It would be highly recommended to have eager evaluation formatting to eliminate safety & risk concerns of corrupting your data or causing errors that could result in many hours of debugging. With eager evaluation, the programmer can simply copy/paste their new filepaths of new datasets and plug & play with little to no risk of damaging the program and having to debug errors that could have been avoided by spending a little extra time to format the filepaths into blocks of code that can be reused over & over with confidence. 
## Part 2
Programmers hate code written for a specific case, "I don't care if it can solve one special case, I want it to solve all cases." This generalization process is called "abstraction".

Generalize the CSV->JSON code above into a function that can work for any CSV file and any JSON file (within reason).
Being able to convert in only one direction is only helpful half the time. Specious math aside,

Write a generalized JSON->CSV converter function.

Use the functions to do a "round-trip" (CSV->JSON->CSV or JSON->CSV->JSON) on the Consumer Complaint Database data found at https://catalog.data.gov/dataset/consumer-complaint-database#topic=consumer_navigation

When you are done with the two functions, the original and the round-trip files should be reasonably identical.

Hint: Mac and Linux have a command line tool called 'diff' that will show differences between two files. Windows users can use the 'fc' command on the command line. See this answer on StackOverflow for alternatives: https://stackoverflow.com/questions/6877238/what-is-the-windows-equivalent-of-the-diff-command

Also: No using libraries like Pandas that will automatically do the conversion!! The purpose of this exercise is for you to get a fairly deep understanding of the two formats and using a converter will not fulfill that purpose.
#### Lazy evaluation -- 
we will keep this cell RAW and will not run it, as we will use the eager evaluation method below
import json
import csv

### Read CSV file. This wouldn't work well for very large files
- > with open('complaints.csv', encoding="UTF-8") as f:
- >    reader = csv.DictReader(f)
- >    rows = list(reader)
    
### Write JSON file to disk
- >with open('complaints.json', 'w', encoding="UTF-8") as f:
- >    json.dump(rows, f)
### Eager Evaluation
### 1 -- Abstraction -- Generalize the CSV->JSON code above into a function that can work for any CSV file and any JSON file (within reason).
Using abstraction with the variables -- this makes for easy code to replicate and uses in blocks in the future. this is more efficient and effective to simply adjust the filenames on the top, and then we should never need to adjust them anywhere throughout due to using variables in place of file names. AKA - using eager vs lazy evaluation programming. We see the gerneralized CSV>JSON converted outlined in RAW format in the cell below: (note we will use this a few cells down to demonstrate)
csvFilePath = 'filename.csv'
jsonFilePath = 'filename.json'

### Read CSV file. 
- > with open(csvFilePath, encoding="UTF-8") as f:
- >    reader = csv.DictReader(f)
- >    rows = list(reader)
    
### Write JSON file to disk
- > with open(jsonFilePath, 'w', encoding="UTF-8") as f:
- >    json.dump(rows, f)
#### Eager Evaluation & Abstraction 
Using abstraction with the variables -- this makes for easy code to replicate and uses in blocks in the future. this is more efficient and effective to simply adjust the filenames on the top, and then we should never need to adjust them anywhere throughout due to using variables in place of file names. AKA - using eager vs lazy evaluation programming.
## Summary
In conclusion, we described the difference between lazy & eager evaluation as well as creating a generalized CSV>JSON JSON>CSV "roundtrip" converter successfully. We were able to populate a new json file from just csv and csv file from just json. We were also succesfully able to convert the  Consumer Complaint Database data found at https://catalog.data.gov/dataset/consumer-complaint-database#topic=consumer_navigation with little to no change to the data after conversion. 
