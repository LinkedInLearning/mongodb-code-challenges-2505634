# Challenge 1-5 - Import and Export

## Challenge 1

1. Create a JSON file called data.json with an array of at least 5 customer documents to insert into the customers collection.
1. Use `mongoimport` to import these documents into your customers collection from this file.
1. Use `mongoexport` to export your collection data to a JSON file called customers.json

Consider:

- What are the differences in the file you exported vs the file you created for import?

## Challenge 2

1. Use `mongoimport` to import the provided data set called `store-customers.json` `store-orders.json` which contain many additional documents for your database.

> Need a hand? Check out the official documentation: [Import](https://www.mongodb.com/docs/database-tools/mongoimport/) / [Export](https://www.mongodb.com/docs/database-tools/mongoexport/) / [Compass](https://www.mongodb.com/docs/compass/current/import-export/>)

## Solution

<details>
  <summary>Click to expand</summary>

### Import

`mongoimport --uri mongodb://localhost:27017/store --collection customers --type json --jsonArray --file ./data.json`

### Export

`mongoexport --uri mongodb://localhost:27017/store --collection customers --jsonArray --out customers.json`

</details>
