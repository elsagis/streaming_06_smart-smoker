# streaming_06_smart_smoker

Author: Elsa Ghirmazion
Date: February 15, 2023 Class: Streaming Data Assignment: Module 06

This program uses 1 producer, 3 task queues (RabbitMQ), 1 consumer, and 3 callbacks. It reads data from the smoker-temps.csv file for smart smokers.


Execute the Producer
Open 2 Anaconda Prompt Terminals
Run bbq_producer.py file (say y to monitor RabbitMQ queues)
Run bbq_consumer.py file
Assignment Details
Using a Barbeque Smoker
When running a barbeque smoker, we monitor the temperatures of the smoker and the food to ensure everything turns out tasty. Over long cooks, the following events can happen:

The smoker temperature can suddenly decline.
The food temperature doesn't change. At some point, the food will hit a temperature where moisture evaporates. It will stay close to this temperature for an extended period of time while the moisture evaporates (much like humans sweat to regulate temperature). We say the temperature has stalled.

Sensors
We have temperature sensors track temperatures and record them to generate a history of both (a) the smoker and (b) the food over time. These readings are an example of time-series data, and are considered streaming data or data in motion.

Streaming Data
Our thermometer records three temperatures every thirty seconds (two readings every minute). The three temperatures are:

the temperature of the smoker itself.
the temperature of the first of two foods, Food A.
the temperature for the second of two foods, Food B.
Significant Events
Condition to monitor/to know if:

If smoker temp decreases by 15 F or more in 2.5 min (or 5 readings) --> smoker alert! If food temp change in temp is 1 F or less in 10 min (or 20 readings) --> food stall alert!

Smart Systeme and share additional custom projects.
use Python to:

Simulate a streaming series of temperature readings from our smart smoker and two foods. Create a producer to send these temperature readings to RabbitMQ. Create three consumer processes, each one monitoring one of the temperature streams. Perform calculations to determine if a significant event has occurred
Windowing
For more on windowing, read https://softwaremill.com/windowing-in-big-data-streams-spark-flink-kafka-akka/Links to an external site. Smoker time window = 2.5 mins Food time window = 10 mins How many temperature readings are in the smoker time window? At one reading every 1/2 minute, the smoker deque max length is 5 (2.5 min * 1 reading/0.5 min) How many temperature readings are in the food time window? At one reading every 1/2 minute, the food deque max length is 20 (10 min * 1 reading/0.5 min)

Deque
For more abut deques, read https://docs.python.org/3/library/collections.html#collections.deque Links to an external site.(only the description of the deque class) We want to create a deque of limited size (to hold just the last n readings) - it'll act like a continuous queue The deque will hold only the number of readings we need for the time window of interest.

Code example: from collections import deque smoker_deque = deque(maxlen=5) # limited to 5 items (the 5 most recent readings)

Screenshot
![Consumer-A-B](https://user-images.githubusercontent.com/105325747/219844873-0d2890fa-58ee-4ad2-804b-ed07cd703b97.png)
![Producer_RabbitMq](https://user-images.githubusercontent.com/105325747/220522544-a54a8dda-16b2-496f-bd5b-d09814262fae.png)
![Producer_rabitmq2](https://user-images.githubusercontent.com/105325747/220522864-58923d57-08c2-44c0-8554-2aa54b3930e1.png)





