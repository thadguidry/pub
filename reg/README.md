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

| Resource              | Resource ID   | Operations |
|:--------------------------------|:---:|:----------:|
|    Digital Input State					| 5500|           R|
|    Digital Input Counter				| 5501|           R|
|    Digital Input Polarity				| 5502|         R,W|
|    Digital Input Debounce				| 5503|         R,W|
|    Digital Input Edge Selection	| 5504|         R,W|
|    Digital Input Counter Reset	| 5505|           E|
|    Current Time 	              | 5506|         R,W|
|    Fractional Time  	          | 5507|         R,W|
|    Min X Value	                | 5508|           R|
|    Max X Value	                | 5509|           R|
|    Min Y Value 	                | 5510|           R|
|    Max Y Value	                | 5511|           R|
|    Min Z Value 	                | 5512|           R|
|    Max Z Value                	| 5513|           R|
|    Latitude	                    | 5514|           R|
|    Longitude 	                  | 5515|           R|
|    Uncertainty 	                | 5516|           R|
|    Velocity 	                  | 5517|           R|
|    Timestamp                    | 5518|           R|
|    Min Limit                  	| 5519|           R|
|    Max Limit 	                  | 5520|           R|
|    Delay Duration             	| 5521|         R,W|
|    Clip 	                      | 5522|         R,W|
|    Trigger 	                    | 5523|           E|
|    Duration 	                  | 5524|         R,W|
|    Minimum Off-time             | 5525|         R,W|
|    Mode                         | 5526|         R,W|
|    Text                   	    | 5527|         R,W|
|    X Coordinate 	              | 5528|         R,W|
|    Y Coordinate 	              | 5529|         R,W|
|    Clear Display                | 5530|           E|
|    Contrast                     | 5531|         R,W|
|    Increase Input State         | 5532|           R|
|    Decrease Input State         | 5533|           R|
|    Counter 	                    | 5534|         R,W|
|    Current Position             | 5536|         R,W|
|    Transition Time              | 5537|         R,W|
|    Remaining Time               | 5538|           R|
|    Up Counter                   | 5541|         R,W|
|    Down Counter 	              | 5542|         R,W|
|    Digital State 	              | 5543|           R|
|    Cumulative Time 	            | 5544|         R,W|
|    Max X Coordinate             | 5545|           R|
|    Max Y Coordinate 	          | 5546|           R|
|    Multi-state Input 	          | 5547|           R|
|    Level             	          | 5548|         R,W|
|    Digital Output State					| 5550|         R,W|
|    Digital Output Polarity			| 5551|         R,W|
|    Analog Input State					  | 5600|           R|
|    Min Measured Value           | 5601|           R|
|    Max Measured Value           | 5602|           R|
|    Min Range Value              | 5603|           R|
|    Max Range Value              | 5604|           R|
|Reset Min and Max Measured Values| 5605|           E|
|    Analog Output Current Value  | 5650|         R,W|  
|    Sensor Value	                | 5700|           R|
|    Sensor Units                 | 5701|           R|
|    X Value                      | 5702|           R|
|    Y Value                      | 5703|           R|
|    Z Value                      | 5704|           R|
|    Compass Direction            | 5705|           R|
|    Colour                       | 5706|         R,W|
|    Application Type	            | 5750|         R,W|
|    Sensor Type	                | 5751|           R|
|    Busy to Clear delay          | 5903|         R,W|
|    Clear to Busy delay          | 5904|         R,W|
|    Instantaneous active power   | 5800|           R|
|    Min Measured active power    | 5801|           R|
|    Max Measured active power    | 5802|           R|
|    Min Range active power       | 5803|           R|
|    Max Range active power       | 5804|           R|
|    Cumulative active power      | 5805|           R|
|    Active Power Calibration     | 5806|           W|
|    Instantaneous reactive power | 5810|           R|
|    Min Measured reactive power  | 5811|           R|
|    Max Measured reactive power  | 5812|           R|
|    Min Range reactive power     | 5813|           R|
|    Max Range reactive power     | 5814|           R|
|    Cumulative reactive power    | 5815|           R|
|    Reactive Power Calibration   | 5816|           W|
|    Power Factor                 | 5820|           R|
|    Current Calibration          | 5821|         R,W|
|    Reset Cumulative energy      | 5822|           E|
|    Event Identifier             | 5823|         R,W|
|    Start Time                   | 5824|         R,W|
|    Duration In Min              | 5825|         R,W|
|    Criticality Level            | 5826|         R,W|
|    Avg Load Adj Pct             | 5827|         R,W|
|    Duty Cycle                   | 5828|         R,W|
|    Increase Input State         | 5532|           R|
|    Decrease Input State         | 5533|           R|
|    On/Off                       | 5850|         R,W|
|    Dimmer                       | 5851|         R,W|
|    On Time                      | 5852|         R,W|
|    Muti-state Output            | 5853|         R,W|
|    Off Time                     | 5854|         R,W|
|    Set Point Value              | 5900|         R,W|
|    Busy to Clear delay          | 5903|         R,W|
|    Clear to Busy delay          | 5904|         R,W|

NB: Please use the [issue tracker](https://github.com/IPSO-Alliance/pub/issues) if you find any mistakes on the content.
* Join the room here: [![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/IPSO-Alliance)
