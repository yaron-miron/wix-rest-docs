SortOrder: 2
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

 ## Query Policies
 [//]: # (https://bo.wix.com/wix-docs/rest/events/wix-events/filter-and-sort#events_wix-events_filter-and-sort_query-policies)

| Field            | Query Filter Operators      |
|------------------|-----------------------------|
| policyId         | $eq,$ne,$hasSome,$contains  |         
| eventId          | $eq,$hasSome                |         

[//]: # (Full list of operators for reference: $eq,$ne,$lt,$lte,$gt,$gte,$hasSome,$in,$contains,$startsWith,$endsWith,$urlized,$exists)
