
1.Starting the docker-compose.yml before starting the container (docker-compose can help you to start up the container quickly)

2.Use docker-compose up -d to start the container

`docker-compose up -d`{{execute}}

3.Check that the container is running 

`docker ps -a`{{execute}}

4.Check that the logs of the container.In this case , container name is wp01 and mysql 01 . By using the command below and add the container name which you want to see the log.

`docker logs`{{copy}} 

5.You can shutdown the compose file by the command below

`docker-compose down -v`{{execute}}

Quick test
>>Q1: Docker-compose file can help install the application quickly ?<<
(*) Correct
( ) Incorrect



