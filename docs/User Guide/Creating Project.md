# Creating new project

SDK already provides functions to quickly create a project according to the environment of the actual OS.

First, activate the virtualenv (if using) and start python3
```commandline
>>> from admin import create_config_file
>>> dir_path = "<path/to/dir>"
>>> create_config_file(dir_path)
```

This outputs the following, if successfull
```commandline
Generating default configuration file.
File generated
```

This creates a **.ini** file which works as a settings file in the specified directory. However, it is recommended to store the **.ini** file in the project or root directory.

```ini title="config.ini" linenums="1"
[weather]
base_url = https://api.openweathermap.org/data/2.5/weather?q=
api_key = <openweather_api_key>
city = 

[db]
url = <your MongoDB url>
name = <your MongoDB name>

[user]
display_name = 
id_token = 
user_uid = 
email = 

[request_urls]
login = http://127.0.0.1:8000/auth/login
device_reg = http://127.0.0.1:8000/devices/register
get_app = http://127.0.0.1:8000/vstore/get_apps
upload_new = http://127.0.0.1:8000/vstore/upload_new

[system]
ip_address = <your ip address>
apps_path = apps/
mqtt_port = 1883

```

!!! warning
    Endpoints in the **request_urls** are for localhost only because the API is not hosted yet. But, these urls will be updated once the API is up and running.

This functionallity can also be acheived by a python file.
```py linenums="1" title="main.py" 
from admin import create_config_file

dir_path = "path/to/dir"
create_config_file(dir_path)
```

## Sections in config file
Descriptions of the sections in **config.ini**. All the sections except Weather are **must** to use.

### Weather
Weather section is optional, this feature is already implemented in the OS, but it is for our innovative vultures who can make even this feature unique somehow. However, it is not necessary to use OpenWeather only.

### DB - Database
DB section is important because the OS uses MongoDB locally to manage data instead of json files. As, it's more accurate and secure. Using MongoDB is important to ensure performance and optimization.

### User
User sections stores user credentails once the user is authenticated using `#!python3 admin.authenticate_user(email, password)` in the admin file.

### Request URLs
request_urls section holds the endpoints to which you can call to perform various functions.

### System
System section holds only required values from your system.

!!! note
    Your IP Address is not shared with any 3rd-patry clients. It is securily fetched through **netifaces** python package.
    