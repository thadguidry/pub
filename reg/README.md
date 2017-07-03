[![Build Status](https://travis-ci.org/IPSO-Alliance/pub.svg?branch=master)](https://travis-ci.org/IPSO-Alliance/pub)

### If you are NOT familiar with IPSO Objects you should probably check the [IPSO README](https://github.com/IPSO-Alliance/pub/tree/master/README.md)

# Smart Objects

IPSO Smart Object Guidelines provide a common design pattern, an object model, that can effectively use the IETF CoAP protocol to provide high level interoperability between Smart Object devices and connected software applications on other devices and services.

This object set is intended to be used as a starting place from which to build more as needed Some of the objects are generic in nature, such as voltage, altitude or percentage, while others are more specialized like the Color Object or the Gyrometer Object. Actuators and Controllers are defined such as timer or buzzer and Joystick and Level. All of these objects were found to be necessary on a variety of use case domains.


| Object 				| Object ID   |
|:----------------------|:-----------:|
|    Digital Input				| 3200|
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
|    Level Controllers			| 3343|
|    Up/Down Control			| 3344|
|    Multiple Axis Joystick		| 3345|
|    Rate						| 3346|
|    Push Button				| 3347|
|    Multi-state Selector		| 3348|
|    Bitmap                     | 3349|
|    Stopwatch                  | 3350|



Below there is the set of Resources that can be used as building blocks for your Objects.

| Resource              | Resource ID   | Operations |Type   |
|:--------------------------------|:---:|:----------:|:-----:|
|    Digital Input State					| 5500|           R|Boolean|
|    Digital Input Counter				| 5501|           R|Integer|
|    Digital Input Polarity				| 5502|         R,W|Boolean|
|    Digital Input Debounce				| 5503|         R,W|Integer|
|    Digital Input Edge Selection	| 5504|         R,W|Integer|
|    Digital Input Counter Reset	| 5505|           E| Opaque|
|    Current Time 	              | 5506|         R,W|   Time|
|    Fractional Time  	          | 5507|         R,W|  Float|
|    Min X Value	                | 5508|           R|  Float|
|    Max X Value	                | 5509|           R|  Float|
|    Min Y Value 	                | 5510|           R|  Float|
|    Max Y Value	                | 5511|           R|  Float|
|    Min Z Value 	                | 5512|           R|  Float|
|    Max Z Value                	| 5513|           R|  Float|
|    Latitude	                    | 5514|           R| String|
|    Longitude 	                  | 5515|           R| String|
|    Uncertainty 	                | 5516|           R| String|
|    Velocity 	                  | 5517|           R| Opaque|
|    Timestamp                    | 5518|           R|   Time|
|    Min Limit                  	| 5519|           R|  Float|
|    Max Limit 	                  | 5520|           R|  Float|
|    Delay Duration             	| 5521|         R,W|  Float|
|    Clip 	                      | 5522|         R,W| Opaque|
|    Trigger 	                    | 5523|           E| Opaque|
|    Duration 	                  | 5524|         R,W|  Float|
|    Minimum Off-time             | 5525|         R,W|  Float|
|    Mode                         | 5526|         R,W|Integer|
|    Text                   	    | 5527|         R,W| String|
|    X Coordinate 	              | 5528|         R,W|Integer|
|    Y Coordinate 	              | 5529|         R,W|Integer|
|    Clear Display                | 5530|           E|       |
|    Contrast                     | 5531|         R,W|  Float|
|    Increase Input State         | 5532|           R|Boolean|
|    Decrease Input State         | 5533|           R|Boolean|
|    Counter 	                    | 5534|         R,W|Integer|
|    Current Position             | 5536|         R,W|  Float|
|    Transition Time              | 5537|         R,W|  Float|
|    Remaining Time               | 5538|           R|  Float|
|    Up Counter                   | 5541|         R,W|Integer|
|    Down Counter 	              | 5542|         R,W|Integer|
|    Digital State 	              | 5543|           R|Boolean|
|    Cumulative Time 	            | 5544|         R,W|  Float|
|    Max X Coordinate             | 5545|           R|Integer|
|    Max Y Coordinate 	          | 5546|           R|Integer|
|    Multi-state Input 	          | 5547|           R|Integer|
|    Level             	          | 5548|         R,W|  Float|
|    Digital Output State					| 5550|         R,W|Boolean|
|    Digital Output Polarity			| 5551|         R,W|Boolean|
|    Analog Input State					  | 5600|           R|  Float|
|    Min Measured Value           | 5601|           R|  Float|
|    Max Measured Value           | 5602|           R|  Float|
|    Min Range Value              | 5603|           R|  Float|
|    Max Range Value              | 5604|           R|  Float|
|Reset Min and Max Measured Values| 5605|           E| Opaque|
|    Analog Output Current Value  | 5650|         R,W|  Float|  
|    Sensor Value	                | 5700|           R|  Float|
|    Sensor Units                 | 5701|           R| String|
|    X Value                      | 5702|           R|  Float|
|    Y Value                      | 5703|           R|  Float|
|    Z Value                      | 5704|           R|  Float|
|    Compass Direction            | 5705|           R|  Float|
|    Colour                       | 5706|         R,W| String|
|    Application Type	            | 5750|         R,W| String|
|    Sensor Type	                | 5751|           R| String|
|    Instantaneous active power   | 5800|           R|  Float|
|    Min Measured active power    | 5801|           R|  Float|
|    Max Measured active power    | 5802|           R|  Float|
|    Min Range active power       | 5803|           R|  Float|
|    Max Range active power       | 5804|           R|  Float|
|    Cumulative active power      | 5805|           R|  Float|
|    Active Power Calibration     | 5806|           W|  Float|
|    Instantaneous reactive power | 5810|           R|  Float|
|    Min Measured reactive power  | 5811|           R|  Float|
|    Max Measured reactive power  | 5812|           R|  Float|
|    Min Range reactive power     | 5813|           R|  Float|
|    Max Range reactive power     | 5814|           R|  Float|
|    Cumulative reactive power    | 5815|           R|  Float|
|    Reactive Power Calibration   | 5816|           W|  Float|
|    Power Factor                 | 5820|           R|  Float|
|    Current Calibration          | 5821|         R,W|  Float|
|    Reset Cumulative energy      | 5822|           E| Opaque|
|    Event Identifier             | 5823|         R,W| String|
|    Start Time                   | 5824|         R,W|  Float|
|    Duration In Min              | 5825|         R,W|  Float|
|    Criticality Level            | 5826|         R,W|Integer|
|    Avg Load Adj Pct             | 5827|         R,W| String|
|    Duty Cycle                   | 5828|         R,W|Integer|
|    On/Off                       | 5850|         R,W|Boolean|
|    Dimmer                       | 5851|         R,W|Integer|
|    On Time                      | 5852|         R,W|Integer|
|    Muti-state Output            | 5853|         R,W| String|
|    Off Time                     | 5854|         R,W|Integer|
|    Set Point Value              | 5900|         R,W|  Float|
|    Busy to Clear delay          | 5903|         R,W|Integer|
|    Clear to Busy delay          | 5904|         R,W|Integer|
|    Bitmap Input                 | 5910|           R|Integer|
|    Bitmap Input Reset           | 5911|           E| Opaque|
|    Bit Description              | 5912|         R,W| String|

NB: Please use the [issue tracker](https://github.com/IPSO-Alliance/pub/issues) if you find any mistakes on the content.
* Join the room here: [![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/IPSO-Alliance)
