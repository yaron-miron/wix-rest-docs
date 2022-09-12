SortOrder: 1
# Field Support for Filtering and Sorting

The table below shows field support for filters and sorting.

## Query Language

Endpoints that allow for querying follow the [API Query Language](https://dev.wix.com/api/rest/getting-started/api-query-language).

## Post API
### Fields That Allow Filtering

| Field | Operators | Sorting Allowed|
| --- | --- | --- |
| id |$eq, $ne, $hasSome, $urlized|Allowed|
| title |$eq, $ne, $contains, $urlized, $startsWith, $endsWith, $hasSome, $lt, $lte, $gt, $gte, $exists, $in|Allowed|
| firstPublishedDate |$eq, $ne, $lt, $lte, $gt, $gte, $in|Allowed|
| lastPublishedDate |$eq, $ne, $lt, $lte, $gt, $gte, $in|Allowed|
| slug |$hasSome, $hasAll, $urlized||
| featured |$eq, $ne|Allowed|
| pinned |$eq, $ne|Allowed|
| categoryIds |$hasSome, $hasAll||
| mainCategoryId |$eq, $ne, $hasSome||
| memberId |$eq, $ne, $hasSome||
| hashtags |$hasSome, $hasAll||
| commentingEnabled |$eq, $ne|Allowed|
| minutesToRead |$eq, $ne, $lt, $lte, $gt, $gte, $in||
| tagIds |$hasSome, $hasAll||
| pricingPlanIds |$hasSome, $hasAll||
| language |$eq, $ne, $hasSome, $exists, $in||
| translationId |$eq, $ne, $exists, $in||
| metrics.views |$eq, $ne, $lt, $lte, $gt, $gte, $in|Allowed|
| metrics.comments |$eq, $ne, $lt, $lte, $gt, $gte, $in|Allowed|
| metrics.likes |$eq, $ne, $lt, $lte, $gt, $gte, $in|Allowed|
| coverMedia.enabled |$eq, $ne||

** Note that "hasSome" is same as the operator "IN" in SQL

### Examples

**Query pinned posts**

```
curl 'https://www.wixapis.com/blog/v3/posts/query' --data-binary '{"filter": {"pinned": {"$eq": true}}}' -H 'Content-Type: application/json' -H 'Authorization: <AUTH>'
```

**Get all posts, sorted by publication date (latest first)**

```
curl 'https://www.wixapis.com/blog/v3/posts/query' --data-binary '{"sort":[{"fieldName": "firstPublishedDate", "order": "DESC"}]}' -H 'Content-Type: application/json' -H 'Authorization: <AUTH>'
```

**Get posts by IDs**

```
curl 'https://www.wixapis.com/blog/v3/posts/query' --data-binary '{"filter": {"id": {"$hasSome": ["POST_ID_1","POST_ID_2"]}}}' -H 'Content-Type: application/json' -H 'Authorization: <AUTH>'
```

## Category API
### Fields That Allow Filtering

| Field         | Operators | Sorting Allowed|
|---------------| --- | --- |
| id            |$eq, $ne, $hasSome, $urlized||
| title         |$eq, $ne, $contains, $urlized, $startsWith, $endsWith, $hasSome, $lt, $lte, $gt, $gte, $exists, $in|Allowed|
| label         |$eq, $ne, $contains, $urlized, $startsWith, $endsWith, $hasSome, $lt, $lte, $gt, $gte, $exists, $in|Allowed|
| postCount     |$eq, $ne, $lt, $lte, $gt, $gte, $in|Allowed|
| displayPosition     |$eq, $ne, $lt, $lte, $gt, $gte, $in|Allowed|
| translationId |$eq, $ne, $exists, $in||
| language      |$eq, $ne, $exists, $in|Allowed|
| slug          |$hasSome, $hasAll|Allowed|

** Note that "hasSome" is same as the operator "IN" in SQL

### Examples

**Query categories by description**

```
curl 'https://www.wixapis.com/blog/v3/categories/query' --data-binary '{"filter": {"description": {"$contains": "cat"}}}' -H 'Content-Type: application/json' -H 'Authorization: <AUTH>'
```

**Get all categories, sorted by display position**

```
curl 'https://www.wixapis.com/blog/v3/categories/query' --data-binary '{"sort":[{"fieldName": "displayPosition"}]}' -H 'Content-Type: application/json' -H 'Authorization: <AUTH>'
```

**Get categories by IDs**

```
curl 'https://www.wixapis.com/blog/v3/categories/query' --data-binary '{"filter": {"id": {"$hasSome": ["CATEGORY_ID_1","CATEGORY_ID_2"]}}}' -H 'Content-Type: application/json' -H 'Authorization: <AUTH>'
```
