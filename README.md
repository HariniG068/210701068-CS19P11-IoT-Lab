HARDWARE SPECIFICATIONS   
  
NodeMCU   	        :   	ESP32 (38 Pins) 
IR Sensor   	      :   	Proximity Sensor 
Rain Drop Sensor   	:     LM393 (Volt-comp)
Servo Motor         :     2.2KW
Power Supply        :     5V DC

SOFTWARE SPECIFICATIONS   
	   
The software requirements document is the specifications of the system. 
It should include both a definition and a specification of requirements. 
It is a set of what the system should rather be doing than focus on how it should be done. 
The software requirements provide a basis for creating the software requirements specification.
 It is useful in estimating the cost, planning team activities, performing tasks, tracking the team, and 
tracking the team’s progress throughout the development activity.


CODE EXPLANATION 

This code is designed to connect an ESP8266 microcontroller to a WiFi network using specified credentials and set up an MQTT client to communicate with Adafruit IO.
It includes libraries for WiFi, MQTT, and servo control. The setup() function initializes the serial communication, connects to the WiFi network, prints the IP address, 
and sets up the servo motor on GPIO2 (D6) to an initial position of 90 degrees. It also configures GPIO5 (D5) and GPIO4 (D2) as input pins with internal pull-up resistors.
These pins are used to read button states to control the servo motor's movement.
In the loop() function, the code first ensures that the MQTT connection is active by calling MQTT_connect(). 
It then checks the states of the buttons connected to D5 and D2. If both buttons are pressed, the servo moves from 90 to 180 degrees, publishes the message "wet" to Adafruit IO,
and returns to 90 degrees. If only D5 is pressed, the servo moves from 90 to 0 degrees, publishes the message "dry" to Adafruit IO, and returns to 90 degrees. The MQTT_connect()
function handles reconnections to the MQTT server if the connection is lost, ensuring the ESP8266 maintains a reliable connection to Adafruit IO for publishing data.
