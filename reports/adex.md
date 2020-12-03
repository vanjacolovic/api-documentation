# Adex reports
host: api.ocamba.com

Use the /reports/adex/ resource to get a custom report. A successful request returns the HTTP 200 OK status code and a JSON or CSV formatted response body. Response body format can be controlled by HTTP Accept header. By default, this resource returns CSV formatted response body.


# Dimensions
Dimensions are attributes of your data. Value is a string that can take multiple values separated by a comma. Maximum length: 100.

| parameter | type | description
| ------ | ---- | ------ |
| subid |string||
| zone_id |int||
| zone_name |string||
| exchange_id |int||
| exchange_name |string||

# Measures


# Examples
