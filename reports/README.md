# Reports api documentation


| parameter | type | required | example | description
| ------ | ---- | ----- | ------ | ----- |
| sort | string | no |+stat_date|Sort by field. Value is a string (one or more of the selected dimensions or measures).|
| page | string | no |2,10|Report can return data paginated by n items. In order to paginate through data, you can specify “page” query parameter. Template: /{path}?page={page},{page_size}.|
| dimensions | string | yes | dimensions=stat_date,zone_id ||
| measures | string | yes | measures=total_click,income ||