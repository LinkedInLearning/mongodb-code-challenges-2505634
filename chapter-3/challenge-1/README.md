# Challenge 3-1 - Updating Documents

## Challenge

Use the `updateOne()` and `updateMany()` methods to alter selected documents in the customers collection as follows:

1. Change one users phone number, using their `_id`
1. Set the active status of all users named "John" to false
1. Perform an insert of a new user using `updateOne()` with the `upsert` flag.
1. Repeat the command, but change a bit of data for the user.

Consider

- Does mongo update the user you just added or create a new one?

### Hints

> Need a hand? Check out the official documentation [updateOne](https://www.mongodb.com/docs/manual/reference/method/db.collection.updateOne/) / [updateMany](https://www.mongodb.com/docs/manual/reference/method/db.collection.updateMany/)

## Solution

<details>
  <summary>Click to expand</summary>

```javascript
// For IDs, use ObjectId('xxxx')
db.customers.updateOne({ _id: ObjectId('63110bb025460cc0c55f6c65') }, { $set: { phone: "555-8888" } })

// For any field (usually for updating multiple entries, just specify it)
db.customers.updateMany({ name: "John" }, { $set: { active: false } })

// Upsert
// Run this multiple times, changing values. The first time, it'll insert. Thereafter, it'll update instead.
db.customers.updateOne(
  { email: "johnc@example.com" },
  {
    $set: {
      name: "Johnny",
      email: "johnc@example.com",
      phone: "555-6363",
      active: false,
      customerSince: ISODate("2022-09-01"),
      orders: []
    }
  },
  { upsert: true }
)

```

### Expected Output

```javascript
{ acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 0,
  upsertedCount: 0
}
```

</details>
