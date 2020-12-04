# Reports api documentation


## Filter Parameters

The following table describes the basic filter operators.
|Type | Operator | Description | Example
|---|---|---|----|
|Numeric | eq: | Equal | ?revenue=eq:2000|
|| neq: | Not equal | ?revenue=neq:2000|
||gt: | Greater than | ?total_click=gt:300|
||gte: | Greater than or equal | ?total_click=gte:300|
||lt: | Less than | ?spam_click=lt:890|
||lte: | Less than or equal | ?spam_click=lte:890|
|List |in: | In | ?zone_id=in:100987,1006932,1044875|
||nin:|Not in	| ?campaign_id=nin:1052894,1087325| 
<br>
  
| parameter | type | required | example | description
| ------ | ---- | ----- | ------ | ----- |
| sort | string | no |+stat_date|Sort by field. Value is a string (one or more of the selected dimensions or measures).|
| page | string | no |2,10|Report can return data paginated by n items. In order to paginate through data, you can specify “page” query parameter. Template: /{path}?page={page},{page_size}.|
| dimensions | string | yes | dimensions=stat_date,zone_id ||
| measures | string | yes | measures=total_click,income ||