# Challenge 4-2 - Deleting Documents

## Challenge

Time to get destructive.

Use the `deleteOne()` and `deleteMany()` and `drop()` methods to remove documents from your customer collection as follows:

1. Begin by using `mongoexport` to make a copy of your `customers` and `orders` collections
1. Delete one user, using their_id
1. Delete all users named "John"
1. Delete every document in the collection
1. Remove the `customers` and `orders` collections from your database

*Note, when you're done, your customers and orders collections will be removed. If you wish to continue practicing with this data set, you will need to re-initialize your database by running the schema created in challenge 1-1 and the `mongoimport` command to reload your exported data from step 1.*

### Hints

> Need a hand? Check out the official documentation: [deleteOne](https://www.mongodb.com/docs/manual/reference/method/db.collection.updateOne/) / [deleteMany](https://www.mongodb.com/docs/manual/reference/method/db.collection.updateMany/) / [drop()](https://www.mongodb.com/docs/manual/reference/method/db.collection.drop/)

## Solution

<details>
  <summary>Click to expand</summary>

```javascript
// Delete one by ID
db.customers.deleteOne({ _id: ObjectId('631131753222f43e15fc0db6') });

// Delete many by name
db.customers.deleteMany({ name: "John" });

// Wipe
db.customers.deleteMany({});

// Nuke
db.customers.drop()
db.orders.drop()
```

### Expected Output

```javascript
{
  acknowledged: true,
  deletedCount: 1
}
```

</details>
