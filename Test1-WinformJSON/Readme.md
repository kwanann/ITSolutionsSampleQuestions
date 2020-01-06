# Introduction

Due to the manual nature of lab testing, frequently the results from the lab may have errornous inputs depending on the readability of the lab assistant's handwriting.

As such there is a need to check and validate the results from the lab against a database of known barcodes and date of birth in order to ensure that the results are accurate.

Samples of lab results: [Sample Input.csv](Sample%20Input.csv)

Sample database input: [Sample Input.json](Sample%20Input.json)

# Description of project and tasks

## 1.1 End-user form

When an end-user runs the executable, it should prompt the user to select the lab result file (with a .csv extension filter). 

There after, it should cross reference the file directly with the database input via a web request to the database server (for sample input use this url https://raw.githubusercontent.com/kwanann/ITSolutionsSampleQuestions/master/Test1-WinformJSON/Sample%20Input.json)

Once the comparison is performed between the csv file and database server, the system should provide 2 grids. 

## 1.2 First Grid

The first grid should have the following columns first (barcode, DOB in lab result, DOB in database) followed by the rest of the columns in the lab result.
- List only records where the "DOB in lab result" and "DOB in database" are not the same
- For the  "DOB in lab result" column
-- it has to be editable
-- colored red if different from "DOB in database"
-- colored green if same as "DOB in database"

## 1.3 Second Grid

The second grid will have the same columns as the lab results, but listing only those for which the DOB in lab result and DOB in database matches exactly.

## 1.4 Action button

There will be a button at the end of the form called "Complete validation". 
- When the end user clicks this button, it will generate a combined output

## 1.5 Output files

**All output files must be stored in the same location as the path to the input file.**

The **main** output file will
- have the same columns as the input file
- matched dob records are copied wholesale
- the output file should have the following filename format: \[input file name\]\_\[V(Current datetime in yyyyMMdd-HHmmss)] e.g if the input file is labresults.csv, the output filename will be labresults_v20200106-083722.csv
- different dob records are copied wholesale with the exception that the dob value is from the dob input inside the *first grid*

A **secondary** output file will be generated in json format
- listing the records that are *originally wrong*
- the filename format should be \[input file name\]\_Wrong(Current datetime in yyMMdd-HHmmss)

A **third** output file *may* be generated
- IF there are still differences in dob after user has clicked on "Complete validation"
- This output file will have the same colums as the original input file, but with an additional db_dob column inserted after the dob column. 
- the filename format should be \[input file name\]\_ValidatedWrong(Current datetime in yyMMdd-HHmmss)
