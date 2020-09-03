# MongoDB Cheat Sheet

## Create DB

### Show All Databases

```
show dbs
```

### Show Current Database

```
db
```

### Create Or Switch Database

```
use Météo
```

### Drop

```
db.dropDatabase()
```

### Create Collection

```
db.createCollection('météo')
```

### Show Collections

```
show collections
```

## CREATE

### Insert Row

```
db.météo.insert({
  ville: "Bruxelles",
  haut: 27,
  bas: 13,
})
```

### Insert Multiple Rows

```
db.météo.insertMany([
  {
  ville: "Bruxelles",
  haut: 27,
  bas: 13,
  },
  {
    ville: "Liège",
    haut: 25,
    bas: 15,
  },
  {
    ville: "Namur",
    haut: 26,
    bas: 15,
  },
  {
    ville: "Charleroi",
    haut: 25,
    bas: 12,
  },
  {
    ville: "Bruges",
    haut: 28,
    bas: 16,
  },
]);
```

## READ

### Get All Rows

```
db.météo.find()
```

### Get All Rows Formatted

```
db.météo.find().pretty()
```

### Find Rows

```
db.météo.find({ haut: { $eq: 26  } }).pretty()
```

### Sort Rows

###### ASC

```
db.météo.find().sort({ ville: 1 }).pretty()
```

###### DESC

```
db.météo.find().sort({ ville: -1 }).pretty()
```

### Count Rows

```
db.météo.find().count()
db.météo.find({ bas: { $lte: 14 } }).count()
```

### Limit Rows

```
db.météo.find().limit(2).pretty()
```

### Chaining

```
db.météo.find().limit(2).sort({ ville: -1 }).pretty()
```

### Foreach

```
db.météo.find().forEach(function(doc) {
  print("Ville : " + doc.ville)
})
```

## UPDATE

### Update Row

```
db.météo.update({ ville: 'Charleroi' },
{
  ville: 'Charleroi',
  haut: 27,
  bas: 14
})
```

### Update Specific Field

```
db.météo.update({ ville: 'Bruxelles' },
{
  $set: {
    haut: 25,
    bas: 11
  }
})
```

### Increment Field (\$inc)

```
db.météo.update({ ville: 'Namur' },
{
  $inc: {
    bas: 3
  }
})
```

## DELETE

### Delete Row

```
db.météo.remove({ ville: 'Namur' })
```

## TEXT

### Add Index

```
db.météo.createIndex({ ville: 'text' })
```

### Text Search

```
db.météo.find({
  $text: {
    $search: "Bru"
    }
})
```
