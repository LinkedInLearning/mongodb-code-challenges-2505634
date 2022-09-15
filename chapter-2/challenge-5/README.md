# Challenge 2-5 - Querying Embedded Objects

## Challenge

Use find() along with any required query operators to run the following queries in the customers collection, returning only the customers name, email, and phone number

1. All customers that do not have a shipping address
1. All customers whose billing address is in the state of Florida ("FL'")
1. All customers who have a shipping address with a different state from their billing address.
   - (Hint: you'll need to use an `$expr` to solve this one!)

### Hints

> Need a hand? Check out the official documentation: [Embedded Documents](https://www.mongodb.com/docs/manual/tutorial/query-embedded-documents/) / [$expr](https://www.mongodb.com/docs/manual/reference/operator/query/expr/)

## Solution

<details>
  <summary>Click to expand</summary>

```javascript
db.customers.find({ "addresses.shipping": { $exists: false } })

db.customers.find({ "addresses.billing.state": "FL" })

db.customers.find(
  {
    "addresses.shipping": { $exists: true },
    $expr: { $ne: ["$addresses.billing.state", "$addresses.shipping.state"] }
  },
  { name: 1, "addresses.billing.state": 1, "addresses.shipping.state": 1, _id: 0 }
)


```

### Expected Output

Challenge Question 3 Sample Output:

```javascript
[
  {
    name: 'Cathy',
    addresses: { shipping: { state: 'WA' }, billing: { state: 'WA' } }
  },
  {
    name: 'Allie',
    addresses: { shipping: { state: 'WA' }, billing: { state: 'WA' } }
  }
]
```

</details>
