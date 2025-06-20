# 📊 MongoDB Aggregation Stages – Pro Backend Developer Guide

A curated list of **essential and standout MongoDB aggregation stages**, complete with descriptions and examples, tailored for backend developers aiming to be top-tier.

---

## 🔧 Core Must-Know Stages

### 1. `$match`
**Description:** Filters documents by specified conditions (similar to `find()`).
```js
{ $match: { status: "active", age: { $gte: 18 } } }
```

---

### 2. `$project`
**Description:** Shapes documents by including/excluding fields or adding computed fields.
```js
{ $project: { fullName: { $concat: ["$firstName", " ", "$lastName"] }, _id: 0 } }
```

---

### 3. `$group`
**Description:** Groups documents by a field and applies aggregation expressions.
```js
{ $group: { _id: "$category", total: { $sum: "$amount" } } }
```

---

### 4. `$sort`
**Description:** Sorts documents in ascending or descending order.
```js
{ $sort: { createdAt: -1 } }
```

---

### 5. `$skip` & `$limit`
**Description:** Skips and limits results, used for pagination.
```js
{ $skip: 10 }, { $limit: 10 }
```

---

### 6. `$lookup`
**Description:** Performs a left outer join with another collection.
```js
{
  $lookup: {
    from: "users",
    localField: "userId",
    foreignField: "_id",
    as: "userDetails"
  }
}
```

---

### 7. `$unwind`
**Description:** Deconstructs arrays into multiple documents.
```js
{ $unwind: "$items" }
```

---

### 8. `$addFields` / `$set`
**Description:** Adds new fields or modifies existing fields.
```js
{ $addFields: { tax: { $multiply: ["$price", 0.1] } } }
```

---

### 9. `$count`
**Description:** Returns a count of documents.
```js
{ $count: "totalUsers" }
```

---

### 10. `$facet`
**Description:** Runs multiple pipelines in parallel.
```js
{
  $facet: {
    paginatedResults: [{ $skip: 0 }, { $limit: 5 }],
    totalCount: [{ $count: "count" }]
  }
}
```

---

## 🌟 Advanced & Standout Stages

### 11. `$bucket`
**Description:** Group documents into user-defined ranges (buckets).
```js
{
  $bucket: {
    groupBy: "$price",
    boundaries: [0, 100, 200, 300],
    default: "Other",
    output: { count: { $sum: 1 } }
  }
}
```

---

### 12. `$bucketAuto`
**Description:** Automatically creates N equal-sized buckets.
```js
{
  $bucketAuto: {
    groupBy: "$age",
    buckets: 4
  }
}
```

---

### 13. `$sortByCount`
**Description:** Shortcut for grouping and sorting by frequency.
```js
{ $sortByCount: "$category" }
```

---

### 14. `$sample`
**Description:** Randomly selects N documents.
```js
{ $sample: { size: 5 } }
```

---

### 15. `$graphLookup`
**Description:** Recursively search documents in a graph structure.
```js
{
  $graphLookup: {
    from: "employees",
    startWith: "$managerId",
    connectFromField: "managerId",
    connectToField: "_id",
    as: "managementHierarchy"
  }
}
```

---

### 16. `$out`
**Description:** Writes pipeline results to a collection.
```js
{ $out: "summaryCollection" }
```

---

### 17. `$merge`
**Description:** Merges pipeline results into a collection with update or insert semantics.
```js
{
  $merge: {
    into: "report",
    whenMatched: "merge",
    whenNotMatched: "insert"
  }
}
```

---

### 18. `$geoNear`
**Description:** Performs geospatial queries to return documents sorted by proximity.
```js
{
  $geoNear: {
    near: { type: "Point", coordinates: [77.5946, 12.9716] },
    distanceField: "distance",
    spherical: true
  }
}
```

---

### 19. `$replaceRoot` / `$replaceWith`
**Description:** Replaces the root document with a specified nested document.
```js
{ $replaceRoot: { newRoot: "$details" } }
```

---

