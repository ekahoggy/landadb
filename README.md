# Landa DB

Mysql PDO CRUD library from Cahkampung

## Installation

Install with [Composer](http://getcomposer.org/)

Add `cahkampung/landa-db` to require in composer.json

`"require": { "cahkampung/landa-db": "^1.0" },`

Run `composer install`

## How To Use

### Insert

`$db->insert(TABLE_NAME, DATA);`

Example : 
```
$data = [
  'name' => 'john',
  'email' => 'john@example.com'
];

$db = new Cahkampung\LandaDB;
$db->insert('user_table', $data);
```

### Update

`$db->update(TABLE_NAME, DATA, PARAMS);`

Example : 
```
$data = [
  'name' => 'john',
  'email' => 'john@example.com'
];

$db = new Cahkampung\LandaDB;
$db->update('user_table', $data, ['id' => 1]);
```
### Delete

`$db->delete(TABLE_NAME, PARAMS);`

Example :
```
$db = new Cahkampung\LandaDB;
$db->delete('user_table', ['id' => 1]);
```

### Select ###

#### select() ####

`select(FIELDS)`

*FIELDS* can be array format, default value is `*`

#### from() ####

`from(TABLE)`

#### where() ####

`where(FIELD_NAME, FILTER, VALUE)`

#### andWhere() ####

`andWhere(FIELD_NAME, FILTER, VALUE)`

#### orWhere() ####

`andWhere(FIELD_NAME, FILTER, VALUE)`

#### customWhere() ####

`customWhere(WHERE_STRING, FILTER)`

Default filter is `And` 

Example : 

`customWhere('name = "john" or nationallity = "indonesia"', 'AND');`

Same as `AND (name="john" or nationallity="indonesia");`

#### join() ####

`join(JOIN TYPE, TABLE, ONCLAUSE)`

#### leftJoin() ####

`leftJoin(TABLE, ONCLAUSE)`

#### rightJoin() ####

`rightJoin(TABLE, ONCLAUSE)`

#### innerJoin() ####

`innerJoin(TABLE, ONCLAUSE)`

#### limit() ####

`limit(INT)`

#### offset() ####

`offset(INT)`

#### orderBy() ####

`orderBy(FIELD)`

#### groupBy ####

`groupBy(FIELD)`

#### findAll() ####

Fetch all result results from query

Example :
```
$db = new Cahkampung\LandaDB;
$db->findAll('select * from user_table where name like "%john%" order by name ASC limit 10 offset 0');
```
Or
```
$db = new Cahkampung\LandaDB;
$db->select()
    ->from('user_table')
    ->where('name','LIKE','john')
    ->limit(10)
    ->offset(0)
    ->orderBy('name ASC')
$getUsers = $db->findAll();
```

#### find() ####

Fetch 1 results from query

Example :
```
$db = new Cahkampung\LandaDB;
$db->find('select * from user_table where name like "%john%" order by name ASC');
```
Or 
```
$db = new Cahkampung\LandaDB;
$db->select()
    ->from('user_table')
    ->where('name','LIKE','john')
    ->orderBy('name ASC')
$getUsers = $db->find();
```

