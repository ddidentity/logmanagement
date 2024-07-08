# logmanagement
This is a mini project for log management.
There are two directories under the project-

	application
	loginfra

## application
There is a springboot application that uses log4j2 to generate logs. 
A console and Kafka appender is configured to send logs to console and Kafka topic.

`./mvnw spring-boot:run` 

above command should start the application and you can use below curl command to generate logs.

`curl http://localhost:8888/log`

Note that you might need to install maven wrapper in the system you are running the application.

Link: [maven-wrapper](https://www.baeldung.com/maven-wrapper)

## loginfra

There is a docker-compose file in it that spawns container for Kafka, Elasticsearch, Logstash and Kibana.

`docker-compose up -d `    
should bring up all the containers.

You can visualise the logs using kibana at `http://localhost:5601/`

For the very first time you have to add Index pattern "logs*"

## How it works?
Application generates log that a kafka-appender send the logs to the Kafka Topic. 

I have configured Logstash to receive the log from Kafka topic and send those to Elasticsearch.

Elastic search does storage and indexing.

Finally with kibana we can visualise the logs.
