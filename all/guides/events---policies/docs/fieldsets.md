SortOrder: 3
# Fieldset

Fieldset is a unified control for additional data that can be returned in the response. 

## Policy fieldset

By default, the `policy` data in the response contains `id`, `eventId`, `name`, `updated_date` and `sortIndex` fields. 
The response will also include following parameters based on the fieldsets provided in the request.

 | Fieldset         | Fields                         |
 |------------------|--------------------------------|
 | BODY             | `body`                         |

## Token fieldset

By default, the get tokens response contains only `token` field. 
The response will also include following parameters based on the fieldsets provided in the request.

 | Fieldset         | Fields                         |
 |------------------|--------------------------------|
 | POLICIES         | `policies`                     |
