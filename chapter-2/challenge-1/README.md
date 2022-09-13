# Challenge 2-1 - Queries with `find()`

## Challenge

Use find() to run the following queries in the customers collection:

- Active Customers
- Customers whose names start with “J”
- Customers whose email is john@example.com
- The customer whose _id is "6312d9d228cec973e20022ff"

> Need a hand? Check out the [official documentation](https://www.mongodb.com/docs/manual/reference/method/db.collection.find/)

## Solution

<details>
  <summary>Click to expand</summary>

```javascript
db.customers.find({ active: true });
db.customers.find({ email: "john@example.com" })
db.customers.find({ name: /a/ })
db.customers.find({ _id: ObjectId("6312d9d228cec973e20022ff") })

```

### Expected Output

```javascript
[
  {
    _id: ObjectId("6312d9d228cec973e20022ff"),
    name: 'Gene',
    email: 'gene@exmple.com',
    phone: '555-1212',
    active: true,
    customerSince: ISODate("2021-10-30T00:00:00.001Z"),
    favoriteCategories: [ 'sports' ],
    addresses: {
      billing: {
        address: '222 Some Rd',
        city: 'Some Town',
        state: 'FL',
        zip: '12345'
      }
    },
    orders: [ ObjectId("6312f4a6f80e3117f621a468") ]
  },
  {
    _id: ObjectId("6312d87c9df14eea7e2ca9e4"),
    name: 'Zach',
    email: 'zach@example.com',
    phone: '206-555-3333',
    active: true,
    customerSince: ISODate("2022-06-17T00:00:00.000Z"),
    favoriteCategories: [ 'sports' ],
    addresses: {
      billing: {
        address: '123 Main St',
        city: 'Some Town',
        state: 'WA',
        zip: '12345'
      }
    },
    orders: [
      ObjectId("6312f4a6f80e3117f621a46a"),
      ObjectId("6312f4a6f80e3117f621a469")
    ]
  }
]
```

</details>
