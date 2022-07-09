# Detecting Overlapping Communities in ISEBEL

This repository implements the BigClam alorithm on Apache Spark used for detecting overlapping communities in ISEBEL.

## Prerequisites: Apache Spark. 
### If you already have Apache Spark Installed and configured, skip this step
#### step 1
- [ a.] Make sure you have jupyter notebook installed and working properly.
#### step 2
- [ a.] Got to Apache Spark website [link](https://spark.apache.org/downloads.html) , download Apache Spark on your system.

- [ b.] If you don't have java installed on your machine, follow this [link](http://tecadmin.net/install-oracle-java-8-jdk-8-ubuntu-via-ppa/) , download and install java.

- [ c.] To install Apache spark on linux, go to your home directory (with command)
```
cd ~
```
- [ d.] Unzip the Apache spark folder you downloaded in [a.] above in your home directory using the following command, replace spark-2.0.0-bin-hadoop2.7.tgz with your own version
```
tar -zxvf spark-2.0.0-bin-hadoop2.7.tgz
```
- [ e.] Use the following command to see that you have a .bashrc file
```
nano .bashrc
```
- [ f.] Don’t remove anything in your .bashrc file. Add the following to the bottom of your .bashrc file
```
function snotebook () {
    #Spark path (based on your computer)
    SPARK_PATH=~/spark-2.0.0-bin-hadoop2.7

    export PYSPARK_DRIVER_PYTHON="jupyter"
    export PYSPARK_DRIVER_PYTHON_OPTS="notebook"

    # For python 3 users, you have to add the line below or you will get an error 
    #export PYSPARK_PYTHON=python3

    $SPARK_PATH/bin/pyspark --master local[2]
}
```
- [ g.] Save and exit out of your .bashrc file. Either close the terminal and open a new one or in your terminal type:
```
source .bashrc
```
#### step 3 : Also install Spark GraphFrames
- [ a.] download the right jar file version of graphframes that correspond to your Apache spark version from [link](https://spark-packages.org/package/graphframes/graphframes)
- [ b.] Extract the jar file and copy it to your spark $SPARK_HOME/jars/ directory on your machine.

# Clone this repo
- [ a.] Clone this repo to your jupter notebook directory

#### step next 1 : Install python packages
- [ a.] install the python_dependencies.sh file by running the command :
```
bash python_dependencies.sh 
```
on the terminal.

#### step next 2: Start Spark with jupter
- [ a.] On the terminal run the command :
```
snotebook
```
to start jupter notebook with Spark configuration runing. 

# How to estimate K-Value
- [ a.] Randomly assign k = 8, 50, 100 . . . in the variable dimensions: int = K, in the BigClamISEBEL
- [ b.] Using some node property (You can already find this specified as `K = create_graph_frames().vertices.select('type').distinct().count()` in the `BigClamISEBEL.ipynb` file)
- [ c.] Use the output generated from Girven-newman algorithm in spark - GN_algorithm_spark.ipynb (i.e.; the last output `print(countList(user_communities))` )

##### Read Chapter 5 and 6 in the documentation for better understanding 