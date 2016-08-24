# IP for Smart Objects

## XML Validation

[![Build Status](https://travis-ci.org/IPSO-Alliance/pub.svg?branch=master)](https://travis-ci.org/IPSO-Alliance/pub)

## Table of Contents
1. [Introduction](#Introduction)
2. [Components](#Data Model Components)
3. [Composite Objects](#Composite Objects)
4. [Example](#Example and Extended References)
5. [Starter Pack](#Smart Objects - Starter Pack)
6. [Expansion Pack](#Smart Objects - Expansion Pack)
7. [Application Specific Objects](#Smart Objects - Application Specific Objects)
8. [References](#References)

## 1. Introduction
Standards for constrained devices are rapidly consolidating and the availability of IP on constrained devices enabled these devices to easily connect to the Internet. The IETF has also created a set of specifications for such IP-enabled devices to work in a Web-like fashion. One such protocol is the Constrained Application Protocol (CoAP) [1] that provides request/response methods, ways to identify resources, discovery mechanisms, etc. similar to HTTP [2] but for use in constrained environments.

However, the use of standardized protocols does not ensure interoperability on the application layer. Therefore, there is a clear need for being able to communicate using structured data models on top of protocols like CoAP and HTTP.

IPSO Smart Objects provide a common design pattern, an object model, to provide high level interoperability between Smart Object devices and connected software applications on other devices and services. IPSO Objects are defined in such a way that they do not depend on the use of CoAP, any RESTful protocol is sufficient. Nevertheless, to develop a complete and interoperable solution the Object model is based on the Open Mobile Alliance Lightweight Specification (OMA LWM2M) [3], which is a set of management interfaces built on top of CoAP in order to enable device management operations (bootstrapping, firmware updates, error reporting, etc.). While LWM2M uses objects with fixed mandatory resources, IPSO Smart Objects use a more reusable design.

**Developers can already use the Objects at the [IPSO Registry](https://github.com/IPSO-Alliance/pub/tree/master/reg/xml)**


## 2. Data Model Components

The data model for IPSO Smart Objects consists of 5 parts:

1. Object Representation
3. Data types
4. Operations
5. Content formats

### 2.1. Object Representation

Objects and resources are implicitly mapped into the URI path hierarchy by following the OMA LWM2M object model, in which each URI path component sequentially represents the Object Type ID, the Object Instance ID and the Resource Type ID. More precisely the structure consists of three unsigned 16-bit integers separated by the character '/':

```
<object ID>/<object instance ID>/<resource ID>
```

This URI template approach follows the Web Linking [4] and the IETF CoRE Link Format [5]. Objects are typed containers, which define the semantic type of instances. Instances represent specific object types at runtime, and allow Smart Object endpoints to expose multiple sensors and actuators of a particular type. Object instances are themselves containers for resources, which are the observable properties of an object.

For example, a temperature sensor example URI would be `3303/0/5700`:

```
3300  -> Temperature Sensor
0     -> instance 0 of a Temperature Sensor
5700  -> resource having the current value or a most recent reading
```

Semantically, the object type represents a single measurement, actuation, or control point for example a temperature sensor, a light (actuator), or an on-off switch (control point).
A resource specifies a particular view or active property of an object. For example, a temperature sensor object might expose the current value (most recent reading), also the minimum and maximum possible reading, the minimum and maximum reading in an interval, and attributes like engineering units and application type.

Attributes describe the metadata configuration, settings, and state of an object or resource, and are discoverable by reading the link-format data of an object or resource. Multiple attributes may be serialized in the link-format descriptors that an object exposes. Some attributes are immutable for a given object or resource type. For example, the static read, write, and execute capability attributes are derived from a Smart Object’s definition file, while other attributes, like the LWM2M Notification Attributes, are used to dynamically configure a particular object instance or resource. Attributes are represented using the IETF CoRE Link Format (RFC 6690) or an equivalent mapping to other content formats, for example, application/json+ld.

This abstraction allows application software to use simple APIs. For complex objects, linking of an object to another object through an object link resource is allowed. This enables the recursion to be handled at the object level, using design patterns similar to web linking. An application client can consume a devices API without knowing its structure and attributes a priori.


### 2.2. Data types

There are 7 data types, same as the ones defined in OMA LWM2M [3].

1. String: A UTF-8 string, the minimum and/or maximum length of the String MAY be defined.
2. Integer: An 8, 16, 32 or 64-bit signed integer. The valid range of the value for a Resource SHOULD be defined. This data type is also used for the purpose of enumeration.
3. Float: A 32 or 64-bit floating point value. The valid range of the value for a Resource SHOULD be defined.
4. Boolean: An integer with the value 0 for False and the value 1 for True.
5. Opaque: A sequence of binary octets, the minimum and/or maximum length of the String MAY be defined.
6. Time: Unix Time. A signed integer representing the number of seconds since Jan 1st, 1970 in the UTC time zone.
7. Object Link: The object link is used to refer an Instance of a given Object. An Object link value is composed of two concatenated 16-bits unsigned integers following the Network Byte Order convention.


### 2.3. Operations
IPSO Objects and their resources have the same operations as their counterparts in the OMA LWM2M specification [3] with the same semantics.

1. Resource values: Read, Write, Execute (restricted by the Access Type field)
2. Object Instances: Create, Delete (restricted by the Multiple Instances field)
3. Objects and their instances: Read, Write
4. Attributes: Set, Discover



### 2.4. Content formats

Content formats are those specified by the OMA LWM2M specification [3]:

1. Resource values: text/plain, tlv
2. Objects: text/senml+json, application/cbor, binary/tlv
3. Attributes: link-format, link-format+json

## 3. Composite Objects

As devices increase in complexity (e.g., from a sensor to an appliance, from a switch to a complex actuator) the need to link resources to create more complex objects or ”Composite Objects” arises. Such a composite object can, for example, be constructed with a single reusable type ”generic composite object” with one ID. The resources may be of a generic reusable link type, also using a single ID, with multiple instances allowed.

For example, ’4000/0/6700/0’ where 4000 is a ”composite object” and 6700 is ”generic object link”. Composite objects offer higher granularity than one large nested object would. An observer of a device represented as a composite object could reduce bandwidth utilization by observing only the linked object instances instead of the full object. Figure 3 shows an example, performing a GET operation to the IPSO thermostat composite object ”/8300/0/7100” would retrieve an object link to ”/3300/0”.


# ![IPSO Object](https://github.com/IPSO-Alliance/pub/blob/master/linking.png)

## 4. Examples and Extended References

### 4.1 Definition documents

For practical purposes we require a format for representing the objects in an unambiguous fashion. IPSO has used XML to the XML Schema in Appendix A, either hand-written or automatically generated from other sources. In the XML version, Integers, Floats and Time values must be represented as in the above subsection. Binary (Opaque) values must be represented in Base64-encoded form. Booleans must be represented using the lower-case strings true and false. XML definition documents may reference other XML definition documents using Include [5].

### 4.2 Humidity Sensor

The following is a example of a humidity sensor that contains the sensor value, units, min and max measured values, min and max range values and a rest of those.
# ![IPSO Object](https://github.com/IPSO-Alliance/pub/blob/master/humidity_object.png)


The following is the definition document for the Humidity Object in XML.


```
<?xml version="1.0" encoding="utf-8"?>
<LWM2M>
	<Object ObjectType="MODefinition">
		<Name>Humidity</Name>
		<Description1>Description: This IPSO object should be used with a humidity sensor to report a humidity measurement.  It also provides resources for minimum/maximum measured values and the minimum/maximum range that can be measured by the humidity sensor. An example measurement unit is relative humidity as a percentage (ucum:%).</Description1>
		<ObjectID>3304</ObjectID>
		<ObjectURN>urn:oma:lwm2m:ext:3304</ObjectURN>
		<MultipleInstances>Multiple</MultipleInstances>
		<Mandatory>Optional</Mandatory>
		<Resources>
			<Item ID="5700">
				<Name>Sensor Value</Name>
				<Operations>R</Operations>
				<MultipleInstances>Single</MultipleInstances>
				<Mandatory>Mandatory</Mandatory>
				<Type>Float</Type>
				<RangeEnumeration></RangeEnumeration>
				<Units>Defined by “Units” resource.</Units>
				<Description>Last or Current Measured Value from the Sensor</Description>
			</Item>
			<Item ID="5601">
				<Name>Min Measured Value</Name>
				<Operations>R</Operations>
				<MultipleInstances>Single</MultipleInstances>
				<Mandatory>Optional</Mandatory>
				<Type>Float</Type>
				<RangeEnumeration></RangeEnumeration>
				<Units>Defined by “Units” resource.</Units>
				<Description>The minimum value measured by the sensor since power ON or reset</Description>
			</Item>
			<Item ID="5602">
				<Name>Max Measured Value</Name>
				<Operations>R</Operations>
				<MultipleInstances>Single</MultipleInstances>
				<Mandatory>Optional</Mandatory>
				<Type>Float</Type>
				<RangeEnumeration></RangeEnumeration>
				<Units>Defined by “Units” resource.</Units>
				<Description>The maximum value measured by the sensor since power ON or reset</Description>
			</Item>
			<Item ID="5603">
				<Name>Min Range Value</Name>
				<Operations>R</Operations>
				<MultipleInstances>Single</MultipleInstances>
				<Mandatory>Optional</Mandatory>
				<Type>String</Type>
				<RangeEnumeration></RangeEnumeration>
				<Units>Defined by “Units” resource.</Units>
				<Description>The minimum value that can be measured by the sensor</Description>
			</Item>
			<Item ID="5604">
				<Name>Max Range Value</Name>
				<Operations>R</Operations>
				<MultipleInstances>Single</MultipleInstances>
				<Mandatory>Optional</Mandatory>
				<Type>Float</Type>
				<RangeEnumeration></RangeEnumeration>
				<Units>Defined by “Units” resource.</Units>
				<Description>The maximum value that can be measured by the sensor</Description>
			</Item>
			<Item ID="5701">
				<Name>Sensor Units</Name>
				<Operations>R</Operations>
				<MultipleInstances>Single</MultipleInstances>
				<Mandatory>Optional</Mandatory>
				<Type>String</Type>
				<RangeEnumeration></RangeEnumeration>
				<Units></Units>
				<Description>Measurement Units Definition e.g. “Cel” for Temperature in Celsius.</Description>
			</Item>
			<Item ID="5605">
				<Name>Reset Min and Max Measured Values</Name>
				<Operations>E</Operations>
				<MultipleInstances>Single</MultipleInstances>
				<Mandatory>Optional</Mandatory>
				<Type>Opaque</Type>
				<RangeEnumeration></RangeEnumeration>
				<Units></Units>
				<Description>Reset the Min and Max Measured Values to Current Value</Description>
			</Item>
		</Resources>
		<Description2></Description2>
	</Object>
</LWM2M>
```

## 4.3. Smart Objects - Starter Pack

This first IPSO Smart Object Guideline describes 18 Smart Object types, including a temperature sensor, a light controller, an accelerometer, a presence sensor, and other common sensor and actuator types representing a variety of use case domains. It is intended as a “Starter Pack” and example of how IPSO Smart Objects can be built to address some application specific use cases.

This first object set is intended to be used as a starting place from which to build more objects and object sets, in order to address vertical application segments and new functional requirements for Smart Objects. The IPSO Alliance is committed to making it easy for people to create new objects based on their use case needs, while promoting reusable and cross-domain standards to as great an extent as is practical.


| Object 		| Object ID     |
|:----------------------|:-----:|
|    Digital 			|  3200 |
|    Digital Output  	|  3201 |
|    Analogue Input  	|  3202 |
|    Analogue Output 	|  3203 |
|    Generic Sensor  	|  3300 |
|    Illuminance Sensor |  3301 |
|    Presence sensor 	|  3302 |
|    Temperature Sensor |  3303 |
|    Humidity Sensor 	|  3304 |
|    Power Measurement 	|  3305 |
|    Actuation 			|  3306 |
|    Set Point 			|  3308 |
|    Load Control 		|  3310 |
|    Light Control 		|  3311 |
|    Power Control 		|  3312 |
|    Accelerometer 		|  3313 |
|    Magnetometer 		|  3314 |
|    Barometer  	    |  3315 |

## 4.4. Smart Objects - Expansion Pack

To complement the initial set of objects, this new IPSO Smart Object Expansion Pack was created. The Expansion Pack covers a new set of 16 Common Template sensors, 6 Special template sensors, 5 Actuators and 6 Control switch types.  

Some of the new objects are generic in nature, such as voltage, altitude or percentage, while others are more specialized like the Color Object or the Gyrometer Object. New Actuators and Controllers are defined such as timer or buzzer and Joystick and Level. All of these objects were found to be necessary on a variety of use case domains.


| Object 				| Object ID   |
|:----------------------|:-----------:|
|    Voltage					| 3316|
|    Current					| 3317|
|    Frequency					| 3318|
|    Depth						| 3319|
|    Percentage					| 3320|
|    altitude					| 3321|
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
|    Multistate Selector		| 3348|
|    Multiple Axis Joystick		| 3345|

## 4.5. Smart Objects - Application Specific Objects

Apart from the basic object sets IPSO provide Objects sets from reusing existing Resources tailored to other use cases.
Anyone can create new Objects from various Resources.


## 5. References

[1]		Z. Shelby, K. Hartke, and C. Bormann, “The Constrained Application Protocol (CoAP),” Internet Engineering Task Force, RFC 7252, Jun. 2014. [Online]. Available: http://www.rfc-editor.org/rfc/rfc7252.txt

[2]		R. Fielding, J. Gettys, J. Mogul, H. Frystyk, L. Masinter, P. Leach, and T. Berners-Lee, “Hypertext Transfer Protocol – HTTP/1.1,” Internet Engineering Task Force, RFC 2616, Jun. 1999. [Online]. Available: http://www.rfc-editor.org/rfc/rfc2616.txt

[3]		O. M. Alliance, “Lightweight Machine-to-Machine Technical Specification v1.0, Candidate Enabler,” Dec. 2015. [Online]. Available: http: //technical.openmobilealliance.org/Technical/technical-information/release-program/current-releases/oma-lightweightm2m-v1-0

[4]		M. Nottingham, “Web Linking,” Internet Engineering Task Force, RFC 5988, Oct. 2010. [Online]. Available: http://www.rfc-editor.org/rfc/rfc5988.txt

[5]		Z. Shelby, “Constrained RESTful Environments (CoRE) Link Format,” Internet Engineering Task Force, RFC 6690, Aug. 2012. [Online]. Available: http://www.rfc- editor.org/rfc/rfc6690.txt
