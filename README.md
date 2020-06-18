# Steps to Reproduce the results:

## Prerequisites:

Hadoop must be installed in your system.
## Steps:
### 1. Switch the user (if you have created separate user for Hadoop)

$ su - username 

### 2. Clone the git repository / download the zipped file and put it inside the hadoop user.
### 3. Start Hadoop using the following commands:

$HADOOP_HOME/sbin/start-dfs 
$HADOOP_HOME/sbin/start-yarn

### 4. Put all the input data files (All CSV files) into the Hadoop file system (hdfs).

$ hdfs dfs -put input/*.csv /stock_analysis


### 5. We have already compiled the source files and created the jar file as stock.jar, so no need to do it again as we can directly use that jar file.
### 6. If you still wish to compile and create a jar file again, Compile All the java files present in src folder.
To create class files for mapper, reducer and the driver codes.

javac src/*.java -cp $(hadoop classpath)
* means put names of all files in place of star.

### 7. Create a jar file using        

$ jar -cvf stock.jar -C bin/ .


### 8. Run the program on the data present in the hdfs :

$ hadoop jar stock.jar MainStockAnalysis  /stock_input   /stock_output
