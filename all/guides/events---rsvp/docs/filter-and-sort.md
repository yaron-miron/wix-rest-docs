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

## List & Query RSVPs
[//]: # (https://bo.wix.com/wix-docs/rest/events/wix-events/filter-and-sort#events_wix-events_filter-and-sort_list-query-rsvp)

| Field        | Description             | Query Filter Operators                                           | Sorting | Facets  |
|--------------|-------------------------|------------------------------------------------------------------|---------|---------|
| created      | Creation date           |                                                                  | Allowed |         |
| modified     | Modification date       |                                                                  | Allowed |         |
| name         | Guest name              |                                                                  | Allowed |         |
| score        | Search phrase relevance |                                                                  | Allowed |         |
| email        | Guest email             |                                                                  | Allowed |         |
| totalGuests  | Guest count             |                                                                  | Allowed |         |
| status       | Guest response          | $eq,$ne,$hasSome                                                 | Allowed | Allowed |
| rsvpId       |                         | $eq,$ne,$hasSome                                                 | Allowed |         |
| eventId      |                         | $eq,$ne,$hasSome                                                 |         | Allowed |

[//]: # (Full list of operators for reference: $eq,$ne,$lt,$lte,$gt,$gte,$hasSome,$in,$contains,$startsWith,$endsWith,$urlized,$exists)
