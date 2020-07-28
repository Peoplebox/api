# Peoplebox API
This documentation covers how you can use the Peoplebox API

## Overview
Hey there! Peoplebox API is not publicly available yet, but if you are interested we can give you an API token for your account to try it out.

# Authentication
Get the `api_token` by emailing support@peoplebox.ai for now. Once you get the `api_token`,  pass it as a query paramter `?api_token=XXXX` along with all requests

# API Documentation

## Get User Details

```
curl 'https://api.peoplebox.ai/users/get_user_details.json' \
   -H 'Accept: application/json, text/plain, */*' \
   -H 'Content-Type: application/json;charset=UTF-8' \
```

Get all information about the user for whome the `api_token` has been generated

## Get Goal Information
```
curl 'https://api.peoplebox.ai/accounts/<account-id>/employees/<employee-id>/goals/<goal-id>' \
   -H 'Accept: application/json, text/plain, */*' \
   -H 'Content-Type: application/json;charset=UTF-8' \
```
**Query Params**

Params
| Param         | Info           |
| ------------- |-------------|
| account_id    | Account Id, obtained from get_user_details |
| employee_id   | Id of the currently logged in user, obtained from get_user_details      |
| goal_id | You can get the goal id by logging into peoplebox and clicking on a specific goal. Use the goal ID in the URL |

Get all information about the goal 

## Checkin Key Results

```
curl 'https://api.peoplebox.ai/accounts/<your-account-id>/employees/<your-employee-id>/goals/<goal-id>/key_results/<key-result-id>/key_result_checkins.json?api_token=XXXX' \
  -H 'Accept: application/json, text/plain, */*' \
  -H 'Content-Type: application/json;charset=UTF-8' \
  --data-binary '{"checkin":{"description":"Launched new feature","completed_value":"153.0"}}' \
```

**Query Params**

| Param         | Info           |
| ------------- |-------------|
| account_id    | Account Id, obtained from get_user_details |
| employee_id   | Id of the currently logged in user, obtained from get_user_details      |
| goal_id | You can get the goal id by logging into peoplebox and clicking on a specific goal. Use the goal ID in the URL |
| key_result_id| Id of they key result, obtained from Goal Information API |

**Post JSON format**
```
{
  "checkin":
    {
      "description":"<Message along with the checkin>",
      "completed_value":"<Value of the updated checkin>"
    }
}
```
