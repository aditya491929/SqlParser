# SqlParser RDBMS IA2 #
#####  Name: Aditya Malwade #####
##### RollNo: 1911091 #####
##### Batch: B2 #####
## INSTALL ##
* FROM npmjs : 
``` bash 
npm install node-sql-parser --save 
```
* FROM browser :
``` bash
<script src="https://unpkg.com/node-sql-parser/umd/index.umd.js"></script>
 
<script src="https://unpkg.com/node-sql-parser/umd/mysql.umd.js"></script>
 
<script src="https://unpkg.com/node-sql-parser/umd/postgresql.umd.js"></script> 
```
## CREATE AST FOR SQL STATEMENT ##
``` bash
const { Parser } = require('node-sql-parser');
const parser = new Parser();
const ast = parser.astify('SELECT * FROM t'); // mysql sql grammer parsed by default
console.log(ast);
```
eg: ast for SELECT * FROM t
``` bash
{
  "with": null,
  "type": "select",
  "options": null,
  "distinct": null,
  "columns": "*",
  "from": [
    {
      "db": null,
      "table": "t",
      "as": null
    }
  ],
  "where": null,
  "groupby": null,
  "having": null,
  "orderby": null,
  "limit": null
}
```
## Get the SQL visited tables: ## 
* get the table list that the sql visited
* the format is {type}::{dbName}::{tableName} // type could be select, update, delete or insert

## Get the SQL visited columns ##
* get the column list that the sql visited
* the format is {type}::{tableName}::{columnName} // type could be select, update, delete or insert
* for select *, delete and insert into tableName values() without specified columns, the .* column authority regex is required
