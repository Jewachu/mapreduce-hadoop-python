#### Introduction
Using the mapreduce framework to score sentiments
#### Tools
This example requires that one has a basic understanding of hadoop and mapreduce framework
* hadoop
* python


This folder contains the map and reducer code for our mapreduce job
some text files have also been included for the mapreduce job.
you can use the following commands  for running this job on your hadoop file system

`hadoop namenode -format` to format namenode

`start-all`  to start hadoop daemons
`hadoop fs -mkdir /input` create an input directory
`hadoop fs -put  opt/example.txt /input` to put  a text file for mapreduce into the input directory
`hadoop jar opt/hadoop-streaming-2.*.*.jar -file opt/mapper.py -mapper.py "python mapper.py" -file opt/reducer.py -reducer "python reducer.py" -input /input/example.txt -output sentimentscore`

you must explicitly declare mapper and reducer files together with the input file and desired output name eg. sentimentscore
hadoop-streaming.jar is used for running mapreduce tasks that are not written in java

`hadoop fs -cat /user/opt/sentimentscore/part-r-00000` use this command to view your output

Also included are negative and positive words for use in scoring the sentiments

