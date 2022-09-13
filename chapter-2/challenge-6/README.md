# Challenge 2-6 - Querying Arrays

## Challenge

Use find() along with any required query operators to run the following queries in the customers collection, returning only the customers name, email, and phone number

1. All customers that have not yet placed an order
1. All customers that do not yet have a favorite categories list
1. All customers whose favorite category is "sports"
   - try this one using a straight match as well as with the $elemMatch query operator

### Hints

> Need a hand? Check out the official documentation = [Querying Arrays](https://www.mongodb.com/docs/manual/tutorial/query-arrays/) / [$size operator](https://www.mongodb.com/docs/manual/reference/operator/query/size/)

## Solution

<details>
  <summary>Click to expand</summary>

```javascript
// No orders placed (size 0)
db.customers.find({ orders: { $size: 0 } }, { _id: 0, name: 1 })

// No favorite categories defined
db.customers.find({ favoriteCategories: { $exists: false } }, { _id: 0, name: 1 })

// Array contains a value, 2 ways
db.customers.find({ favoriteCategories: 'sports' });
db.customers.find({ favoriteCategories: { $elemMatch: { $eq: 'sports' } } }, { _id: 0, name: 1 })
```

### Expected Output

```javascript
```

</details>