### 20. `$redact`
**Description:** Conditionally include/exclude fields for field-level access control.
```js
{
  $redact: {
    $cond: {
      if: { $eq: ["$access", "restricted"] },
      then: "$$PRUNE",
      else: "$$KEEP"
    }
  }
}
```

---

## 🏅 Honourable Mentions

### `$indexStats`
Provides index usage statistics (used more for diagnostics than aggregation).

### `$collStats`
Gives collection statistics including storage size, count, etc.

### `$planCacheStats`
Reports on query plan cache performance.

---

## 🛑 Deprecated (Avoid Using)

- `$currentOp` (use admin commands instead)
- `$text` in pipelines (better to use in regular queries)

---

**🧠 Pro Tip:** Most real-world aggregations are a mix of `\$match → \$unwind → \$group → \$sort → \$skip/\$limit`, and joining with `\$lookup` or shaping with `\$project` / `\$addFields`.

---

Crafted for backend professionals aiming to go beyond CRUD and build high-performance, scalable MongoDB systems.
---

# 🔍 MongoDB Query Operators – Top 20 You Should Know

These operators are used inside `$match`, `$expr`, and other stages to filter or compare field values.

---

### 1. `$eq`
**Description:** Matches values that are equal to a specified value.
```js
{ age: { $eq: 25 } }
```

---

### 2. `$ne`
**Description:** Matches all values that are not equal to a specified value.
```js
{ status: { $ne: "inactive" } }
```

---

### 3. `$gt`
**Description:** Matches values that are greater than a specified value.
```js
{ age: { $gt: 18 } }
```

---

### 4. `$gte`
**Description:** Matches values that are greater than or equal to a specified value.
```js
{ score: { $gte: 90 } }
```

---

### 5. `$lt`
**Description:** Matches values that are less than a specified value.
```js
{ price: { $lt: 100 } }
```

---

### 6. `$lte`
**Description:** Matches values that are less than or equal to a specified value.
```js
{ price: { $lte: 100 } }
```

---

### 7. `$in`
**Description:** Matches any of the values specified in an array.
```js
{ category: { $in: ["tech", "fashion"] } }
```

---

### 8. `$nin`
**Description:** Matches none of the values specified in an array.
```js
{ role: { $nin: ["admin", "superuser"] } }
```

---

### 9. `$and`
**Description:** Joins query clauses with a logical AND.
```js
{ $and: [{ status: "active" }, { age: { $gt: 18 } }] }
```

---

### 10. `$or`
**Description:** Joins query clauses with a logical OR.
```js
{ $or: [{ age: { $lt: 18 } }, { isMinor: true }] }
```

---

### 11. `$not`
**Description:** Inverts the effect of a query expression.
```js
{ age: { $not: { $gte: 18 } } }
```

---

### 12. `$exists`
**Description:** Matches documents that have the specified field.
```js
{ phoneNumber: { $exists: true } }
```

---

### 13. `$type`
**Description:** Matches documents where the field is of the specified BSON type.
```js
{ age: { $type: "int" } }
```

---

### 14. `$regex`
**Description:** Matches documents with values matching the specified regular expression.
```js
{ name: { $regex: "^A", $options: "i" } }
```

---

### 15. `$expr`
**Description:** Allows the use of aggregation expressions inside `$match`.
```js
{ $expr: { $gt: ["$spent", "$budget"] } }
```

---

### 16. `$mod`
**Description:** Matches numbers that are divisible by a given divisor.
```js
{ quantity: { $mod: [5, 0] } }
```

---

### 17. `$size`
**Description:** Matches any array with the specified number of elements.
```js
{ tags: { $size: 3 } }
```

---

### 18. `$all`
**Description:** Matches arrays that contain all elements specified.
```js
{ tags: { $all: ["mongodb", "database"] } }
```

---

### 19. `$elemMatch`
**Description:** Matches documents that contain an array field with at least one element matching all specified criteria.
```js
{ scores: { $elemMatch: { $gt: 70, $lt: 90 } } }
```

---

### 20. `$slice`
**Description:** Limits the number of elements returned from an array field.
```js
{ comments: { $slice: 5 } }
```

---