# Challenge 3-2 - Updating array values in documents

## Challenge

Use the `updateOne()` method to alter an array with selected documents in the customers collection as follows:

1. Add a valid value to the end favoriteCategories array for a single user, using their email address as the `find({})` source.
1. Add another valid value to the beginning of the favoriteCategories array for a single user, using their email address as the `find({})` source.

Consider

- What happens when you try and push a value that's not part of the `enum`?
- How would you handle this?

### Hints

> Need a hand? Check out the official documentation: [Updating Arrays](<https://www.mongodb.com/docs/manual/reference/operator/update-array/>) / [$push](https://www.mongodb.com/docs/manual/reference/operator/update/push/) / [querying arrays](https://www.mongodb.com/docs/manual/tutorial/query-arrays/)

## Solution

<details>
  <summary>Click to expand</summary>

```javascript
db.customers.updateOne(
  { email: "john@example.com" },
  {
    $push: {
      favoriteCategories: "sports"
    }
  },
  { upsert: true }
)
```

```javascript
db.customers.updateOne(
  { email: "john@example.com" },
  {
    $push: {
      favoriteCategories: {
        $each: ["food"],
        $position: 0
      }
    }
  },
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
