Device communicaiton in Vulture Pi is accomplished through MQTT server running on local network. Using local network is not important while developing but during production using MQTT on local network is important to ensure security and performance.

![Image title](https://firebasestorage.googleapis.com/v0/b/vultureweb-ee535.appspot.com/o/DEVICE%20COMMUNICATION.drawio.png?alt=media&token=57d7e289-0125-4ed8-8733-fc76e6b112b6)

## Starting a local MQTT Server
Running a MQTT server is easy. Our team did not find much easier instructions so they are provided here.

### Requirements
* Ubuntu or Linux or WSL
* MQTT package

### Installing dependencies
To install MQTT package run:

<!-- termynal -->
```console
$ sudo apt install mosquitto
--------------------> 100%
Done!
```
**You may need to enter your password**

After installing, create a custom configuration file for the local server.

```conf title="server settings.conf" linenums="1"

listener 1883 <your_ip_address>
log_dest syslog
log_dest stdout
log_dest topic
log_type error
log_type warning
log_type notice
log_type information
connection_messages true
log_timestamp true
allow_anonymous true
```

This is the configuration file for the MQTT local server we will use this by:

```command
mosquitto -c /etc/mosquitto/server_settings.conf
```

The path after -c flag depends on the file path of your .conf file.

!!! warning
    It is recommended to save the configuration file in **/etc/mosquitto** directory. Server will fail to start if the IP Address provided is invalid. So, keep in mind to update IP address once you connect to any other internet.

After hitting enter the server should start and output the following:

```command
1670310431: mosquitto version 2.0.11 starting
1670310431: Config loaded from /etc/mosquitto/server_settings.conf.
1670310431: Opening ipv4 listen socket on port 1883.
1670310431: mosquitto version 2.0.11 running
```

!!! success
    The server is running. You can now subscribe to topics, publish messages through the SDK or the terminal itself.

## Connecting to broker

Using this feature in SDK is easy. By calling `#!python3 device_com.connect_broker()`. This function does not take any arguments as it utilises settings in the **settings.ini** file under system sections namely **ip_address** and **mqtt_port**. 

```py title="main.py" linenums="1"
from device_com import connect_broker

connect_broker()
```

Through this function python will start listening on the local ip address and default port 1883.


### Utilise incoming values

`#!python3 device_com.connect_broker()` already has an event name **on_message** which is triggered when a message is received by the client. By default this decodes the values and returns it. You can use those value like:

```py title="main.py" linenums="1"
from device_com import connect_broker

vals = connect_broker()
if vals == 0:  # Put any condition you want
    print("Value received is 0")

else:
    print("Value received is not 0")
```