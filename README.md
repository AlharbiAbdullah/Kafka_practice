## Kafka Topics
- Topics are the "stream of data", for example:
	* logs
	* twitter hashtags 
	* CRUD database 
- Kafka cluster can have many topics 
- Easy way to think about kafka topic is to assume it's a database table, but without constraints.
- A topic is identified by it's name. 
- Kafka topic support any type of messaging format. 
- The sequance of messages is called "data stream"
- We can't query topics, instead:
	* Kafka producer > send data 
	* Kafka Consumer > read data
- Each Kafka topic split into partitions
	* Messages with partitions are order by unique ID(The ID called "Kafka Partition offset")
- Kafka topics are immuatable: 
	* Once the once the data is written in partition, it can't be changed
- We can't delete , update within kafka

----------------------------------------------

## Producers 
- Producers wtire to kafka topics(partitions). 
- Producers knows which partiotion it's writing to. 
- In case of failure, producers know how to recover. 
- We can think of producers like "Load Balancer" 
- Producers can send a key(optional), it can be string,number, binery
	* we can manage messages with keys for example: 
		* if key = null , data is sent round robin (partition1 , 2 ,3,...)
		* if key != null , all the data has the same key will sent into the same partition.

-------------------------------------------------

## Consumers 
- Consumers read from Kafka topics -partitions- (pull model).
- Consumers automaticly knows which broker to read from. 
- In case of failure, Consumers knows how recover. 
- Consumers reads data from low to high offset: 
	* meaning it read from 0-n in order within each parition. 

------------------------------------------------

## Serializer/Deserilazer 
- Kafka accepts data from producers as bytes. 
- We serialize the message when we sent data, and decerilize when the consumers read the data
- Producer > Serlixzer > Kafka broker > Decerializer > consumer 

----------------------------------

## Consumer Groups 
- The Idea here is to have consumer groups read diffrent thins
	* lets say there the producser has data about employees and products. 
	* We create two consumer groups, one to read emplyees data, and the second to read products data. 
	
