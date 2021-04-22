# ESP32Logger
Logger for ESP32 for debugging C++-code

## Introduction
ESP32Logger is a C++-library for ESP32/Arduino.
The library contains a class ESP32Logger wich contains the functionality.
The logging-functions are used via macro-functions; this makes it possible not only to deactivate logging but to compile the code even w/o any logging-code included, and without deleting your logging-comamands in the project.
Logging is done to serial-output.
The logging includes 
* a timestamp (optional, can be time passed since start (in ms) or a specific time)
* name of the function which contains the logging-function.
Example code:
```C++
char s[] = "Test";
DBGLOG(Info, "This is an info-example; string-value s: %s.", s)
uint32_t u = 123;
DBGLOG(Error, "This is an error message; uint-value u: %u.", u)
```
Example output:
00000004120 INF setup: This is an info-example; string-value s: test.
00000004120 ERR setup: This is an error message; uint-value u: 123.

Logging depends on the choosen level of logging; the three levels are:
* Error
* Info
* Debug

## Outlook
Add other forms of output as acutally the serial-output, like e.g. via MQTT.

## Include the library in the project

Include library in the project and activate in general the logging-funcionality (i.e. include code for logging in the project):
```C++
#define ESP32DEBUGGING
#include <ESP32Logger.h>
```
Just comment out the #define ESP32DEBUGGING definition and no logging-code will be included to the project.
It is not necessary to remove the logging-commands out of the project-code.

## Initialize logging with DBGINI

Initialize the logging, usually done in the setup()-function, by one of the four alternatives:
```C++
DBGINI(&Serial, ESP32Timestamp::TimestampSinceStart)
```

