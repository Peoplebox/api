# Peoplebox API
This documentation covers how you can use the Peoplebox API

## Overview
Hey there! Peoplebox API is not publicly available yet, but if you are interested we can give you an API token for your account to try it out.

# Authentication
Get the `api_token` by emailing support@peoplebox.ai for now. Once you get the `api_token`,  pass it as a query paramter `?api_token=XXXX` along with all requests

# API Documentation

## Get User Details

```
curl 'https://api.peoplebox.ai/users/get_user_details.json?api_token=XXX' \
   -H 'Accept: application/json, text/plain, */*' \
   -H 'Content-Type: application/json;charset=UTF-8' \
```

Get all information about the user for whome the `api_token` has been generated


## Get 1-on-1 Analytics

```
curl 'https://api.peoplebox.ai/accounts/32/homepage_analytics/get_homepage_insight?insight_type=one_on_one_meetings_analytics&time_filter=last_30_days&api_token=XXX' \
   -H 'Accept: application/json, text/plain, */*' \
   -H 'Content-Type: application/json;charset=UTF-8' \
```
**Params**
| Param         | Info           |
| ------------- |-------------|
| account_id    | Account Id, obtained from get_user_details |
| time_filter | Time range you want the data for `this_month,last_month,last_30_days,last_90_days,last_180_days,last_365_days,current_quarter,previous_quarter,current_year,previous_year`|


**Response**
```
[
  {
    "employee": {
      "id": 11842,
      "full_name": "Alba"
    },
    "direct_reports": 27,
    "time_since_last": -32,
    "unique_with_reports": 23,
    "talking_points_added": 7,
    "action_items_added": 5
  },
  {
    "employee": {
      "id": 13567,
      "full_name": "Bianka"
    },
    "direct_reports": 24,
    "time_since_last": -2,
    "unique_with_reports": 2,
    "talking_points_added": 0,
    "action_items_added": 0
  }
 ]
```


## Get Goal Information
```
curl 'https://api.peoplebox.ai/accounts/<account-id>/employees/<employee-id>/goals/<goal-id>?api_token=XXX' \
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
