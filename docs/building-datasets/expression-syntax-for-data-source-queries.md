---
title: 'Expression Syntax for data source queries'
---

# Expression Syntax for data source queries

## Basic Structure

```
{
  variableName: dataSourceName {
    dataSourceName_data (filter: "ColumnName1 = "Some product name"",sort: "ColumnName1",order: "asc",skip: 5,top: 1) {
      items {
        ColumnName1
      }
    }
  }
}
```

## Expressions

### For Files

#### Filter

Values | Description
--- | ---
43, -1.234 | Numbers
"hello" | String

Comparisons | Description
--- | ---
x = y | Equals
x != y | Does not equal
x < y | Less than
x <= y | Less than or equal to
x > y | Greater than
x >= y | Greater than or equal to
x ~= y | Regular expression match (case insensitive)

Boolean logic | Description
--- | ---
x or y | Boolean or
x and y | Boolean and
not x | Boolean not
( x ) | Explicity operator precedence

Operator precedence follows that of any sane language.

##### Examples

```
(filter: "ColumnName1 = "Some product name"")
(filter: "ColumnName1 >= 100.5 and ColumnName2 <= 300")
(filter: "ColumnName1 ~= "some"")
(filter: "ColumnName1 = 1")
(filter: "ColumnName1 = false")
(filter: "ColumnName1 = "Some product" and (ColumnName2 = "Appliances" or ColumnName3 = "Electronics")")
```


#### Sort

Values | Description
--- | ---
"ColumnName" | String

##### Examples

```
(sort: "ColumnName1")
```

#### Order

Values | Description
--- | ---
"asc" | Ascending
"desc" | Descending

##### Examples

```
(order: "asc")
(order: "desc")
```

#### Skip

Values | Description
--- | ---
43, -1.234 | Numbers

##### Examples

```
(skip: 5)
(skip: 1000)
```

#### Top

Values | Description
--- | ---
43, -1.234 | Numbers

##### Examples

```
(top: 1)
(top: 5)
```

## Expressions for other data sources

Those expressions are used, that the data source supports by default.