# PTR_LABORATORIES

This repository contains the code source of the laboratory work made by me for PTR subject for the Software Engineering.

## Diagrams.

## Message Flow.

First step of message flow is the subscription of Producer and Consumer to the Message Broker. This happens by Producer or Consumer sending a TCP message making a subscription to the host and port - localhost:8080. The MainSupervisor spawns a MainSupervisorMessageHandler that saves the producer/consumer into a local storage (File), generates a new random port and sends it to the Consumer/Sponsor. Using this port and Gateway actor is created that mentoins the connection and get messages from Producers.

Using the new port Procer creates a new actor that sends messages to the Gateway. Fore every message send a MessageHandler is created that getts the topic of the message, finds the Consumers subscribed to these topics and creates a Distributor for every Consumer which sends the message to them.

![/assets/Message Flow.png](https://github.com/ScienceKot/PTR_LABORATORIES/blob/main/assets/Message%20Flow.png)

## Spawn Tree

MainSuperviser for every subscribe message creates a MainSupervisorMessageHandler, which after saving the producer/consumer data, creates a Gateway actor. This one creates a MessageHandler for every message, wich after finding the ports to forward the message to the consumer subscribed to the topics of the message.
![MessageFlow](/assets/Spawn Tree.png)](https://github.com/ScienceKot/PTR_LABORATORIES/blob/main/assets/Spawn%20Tree.png)
