# Challenge 1-3 - Insert Multiple Documents

## Challenge

1. Create an array of at least 5 customer documents to insert into the customers collection.
1. Use the `insertMany()` method from within `mongosh`  to import these documents into your customers collection from this array, using a loop to process the array

Consider:

- What does {ordered:false} do for you?
- How do unique indexes help us?

### Hints

- Note the use of unordered to let you try again and skip the duplicate inserts.
- Make sure you have a unique key!

> Need a hand? Check out the [official documentation](https://www.mongodb.com/docs/manual/reference/method/db.collection.insertMany/)

## Solution

<details>
  <summary>Click to expand</summary>

### Insert a record, with error trapping

```javascript
customers = [
  {
    name: "Cathy",
    email: "cathy@example.com",
    phone: "206-555-2222",
    active: true,
    customerSince: ISODate("2021-09-12"),
    favoriteCategories: ["food"],
    orders: [],
    addresses: {
      shipping: {
        address: "123 Main St",
        city: "Some Town",
        state: "WA",
        zip: "12345"
      },
      billing: {
        address: "123 Bank St",
        city: "Some Town",
        state: "WA",
        zip: "12345"
      }
    }
  },
  {
    name: "Zach",
    email: "zach@example.com",
    phone: "206-555-3333",
    active: true,
    customerSince: ISODate("2022-06-17"),
    favoriteCategories: ["sports"],
    orders: [],
    addresses: {
      shipping: {
        address: "123 Main St",
        city: "Some Town",
        state: "WA",
        zip: "12345"
      }
    }
  },
  {
    name: "Allie",
    email: "allie@example.com",
    phone: "206-555-4444",
    active: true,
    customerSince: ISODate("2022-02-09"),
    favoriteCategories: ["clothing"],
    orders: [],
    addresses: {
      billing: {
        address: "555 Business St",
        city: "Some Town",
        state: "WA",
        zip: "12345"
      },
      shipping: {
        address: "123 Main St",
        city: "Some Town",
        state: "WA",
        zip: "12345"
      }
    }
  }
];

try {
  db.customers.insertMany( customers, { ordered: false });
} catch (e) {
  print("Something went wrong");
  print(e);
}

```

### Expected Output

```javascript
{
  acknowledged: true,
    insertedIds: {
    '0': ObjectId("63154085b1a6c353aaf3f194"),
    '1': ObjectId("63154085b1a6c353aaf3f195"),
    '2': ObjectId("63154085b1a6c353aaf3f196")
  }
}
```

</details>
