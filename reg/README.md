[![Build Status](https://travis-ci.org/IPSO-Alliance/pub.svg?branch=master)](https://travis-ci.org/IPSO-Alliance/pub)

### If you are NOT familiar with IPSO Objects you should probably check the [IPSO README](https://github.com/IPSO-Alliance/pub/tree/master/README.md)

# Smart Objects

IPSO Smart Object Guidelines provide a common design pattern, an object model, that can effectively use the IETF CoAP protocol to provide high level interoperability between Smart Object devices and connected software applications on other devices and services.

This object set is intended to be used as a starting place from which to build more as needed Some of the objects are generic in nature, such as voltage, altitude or percentage, while others are more specialized like the Color Object or the Gyrometer Object. Actuators and Controllers are defined such as timer or buzzer and Joystick and Level. All of these objects were found to be necessary on a variety of use case domains.


| Object 				| Object ID   |
|:----------------------|:-----------:|
|    Digital 					| 3200|
|    Digital Output  			| 3201|
|    Analogue Input  			| 3202|
|    Analogue Output 			| 3203|
|    Generic Sensor  			| 3300|
|    Illuminance Sensor 		| 3301|
|    Presence sensor 			| 3302|
|    Temperature Sensor 		| 3303|
|    Humidity Sensor 			| 3304|
|    Power Measurement 			| 3305|
|    Actuation 					| 3306|
|    Set Point 					| 3308|
|    Load Control 				| 3310|
|    Light Control 				| 3311|
|    Power Control 				| 3312|
|    Accelerometer 				| 3313|
|    Magnetometer 				| 3314|
|    Barometer  	   		 	| 3315|
|    Voltage					| 3316|
|    Current					| 3317|
|    Frequency					| 3318|
|    Depth						| 3319|
|    Percentage					| 3320|
|    Altitude					| 3321|
|    Load						| 3322|
|    Pressure					| 3323|
|    Loudness					| 3324|
|    Concentration 				| 3325|
|    Acidity					| 3326|
|    Conductivity				| 3327|
|    Power						| 3328|
|    Power Factor				| 3329|
|    Rate						| 3346|
|    Distance					| 3330|
|    Energy						| 3331|
|    Direction					| 3332|
|    Time						| 3333|
|    Gyrometer					| 3334|
|    Color 						| 3335|
|    GPS Location 				| 3336|
|    Positioner 				| 3337|
|    Buzzer						| 3338|
|    Audio Clip					| 3339|
|    Timer						| 3340|
|    Addressable Text Display	| 3341|
|    On/Off Switch				| 3342|
|    Push Button				| 3347|
|    Level Controllers			| 3343|
|    Up/Down Control			| 3344|
|    Multi-state Selector		| 3348|
|    Multiple Axis Joystick		| 3345|


Below there is the set of Resources that can be used as building blocks for your Objects.

| Resource              | Resource ID   |
|:--------------------------------|:---:|
|    Digital Input State					| 5500|
|    Digital Input Counter				| 5501|
|    Digital Input Polarity				| 5502|
|    Digital Input Debounce				| 5503|
|    Digital Input Edge Selection	| 5504|
|    Digital Input Counter Reset	| 5505|
|    Current Time 	              | 5506|
|    Fractional Time  	          | 5507|
|    Min X Value	                | 5508|
|    Max X Value	                | 5509|
|    Min Y Value 	                | 5510|
|    Max Y Value	                | 5511|
|    Min Z Value 	                | 5512|
|    Max Z Value                	| 5513|
|    Latitude	                    | 5514|
|    Longitude 	                  | 5515|
|    Uncertainty 	                | 5516|
|    Velocity 	                  | 5517|
|    Timestamp                    | 5518|
|    Min Limit                  	| 5519|
|    Max Limit 	                  | 5520|
|    Delay Duration             	| 5521|
|    Clip 	                      | 5522|
|    Trigger 	                    | 5523|
|    Duration 	                  | 5524|
|    Minimum Off-time             | 5525|
|    Mode                         | 5526|
|    Text                   	    | 5527|
|    X Coordinate 	              | 5528|
|    Y Coordinate 	              | 5529|
|    Clear Display                | 5530|
|    Contrast                     | 5531|
|    Counter 	                    | 5534|
|    Current Position             | 5536|
|    Transition Time              | 5537|
|    Remaining Time               | 5538|
|    Up Counter                   | 5541|
|    Down Counter 	              | 5542|
|    Digital State 	              | 5543|
|    Cumulative Time 	            | 5544|
|    Max X Coordinate             | 5545|
|    Max Y Coordinate 	          | 5546|
|    Multi-state Input 	          | 5547|
|    Digital Output State					| 5550|
|    Digital Output Polarity			| 5551|
|    Analog Input State					  | 5600|
|    Min Measured Value           | 5601|
|    Max Measured Value           | 5602|
|    Min Range Value              | 5603|
|    Max Range Value              | 5604|
|Reset Min and Max Measured Values| 5605|
|    Sensor Value	                | 5700|
|    Sensor Units                 | 5701|
|    X Value                      | 5702|
|    Y Value                      | 5703|
|    Z Value                      | 5704|
|    Compass Direction            | 5705|
|    Colour                       | 5706|
|    Application Type	            | 5750|
|    Sensor Type	                | 5751|
|    Busy to Clear delay          | 5903|
|    Clear to Busy delay          | 5904|
|    Instantaneous active power   | 5800|
|    Min Measured active power    | 5801|
|    Max Measured active power    | 5802|
|    Min Range active power       | 5803|
|    Max Range active power       | 5804|
|    Cumulative active power      | 5805|
|    Active Power Calibration     | 5806|
|    Instantaneous reactive power | 5810|
|    Min Measured reactive power  | 5811|
|    Max Measured reactive power  | 5812|
|    Min Range reactive power     | 5813|
|    Max Range reactive power     | 5814|
|    Cumulative reactive power    | 5815|
|    Reactive Power Calibration   | 5816|
|    Power Factor                 | 5820|
|    Current Calibration          | 5821|
|    Reset Cumulative energy      | 5822|
|    Event Identifier             | 5823|
|    Start Time                   | 5824|
|    Duration In Min              | 5825|
|    Criticality Level            | 5826|
|    Avg Load Adj Pct             | 5827|
|    Duty Cycle                   | 5828|
|    Increase Input State         | 5532|
|    Decrease Input State         | 5533|
|    On/Off                       | 5850|
|    Dimmer                       | 5851|
|    On Time                      | 5852|
|    Muti-state Output            | 5853|
|    Off Time                     | 5854|
|    Set Point Value              | 5900|


NB: Please use the [issue tracker](https://github.com/IPSO-Alliance/pub/issues) if you find any mistakes on the content.
* Join the room here: [![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/IPSO-Alliance)
