# Wordcount hadoop streaming mapreduce
## Usage
### Run the mapper
cat word_input | python WordCountMapper.py
### Run the reducer
cat word_input | python WordCountMapper.py | sort -k1,1 | python wordcountreducer.py
### Running the Python Code on Hadoop 
Before we run the MapReduce  on Hadoop, copy local data (word_input) to HDFS

hadoop fs -put /Tp_Python_hadoop_streaming/word_input  /Tp_Python_Hadoop/word_input
#### Run the MapReduce job
hadoop jar /usr/lib/hadoop-0.20-mapreduce/contrib/streaming/hadoop-streaming-2.6.0-mr1-cdh5.7.0.jar -file /Tp_Python_hadoop_streaming/WordCountMapper.py /Tp_Python_hadoop_streaming/wordcountreducer.py -mapper "python WordcountMapper.py" -reducer "python wordcountreducer.py" -input /Tp_Python_Hadoop/word_input -output /Tp_Python_Hadoop/output_word

