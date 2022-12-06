Once, you purchase a device beloging to Vulture Pi, then on the backside of the product you will find device serial number. Using this you can register it. Registering the device is similar to claiming the ownership of the device.

This can be accomplished using Web Version, but for developers this feature is also provided in the SDK.

```py title="main.py" linenums="1"
from device_manager import register_new_device

register_new_device(device_type, device_sr_no, owner_uid, id_token)
```
The parameters are already in the settings.ini file. For getting these values you have to make your own configpareser object.

If successfull it would return a dictionary

The dictionary will contain device serial number, message and owner uid.

Once, registered then the device can be omitted by the employees only.

