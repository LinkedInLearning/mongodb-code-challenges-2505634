# Challenge 4-1 - Removing data from arrays

## Challenge

Use the updateOne () method to alter an array with selected documents in the customers collection as follows:

1. Disassociate an order with a user, using a valid id found in a user's orders array.
1. Empty one user's `favoriteCategories` array, using their email address as the lookup key

### Hints

> Need a hand? Check out the official documentation: [Querying Arrays](https://www.mongodb.com/docs/manual/tutorial/query-arrays/) / [$pull](https://www.mongodb.com/docs/manual/reference/operator/update/pull/)

## Solution

<details>
  <summary>Click to expand</summary>

```javascript
db.customers.updateOne(
  { _id: ObjectId("6312d87c9df14eea7e2ca9e4") },
  {
    $pull: {
      orders: ObjectId("6312f4a6f80e3117f621a469")
    }
  },
  { upsert: true }
);

db.customers.updateOne(
  { email: "john@example.com" },
  { $set: { favoriteCategories: [] } },
  { upsert: true }
)


```

### Expected Output

```javascript
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
```

</details>
