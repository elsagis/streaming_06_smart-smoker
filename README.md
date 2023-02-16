# Streaming_05_smart_smoker

Author: Elsa Ghirmazion
Date: February 7, 2023 Class: Streaming Data Assignment: Module 05

This program uses producers and task queues (RabbitMQ). It reads data from the smoker-temps.csv file for smart smokers.

Creating a producer, using 3 task_queues, and 3 callbacks.

#Instructions on how to run the program
## Before You Begin

1. Fork this starter repo into your GitHub.
1. Clone your repo down to your machine.
1. View / Command Palette - then Python: Select Interpreter
1. Select your conda environment.
1. Execute the Producer
1. Run bbq_producer.py (say y to monitor RabbitMQ queues)

## The Problem / Challenge To Solve
Please read about the Smart Smoker system here: Smart Smoker
Access the smoker data file here Download smoker data file here.
We want to stream information from a smart smoker. Read one value every half minute. (sleep_secs = 30)

smoker-temps.csv has 4 columns:

[0] Time = Date-time stamp for the sensor reading
[1] Channel1 = Smoker Temp --> send to message queue "01-smoker"
[2] Channe2 = Food A Temp --> send to message queue "02-food-A"
[3] Channe3 = Food B Temp --> send to message queue "02-food-B"

## Assignment Details
Using a Barbeque Smoker
When running a barbeque smoker, we monitor the temperatures of the smoker and the food to ensure everything turns out tasty. Over long cooks, the following events can happen:

The smoker temperature can suddenly decline.
The food temperature doesn't change. At some point, the food will hit a temperature where moisture evaporates. It will stay close to this temperature for an extended period of time while the moisture evaporates (much like humans sweat to regulate temperature). We say the temperature has stalled.

Sensors
We have temperature sensors track temperatures and record them to generate a history of both (a) the smoker and (b) the food over time. These readings are an example of time-series data, and are considered streaming data or data in motion.

Streaming Data
Our thermometer records three temperatures every thirty seconds (two readings every minute). The three temperatures are:
the temperature of the smoker itself. the temperature of the first of two foods, Food A. the temperature for the second of two foods, Food B.

Significant Events
We want know if:
The smoker temperature decreases by more than 15 degrees F in 2.5 minutes (smoker alert!) Any food temperature changes less than 1 degree F in 10 minutes (food stall!)

Smart System
We will use Python to:
Simulate a streaming series of temperature readings from our smart smoker and two foods. Create a producer to send these temperature readings to RabbitMQ. Create three consumer processes, each one monitoring one of the temperature streams. Perform calculations to determine if a significant event has occurred.

Optional: Alert Notifications
Optionally, we can have our consumers send us an email or a text when a significant event occurs. You'll need some way to send outgoing emails. I use my main Gmail account - other options are possible.
## Required Approach
Use your Module 4 projects (Version 2 and Version 3) as examples.
Remember: No prior coding experience is required to take this course. Rely heavily on the working examples from earlier modules.
The more similar your code looks to the examples - the more credit earned.
Vastly different approaches can be expected to earn less credit not more.
This project should clearly build on skills and code we've already mastered. If not, let me know and more help will be provided.
The primary difference should be going from 1 to 3 queue_names and from 1 to 3 callbacks.
Part of the challenge is to implement analytics using the tools and approach provided (don't significantly refactor the codebase during your first week of work!)
AFTER earning credit for the assignment, THEN create and share additional custom projects.

Screenshot
![A5_Streaming Smart Smoker](https://user-images.githubusercontent.com/105325747/218296338-00384250-7ec5-40af-bd5b-99a73e2c0e52.png)
![bbq_producer-streaming](https://user-images.githubusercontent.com/105325747/218296366-23344705-f831-47a0-a4c9-a7de9e950508.png)

