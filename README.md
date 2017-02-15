
# Python bindings for ipapi (IP address location API)

## Installation

```
pip install ipapi
```
or

```
python setup.py install
```

## Usage

### From your Python code

```
import ipapi
ipapi.location(ip=None, key=None, field=None)
```

- `ip`    : use specified IP address. If omitted or `None`, use your machine's IP address
- `key`   : For paid plans
- `field` : get specified field (ip, city, country, timezone etc.) as text. If omitted or `None`, get entire location data as `JSON`

#### Examples

```
ipapi.location()
# Gets complete location for your IP address
{u'city': u'Wilton', u'ip': u'50.1.2.3', u'region': u'California', u'longitude': -121.2429, u'country': u'US', u'latitude': 38.3926, u'timezone': u'America/Los_Angeles', u'postal': u'95693'}

ipapi.location(None, None, 'ip')
# Gets my external IP address
u'50.1.2.3'

ipapi.location(None, None, 'city')
# Gets your city name
u'Wilton'

ipapi.location(None, None, 'country')
# Gets your country
u'US'

ipapi.location('8.8.8.8')
# Gets complete location for IP address 8.8.8.8
{u'city': u'Mountain View', u'ip': u'8.8.8.8', u'region': u'California', u'longitude': -122.0838, u'country': u'US', u'latitude': 37.386, u'timezone': u'America/Los_Angeles', u'postal': u'94035'}

ipapi.location('8.8.8.8', None, 'city')
# Gets city name for IP address 8.8.8.8
u'Mountain View'

ipapi.location('8.8.8.8', None, 'country')
# Gets country for IP address 8.8.8.8
u'US'
```


### From command line
```
$ python ipapi.py -i <IP address> -f <field> -k <API KEY>
```

#### Examples

```
$ python ipapi.py 
{u'city': u'Wilton', u'ip': u'50.1.2.3', u'region': u'California', u'longitude': -121.2429, u'country': u'US', u'latitude': 38.3926, u'timezone': u'America/Los_Angeles', u'postal': u'95693'}

$ python ipapi.py  -f ip
50.1.2.3

$ python ipapi.py  -f city
Wilton

$ python ipapi.py -i 8.8.8.8
{u'city': u'Mountain View', u'ip': u'8.8.8.8', u'region': u'California', u'longitude': -122.0838, u'country': u'US', u'latitude': 37.386, u'timezone': u'America/Los_Angeles', u'postal': u'94035'}

$ python ipapi.py -i 8.8.8.8 -f city
Mountain View

$ python ipapi.py -i 8.8.8.8 -f country
US
```

### With API Key

API key can be specified in the following ways : 

1. Inside `ipapi.py` by setting `API_KEY` variable
2. Via command line with the `-k` option
3. As a function argument e.g. `ipapi.location(ip='8.8.8.8', key='secret-key')` or `ipapi.location(ip='8.8.8.8', key='secret-key', field='city')`

### Notes
- All function arguments (`ip`, `key`, `field`) are optional . To skip an argument, use `None` or an empty string `''`.
  `ipapi.location(ip='8.8.8.8', key=None, field='city')`
  `ipapi.location(ip='8.8.8.8', key='',   field='city')`    
