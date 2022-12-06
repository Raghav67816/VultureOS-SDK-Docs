To simulate real experience for testing, authenticating user and playing around makes it development more easy. You can authenticate yourself as a user using `#!python3 admin.authenticate(email, password)`.

```py title="main.py" linenums="1"
from admin import authenticate_user

user = authenticate_user(email, password)
print(user)
```

This will try to authenticate user and store the dict containing imporatant information and then return it.


```js title="example_json"
{
  "kind": "identitytoolkit#VerifyPasswordResponse",
  "localId": "snzZNdXCQuVrT6pyqk2HxDnDn4M2",
  "email": "johndoe@gmail.com",
  "displayName": "John Doe",
  "idToken": "eyJhbGciOiJSUzI1NiIsImtpZCI6Ijk1MWMwOGM1MTZhZTM1MmI4OWU0ZDJlMGUxNDA5NmY3MzQ5NDJhODciLCJ0eXAiOiJKV1QifQ.eyJuYW1lIjoiSm9obiBEb2UiLCJkZXZlbG9wZXIiOmZhbHNlLCJlbXBsb3llZSI6ZmFsc2UsImlzcyI6Imh0dHBzOi8vc2VjdXJldG9rZW4uZ29vZ2xlLmNvbS92dWx0dXJld2ViLWVlNTM1IiwiYXVkIjoidnVsdHVyZXdlYi1lZTUzNSIsImF1dGhfdGltZSI6MTY3MDE0ODk2NCwidXNlcl9pZCI6InNuelpOZFhDUXVWclQ2cHlxazJIeERuRG40TTIiLCJzdWIiOiJzbnpaTmRYQ1F1VnJUNnB5cWsySHhEbkRuNE0yIiwiaWF0IjoxNjcwMTQ4OTY0LCJleHAiOjE2NzAxNTI1NjQsImVtYWlsIjoiam9obmRvZUBnbWFpbC5jb20iLCJlbWFpbF92ZXJpZmllZCI6ZmFsc2UsInBob25lX251bWJlciI6Iis5MTkzMTkzNzY4MzAiLCJmaXJlYmFzZSI6eyJpZGVudGl0aWVzIjp7InBob25lIjpbIis5MTkzMTkzNzY4MzAiXSwiZW1haWwiOlsiam9obmRvZUBnbWFpbC5jb20iXX0sInNpZ25faW5fcHJvdmlkZXIiOiJwYXNzd29yZCJ9fQ.HbUH8VifbFesXKRpCZYqJ2bapp7QxUcBx8Kb13SbicH7HcwIteYwtcBNM_UGQf8acNDHchkPxjIyugKmWexJsAmvwm79-X6Dmak0V26qK8d7xWeFqxzoa62AaWbJHGnRGQPmGp5tMJOZKyTruxrur6O9FMZv9IpkrqhT1Ckk0svG0S_VYuHHHBk0JMyXsNwDKMKwIAM5JZij7NOuHb9sV_exkxNZcWJWXtzyp6EdkKesqwXVnSPcbDK-EJ2yuG8L9PfsusbE-K0MkbVA3gcm0zggRoFCh7oJJ-hiYkXA8SYbg7VGPUJqZ8uPQuAs43RHKwrFgyRYA1mA6YTuSNLg-w",
  "registered": true,
  "refreshToken": "AOkPPWRRwd3fX5ePLgDqe_s2dfILSfRU7LeZaGyK7z_Emw-E_rNRhTKVzSAVcpLqguhDm8fdeMGUO6Ta4NEEasTLSzdMVf_wxUcgXVCeCZviaK74TIqp1dHTZ3TCdzGxmU6Ecelaz330LCsnoVz3kslAReTfbifzSCfun9Xq3koSRBMEC2UxCCEMvf5E9jhWqTPvRT8YW33PRgHsvpRNPNNpnoPG773snJFX-qfUKc3ACKROhaZ0NO8",
  "expiresIn": "3600"
}
```

Then we can get keys from this dict to process values. However VultureOS SDK automates this process for you. It automatically collects information and writes it to the config file.

```ini title="config.ini" linenums="1"
[weather]
base_url = https://api.openweathermap.org/data/2.5/weather?q=
api_key = sample api key
city = 

[db]
url = mongodb://127.0.0.1:27017/
name = Vulture_Web_DB

[user]
display_name = John Doe
id_token = eyJhbGciOiJSUzI1NiIsImtpZCI6Ijk1MWMwOGM1MTZhZTM1MmI4OWU0ZDJlMGUxNDA5NmY3MzQ5NDJhODciLCJ0eXAiOiJKV1QifQ.eyJuYW1lIjoiSm9obiBEb2UiLCJkZXZlbG9wZXIiOnRydWUsImVtcGxveWVlIjp0cnVlLCJpc3MiOiJodHRwczovL3NlY3VyZXRva2VuLmdvb2dsZS5jb20vdnVsdHVyZXdlYi1lZTUzNSIsImF1ZCI6InZ1bHR1cmV3ZWItZWU1MzUiLCJhdXRoX3RpbWUiOjE2NzAxNTI2NzAsInVzZXJfaWQiOiJ2TjJicm9kTFFuYVNEbTVsdWVyUjZjcGFDSEoyIiwic3ViIjoidk4yYnJvZExRbmFTRG01bHVlclI2Y3BhQ0hKMiIsImlhdCI6MTY3MDE1MjY3MCwiZXhwIjoxNjcwMTU2MjcwLCJlbWFpbCI6ImpvaG5kb2VAZ21haWwuY29tIiwiZW1haWxfdmVyaWZpZWQiOmZhbHNlLCJwaG9uZV9udW1iZXIiOiIrOTE5MzE5Mzc2ODMwIiwiZmlyZWJhc2UiOnsiaWRlbnRpdGllcyI6eyJwaG9uZSI6WyIrOTE5MzE5Mzc2ODMwIl0sImVtYWlsIjpbImpvaG5kb2VAZ21haWwuY29tIl19LCJzaWduX2luX3Byb3ZpZGVyIjoicGFzc3dvcmQifX0.d6u_w3XINO7NILJaFJuQY_082eC4qw3WTMsSgmuAvcCawOo4ucrovNj345ZiBhMe5C_yVqQMj4LQDfloztdn-mH7vjHW3Mwj7CB3xum7K-QLNIv1xEss5eY_SBM8mmfMjkejAi0-bqQb_S1WkCTnQ-rCdHwkmCqvDjvmLpx-SO2XzS9NhdDF1TcL0m5HZDnzeWPh2HbbKTB8H73ltot2XrcwZAlAyiW42Z4Rq01pR3F-Awkmpi7SfCyAdUALBMk6HCY9Mec4Y7W0F38kL0M30Xdo3JaYu1Ny-1hAaBrvZZ41SYtQuu2IUUBJpELPjuKYAajxaseDHjcZOkRVeR0hFw
user_uid = vN2brodLQnaSDm5luerR6cpaCHJ2
email = johndoe@gmail.com

[request_urls]
login = http://127.0.0.1:3000/auth/login
device_reg = http://127.0.0.1:3000/devices/register
get_app = http://127.0.0.1:3000/vstore/get_apps
upload_new = http://127.0.0.1:3000/vstore/upload_new

[system]
ip_address = 
apps_path = apps/
mqtt_port = 1883

```