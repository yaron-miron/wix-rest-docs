SortOrder: 5
# Filter and Sort

Select endpoints allow sorting results by field. Use `field:asc` to sort results in **ascending** order, and `field:desc` to sort in **descending** order.

For example, to sort events by start date in ascending order, and then by modification date in descending order: 

```
?sort=start:asc,modified:desc
```

or 

```json
"sort": "start:asc,modified:desc"
```

Refer to the following tables to check which fields support sorting.

## List & Query Events
[//]: # (https://bo.wix.com/wix-docs/rest/events/wix-events/filter-and-sort#events_wix-events_filter-and-sort_list-query-event)

| Field            | Description       | Query Filter Operators                                  | Sorting | Facets  |
|------------------|-------------------|---------------------------------------------------------|---------|---------|
| created          | Creation date     | $eq,$ne,$lt,$lte,$gt,$gte,$hasSome                      | Allowed |         |
| modified         | Modification date | $eq,$ne,$lt,$lte,$gt,$gte,$hasSome                      | Allowed |         |
| start            | Start date        | $eq,$ne,$lt,$lte,$gt,$gte,$hasSome                      | Allowed |         |
| end              | End date          | $eq,$ne,$lt,$lte,$gt,$gte,$hasSome                      | Allowed |         |
| title            |                   | $eq,$ne,$lt,$lte,$gt,$gte,$hasSome,$contains,$urlized   | Allowed |         |
| slug             | URL slug          | $eq,$ne,$lt,$lte,$gt,$gte,$hasSome,$contains,$urlized   | Allowed |         |
| status           |                   | $eq,$ne,$hasSome                                        |         | Allowed |
| eventId          |                   | $eq,$ne,$hasSome                                        |         |         |
| userId           |                   | $eq,$ne,$hasSome                                        |         |         |
| categoryId       |                   | $eq,$ne,$hasSome                                        |         |         |
| categoryState    |                   | $eq,$ne,$hasSome                                        |         | Allowed |        
| recurrenceStatus |                   | $eq,$ne,$hasSome                                        |         | Allowed |
| recurringGroupId |                   | $eq,$ne,$hasSome                                        |         |         |

[//]: # (Full list of operators for reference: $eq,$ne,$lt,$lte,$gt,$gte,$hasSome,$in,$contains,$startsWith,$endsWith,$urlized,$exists)
