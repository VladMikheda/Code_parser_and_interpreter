# Parser and Interpreter for IPPcode22


## Parser
Converts code written in IPPcode22 language into XML format. The code is read from standard input.

### Execution Examples 
```
php8.1 parse.php
```
nebo
```
php8.1 parse.php < file
```
pro zobrazeni informace 
```
php8.1 parse.php --help 
```

## Interpreter
Interprets the code converted into XML format and generates output.


### Parameters
+ --help: Displays information
+ --source=file: Specifies the input file with the XML representation of the source code
+ --input=file: Specifies the file with inputs for the interpretation of the source code.

At least one of the parameters (--source or --input) must always be provided. If one of them is missing, the missing data is read from standard input.
### Execution Examples
```
python interpret.py --source=code.xml --input=output.out
```

## Testing
The script is designed for testing the parser and interpreter, and it generates output in HTML format.    
To run tests you need jexam.

### Parameters 
+ --help: Displays information
+ --directory=path: Tests will be searched for in the specified directory (if this parameter is missing, the script searches in the current directory) 
+ --recursive: Tests will be searched for not only in the specified directory but also recursively in all its subdirectories
+ --parse-script=file: Specifies the PHP 8.1 script file for parsing the source code in IPPcode22 (if this parameter is missing, the default value is parse.php stored in the current directory) 
+ ---int-script=file: Specifies the Python 3.8 script file for interpreting the XML representation of the code in IPPcode22 (if this parameter is missing, the default value is interpret.py stored in the current directory)
+ --parse-only: Only the script for parsing the source code in IPPcode22 will be tested (this parameter cannot be combined with --int-only and --int-script parameters), with the output compared to the reference output (file with the out extension)  
+ --int-only: Only the script for interpreting the XML representation of the code in IPPcode22 will be tested (this parameter cannot be combined with --parse-only, --parse-script, and --jexampath parameters). The input program is represented using XML and will be stored in a file with the src extension
+ --jexampath=path: Specifies the path to the directory containing the jexamxml.jar file with the JAR package containing the A7Soft JExamXML tool and a configuration file named options. If this parameter is omitted, the default location /pub/courses/ipp/jexamxml/ on the Merlin server will be considered, where test.php will be evaluated. A trailing slash in the path may need to be added if necessary 
+ ---noclean: During the operation of test.php, auxiliary files with intermediate results will not be deleted, meaning the script will leave files created during the operation of tested scripts (e.g., the file with the resulting XML after running parse.php, etc.)

### Execution Examples
```
# Execution for testing two scripts
# with preservation of intermediate results
php8.1 directory=./tests --recursive  --jexampath=./jexampath --noclean
```
