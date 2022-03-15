## Writeup

---

**System-Integration-Project**
This project aims to build a scalable autonomous architecture by utilizing ROS. The architecture consists of 3 subsystems and 6 ros nodes as shown in below picture. I followed the walkthrough videos for completing all necessary nodes.
![image](https://user-images.githubusercontent.com/22918386/158345416-ade0a1a9-1a21-45a7-ad7a-db2f0eeef91d.png)


### Waypoint Updater Node 
* This node takes in base waypoints and traffic light detection info. Then it publishes final waypoints to Waypoint Follower node based on traffic light color. If the color is red, the vehicle should stop in front of the stopline, otherwise it will just travel as normal. 


### DBW Node
* This node takes in twist command from Waypoint Follower node and convert these commands to brake, steer and throttle commands.
* PID controller is used to generate control output to simulator.
* Lowpass filter is used to filter out noise

###Traffic Light Detection Node
* This node takes in traffic light color and current position.
* In this implementation, traffic light classifier is not implemented but traffic light state info is directly used instead. A classifier can be integrated in the design for future improvement
* Current position and traffic light position information is processed so that the closest traffic light waypoint index is published if it is within vehicles lookahead range.

### Reflection
* A comprehensive system architecture is required before implementation, otherwise it would be chaotic to integrate different subsytems and hard to debug.
* Currently only basic functions are implemented. More improvement can be done in the future, such as:
Tune PID parameters for smoother control,
Integrate a traffic light classifier,
Smoothen the deceleration process before traffic light stopline.
