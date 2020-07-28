# Peoplebox API
This documentation covers how you can use the Peoplebox API

## Overview
Hey there! Peoplebox API is not publicly available yet, but if you are interested we can give you an API token for your account to try it out.

# Authentication
Get the `api_token` by emailing support@peoplebox.ai for now. Once you get the `api_token`,  pass it as a query paramter `?api_token=XXXX` along with all requests

# API Documentation

## Checkin Key Results

```
curl 'http://api.peoplebox.ai/accounts/<your-account-id>/employees/<your-employee-id>/goals/<goal-id>/key_results/<key-result-id>/key_result_checkins?api_token=XXXX' \
  -H 'Accept: application/json, text/plain, */*' \
  -H 'Content-Type: application/json;charset=UTF-8' \
  --data-binary '{"checkin":{"description":"Launched new feature","completed_value":"153.0"}}' \
```
