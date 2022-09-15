# Challenge 2-4 - Query Operators

## Challenge

Use find() along with proper query operators to run the following queries in the customers collection, returning only the customers name, email, and phone number

1. All customers that have joined on or after March 1, 2021
1. Active customers whose names are "John" or "Cathy" using the $ in query operator

### Hints

Query Operator Syntax:

```javascript
{
  field: { $operator: <thing> }
}
```

> Need a hand? Check out the [official documentation](https://www.mongodb.com/docs/manual/reference/operator/query/)

## Solution

<details>
  <summary>Click to expand</summary>

```javascript
// Customers that have joined since 9/1/2021
db.customers.find({ customerSince: { $gte: ISODate('2022-03-01') } })

// Active customers named john or cathy
db.customers.find({ active: true, name: { $in: ["John", "Cathy"] } })

```

### Expected Output

```javascript
[
  {
    _id: ObjectId("6312d87c9df14eea7e2ca9e3"),
    name: 'Cathy',
    email: 'cathy@example.com',
    phone: '206-555-2222',
    active: true,
    customerSince: ISODate("2021-09-12T00:00:00.000Z"),
    favoriteCategories: [ 'food', 'sports', 'clothing' ],
    addresses: {
      shipping: {
        address: '123 Main St',
        city: 'Some Town',
        state: 'WA',
        zip: '12345'
      },
      billing: {
        address: '123 Bank St',
        city: 'Some Town',
        state: 'WA',
        zip: '12345'
      }
    },
    orders: [
      ObjectId("6312eec6f80e3117f621a463"),
      ObjectId("6312eed4f80e3117f621a464")
    ]
  }
]
```

</details>
