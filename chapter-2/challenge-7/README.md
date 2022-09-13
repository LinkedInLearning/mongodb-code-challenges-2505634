# Challenge 2-7 - `$and` and `$or`

## Challenge

Use find() along with any required query operators to run the following queries in the customers collection, returning only the customers name, email, and phone number

1. All active customers whose name starts with "J" (do not use `$and:{}`)
1. All customers who have a shipping address with a different state from their billing address.
   - (Hint: you’ll need to use both `$and:{}` and an `$expr:{}` to solve this one!)
1. Customers who are either inactive or who have joined after September 1, 2022 and have not yet placed an order

### Hints

> Need a hand? Check out the official documentation: [$and](https://www.mongodb.com/docs/manual/reference/operator/query/and/) / [$or](https://www.mongodb.com/docs/manual/reference/operator/query/or/)

## Solution

<details>
  <summary>Click to expand</summary>

### Challenge Question 1

```javascript
// Challenge 1
db.customers.find({ name: /^J/, active: true }, {name:1, phone: 1, _id:0})

// Output:
[
  { name: 'Josie', phone: '555-1212' }
]
```

### Challenge Question 2

```javascript
db.customers.find(
  {
    $and: [
      { "addresses.shipping": { $exists: true } },
      { "addresses.billing": { $exists: true } },
      { $expr: { $ne: ["$addresses.billing.state", "$addresses.shipping.state"] } }
    ]
  },
  { name: 1, "addresses.billing.state": 1, "addresses.shipping.state": 1, _id: 0 }
)

// Output:
[
  {
    name: 'John',
    addresses: { billing: { state: 'NJ' }, shipping: { state: 'WA' } }
  },
  { name: 'Rosie', addresses: { shipping: { state: 'WA' } } },
  { name: 'Luna', addresses: { shipping: { state: 'WA' } } }
]
```

### Challenge Question 3

```javascript
db.customers.find({
  $or: [
    { active: false },
    {
      $and: [
        { customerSince: { $gte: ISODate("2022-09-01") } },
        { orders: { $size: 0 } }
      ]
    }
  ]
}, { _id: 0, name: 1, active: 1 })

// Output
[
  { name: 'John', active: false },
  { name: 'Cathy', active: true }
]
```

</details>
