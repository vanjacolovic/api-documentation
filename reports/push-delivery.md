# Push delivery reports
host: api.ocamba.com

Use the /reports/push/delivery resource to get a custom report. A successful request returns the HTTP 200 OK status code and a JSON or CSV formatted response body. Response body format can be controlled by the HTTP Accept header. By default, this resource returns a CSV formatted response body.


# Dimensions
Dimensions are attributes of your data. 

Value is a string that can take multiple values separated by a comma. 

Maximum length: 100.

This parameter is required.

| parameter | type | example | description
| ------ | ---- | ------ | ----- |
| delivery_time | string |2020-11-20 11:40:00|Task execution time.|
| task_id |int|1002600|The ID of the task.|
| task_name |string|Demo task|The name of the task.|
| app_id |int|1459574831|The ID of the app.|
| app_name |string|Demo app|The name of the app.|

# Measures
This parameter represent the values that you're measuring. For example, you can measure app performance by looking at your earnings or number of clicks.

Value is a string that can take multiple values separated by a comma.

Maximum length: 100.

This parameter is required.

| parameter | type | example | description
| ------ | ---- | ------ | ----- |
| impression |int|15268|The total number of impressions.|
| total_click |int|1277|The total number of clicks (including spam).|
| click |int|1562|The total number of valid clicks.|
| spam_click |int|94|The total number of spam clicks.|
| ctr |float|0.15|The rate of clicks to impressions.|
| ctdr |float|1.23|The rate of clicks to delivered.|
| income |float|16.52||
| conversion |int|12|The total number of conversions.|
| total_user |int|2897|The total number of users.|
| unsubscribed |int|2123|The total number of unsubscribed users.|
| wokenup |int|480876|The total number of wokenup users.|
| delivered |int|888248|The total number of ads delivered to users.|
| failed |int|9|The total number of users failed to receive ads.|
| delivery_rate |float|0.54|The rate of wokenup to total user.|

# Other parameters

These parameters are not required. 

| parameter | type | example | description
| ------ | ---- | ------ | ----- |
| task_id |string|1002600|Task id created on the Ocamba platform. This parameter can be used to filter your data by the specified task.|
| app_id |string|1002600|App id created on the Ocamba platform. This parameter can be used to filter your data by the specified app.|
| sort |string|+delivered|Sort by field. Value should be one of the selected dimensions or measures.| 
| page |string|2,10|The report can return data paginated by n items. In order to paginate through data, you can specify the “page” query parameter. The default setup is to return the first 100 results.|
| stat_date |string|2020-12-08|Interval of time.<br>Single Format: Y-m-d<br>Range format: Y-m-d &#124; Y-m-d<br>Hour format: Y-m-d hh:00:00<br><br>If “single format” is used, the report displays stats for tasks executed on this specific day.<br>If “range format” is used, the report displays stats for tasks executed in this specific range.<br>If “hour format” is used, the report displays stats for tasks executed in this specific hour.<br><br>If you exclude this parameter, the default setup displays the last executed tasks. This case requires dimension delivery_time.|

# Examples
**GET STATISTICS BY DATE (SINGLE FORMAT)**

Sample Request: GET /v1/reports/push/delivery?dimensions=delivery_time,task_name&measures=total_user,unsubscribed,delivered,wokenup,failed,income,total_click&stat_date=2020-12-08&sort=-delivery_time

Authorization: Bearer [bearer_token]

Accept: text/csv

Sample Response:

HTTP/1.1 200 OK

Content-Type: text/csv

**GET STATISTICS BY DATE RANGE (RANGE FORMAT)**

Sample Request: GET /v1/reports/push/delivery?dimensions=delivery_time,task_name&measures=total_user,unsubscribed,delivered,wokenup,failed,income,total_click&stat_date=2020-12-07|2020-12-09

Authorization: Bearer [bearer_token]

Accept: text/csv

**GET STATISTICS BY HOUR (HOUR FORMAT)**

Sample Request: GET /v1/reports/push/delivery?dimensions=delivery_time,task_name&measures=total_user,unsubscribed,delivered,wokenup,failed,income,total_click&stat_date=2020-12-08 15:00:00&sort=+delivery_time

Authorization: Bearer [bearer_token]

Accept: text/csv

**GET LAST STATISTICS (WHERE TOTAL USER IS GREATER THAN 0)**

Sample Request: GET /v1/reports/push/delivery?dimensions=delivery_time,task_name&measures=total_user,unsubscribed,delivered,wokenup,failed,income,total_click&total_user=gt:0

Authorization: Bearer [bearer_token]

Accept: text/csv

**GET STATISTICS FILTERED BY TASK ID**

Sample Request: GET /v1/reports/push/delivery?dimensions=delivery_time,task_name&measures=total_user,unsubscribed,delivered,wokenup,failed,income,total_click&task_id=2113398

Authorization: Bearer [bearer_token]

Accept: text/csv

**GET STATISTICS BY TASK ID (FILTERED BY APP ID, SORTED BY DELIVERED)**

Sample Request: GET 127.0.0.1:6161/v1/reports/push/delivery?dimensions=delivery_time,task_name&measures=total_user,unsubscribed,delivered,wokenup,failed,income,total_click&stat_date=2020-12-08&sort=-delivered&app_id=4189144052

Authorization: Bearer [bearer_token]

Accept: text/csv

## Report performance (IMPORTANT)

- **A wide date range will increase response time.**
- **The maximum date range is 100 days.**
- **It's recommended not to use a date range wider than 30 days.**
- **The number of requested dimensions in the report will have an increasing effect on response time and amount of data that will be generated by API.**
- **It's recommended to use a lower number of dimensions in reports.**
- **The number of requested measures should not have a significant impact on report performance.**
