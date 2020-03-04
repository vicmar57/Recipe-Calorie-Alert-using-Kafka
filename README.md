# Recipe-Calorie-Alert-using-Kafka

Building a system with Kafka, that parses recipes from an online API and alerts the user of recipes that exceed a calorie threshold.
the system uses microservices written in python, using Kafka-python.

Pipeline illustration:
![Alt text](calorie_alert_pipeline_Kafka.png?raw=true "Pipeline illustration")

## Installation

Kafka-python is needed to get the Python Kafka API (pip install Kafka-python)

## Usage

1. start zookeeper (on Windows, run ".\bin\windows\zookeeper-server-start.bat config/zookeeper.properties" in the kafka directory)
2. start Kafka server (on Windows, run ".\bin\windows\kafka-server-start.bat config/server.properties" in the kafka directory)
3. run producer-raw-recipies.py to get recipes from https://www.allrecipes.com and write them to the 'raw_recipes' topic in kafka
4. run producer_consumer_parse_recipes.py to get the raw recipes and parse them by (title, description, ingrediants, calorie-count, publisher) and write them to the 'parsed_recipes' topic in kafka  
5. run consumer-notification.py to get parsed recipes from kafka and alert the user which recipe has a calorie-count, greater than "calories_threshold"

## Credits

credit to Adnan Siddiqi for his tutorial on using python microservices communicating with Kafka!!
( https://towardsdatascience.com/getting-started-with-apache-kafka-in-python-604b3250aa05 )
