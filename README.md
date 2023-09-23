# House Assistant

## Description


This project simulates an Home intelligent environment. In this environment, there are Sensors (that collect data from the surroundings) and Actuators (that can take actions to modify the environment in some way). For instance, in a smart residential environment, there can be temperature sensors that periodically collect room temperature, and devices like air conditioners and heaters that act as actuators and can modify the room's temperature.

All these sensors and actuators are managed by a server called Home Assistant. This equipment interacts with the sensors and actuators, collecting information and occasionally taking actions in the environment.

Communication between the sensors and the Home Assistant occurs via RabbitMQ, using the Publisher/Subscriber paradigm. The Home Assistant acts as a Subscriber, and each sensor acts as a Publisher. Each sensor should periodically publish the data it observes to its own RabbitMQ queue, which will notify the Home Assistant of the new message.

Communication between the Home Assistant and the actuators occurs via gRPC, using the Client/Server paradigm. The Home Assistant acts as a Client, and each actuator acts as a Server. For example, consider a smart lamp with two possible actions: turn on or turn off. The lamp should offer a remote invocation interface with two methods: `turnOnLamp()` and `turnOffLamp()`. This way, the Home Assistant can interact with the environment by remotely invoking these methods. For example, to turn on a specific lamp, it should remotely invoke the `turnOnLamp()` method via gRPC.

In this case, the protocol used before the connection between the sensors and the gateway is UDP to prioritize speed and data efficiency; after the connection is established, the communication changes to TCP to guarantee the correct exchange of information.

# Diagrams :

![Gateway_Diagram](https://user-images.githubusercontent.com/52925699/154584296-e4fc2cb6-5779-4d0e-9575-42f00a636f8e.png)

![Overall Diagram](https://github.com/Lucasvitoriano25/Gateway-TCP-UDP/assets/52925699/01c16b44-ab3c-4b30-adf7-39204c6785b9)



