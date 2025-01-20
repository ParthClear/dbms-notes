  **SQL** : You tell oracle which information you want it to **_select, insert, update, delete._**

  **select and from**: query example: 
select _birthday_ from _classmates_; 
 You will use 4 primary keywords while selecting information from an table: **select, from, where, order by**

  **Where**: Use of this keyword must be followed by one or more logical tests with AND, or  OR , the logical connectors.  The preference for AND > OR.

 ![file attached](IMG-20231010-WA0007.jpg) (file attached)

 Logical Test against **single values**: 

1. _comparators:_ =,>=,<=,^=,!=,<> 
2. _pattern matching_: **LIKE**  'M_o%g' , % is any number of any characters, _ is 1 character.
3. _IS NULL, IS NOT NULL_: special comparators for checking equivalence with NULL. Comparators wont work

 ![file attached](IMG-20231010-WA0009.jpg) (file attached)

Logical Tests against a **List of values**:
 Logical Test against List of Values:
IN,
NOT IN, 
BETWEEN 9 AND 10,
BETWEEN 'A' AND 'D', 
NOT BETWEEN 6 AND 9 

  **order by**: orders the results. this keyword should be followed by one or more column names(comma separated), each followed by **asc** (default) or **desc**. Sorting priority followed from left to right. (high to low)
 ![file attached](IMG-20231010-WA0012.jpg) (file attached)
 Some notes about using subqeuries with operators
 One query to rule them all , of that which has been taught till now:
 create or replace view abctest as 

 **select**  
    "EMPNO", 
    "ENAME", 
    "JOB",
    "DEPTNO" 
from "EMP" 
 **where**  
    ename > 'A'  
    and ename <= 'D' 
    or deptno IN  
    ( **select** deptno  
    from dept  
    **where** dname LIKE 'A%' 
    or deptno BETWEEN 0 and 10 
    ) **order by** ename, job desc 

 Views are **dynamic**, and always reflect data present in the actual tables

 Data types in Oracle: NUMBER, CHAR, DATE, VARCHAR2, LONG, RAW, LONG RAW.

 ![file attached](IMG-20231010-WA0014.jpg) (file attached)

String functions

 some example and usage for understanding

 ![file attached](IMG-20231010-WA0022.jpg) (file attached)
 ![file attached](IMG-20231010-WA0027.jpg) (file attached)
 ![file attached](IMG-20231010-WA0024.jpg) (file attached)
 ![file attached](IMG-20231010-WA0023.jpg) (file attached)
 ![file attached](IMG-20231010-WA0028.jpg) (file attached)
 ![file attached](IMG-20231010-WA0026.jpg) (file attached)
 ![file attached](IMG-20231010-WA0025.jpg) (file attached)
 ![file attached](IMG-20231010-WA0033.jpg) (file attached)

Functions for NUMBER data type:

 ![file attached](IMG-20231010-WA0034.jpg) (file attached)

 group value functions are invariant to NULL values and ignore them.

 **SysDate** shows todays date. ex. select SysDate from DUAL;

 ![file attached](IMG-20231010-WA0036.jpg) (file attached)
 ![file attached](IMG-20231010-WA0038.jpg) (file attached)

 Understanding groups

 ![file attached](IMG-20231010-WA0040.jpg) (file attached)
 ![file attached](IMG-20231010-WA0042.jpg) (file attached)

for above query

 having can be used when filter is based on calculated group function like sum, avg , efc.

 putting double quotation  marks around aliases, forces oracle to store and match the name in mixed case. So the alias will become case sensitive. By default when no quotation marks are present all names are stores in  upper case 
 
 ![file attached](IMG-20231010-WA0045.jpg) (file attached)

 **Example of a list of Columns being compared at once in a where clause**

 when we use the test say , W.lodging = lodging , We exclude all rows with lodging NULL in our results

 to avoid this use: NVL(W.lodging,'whatever') = NVL(lodging,'whatever') 

 this query also excludes rows with null values as the **IN** keyword ignores NULL values

 Note for correlated subqueries: 

sql chooses the variable related to the _closest_ select statement

 ![file attached](IMG-20231010-WA0047.jpg) (file attached)

 truncate command cannot be rolled back or commited

 **update** COMFORT **set** Midnight = Midnight + 1, Noon = 20.5, Sampledat = _value/subquery_ 

 **where** City = _value/subquery_

 ![file attached](IMG-20231010-WA0049.jpg) (file attached)

also possible

 **candidate key** : any combination of 1 or more columns, the values of which uniquely identify the table 

 **primary key**: a candidate key which cannot have a null value. Only one primary key is possible for a table

 **create table** _tablename_ (
 _columnname_ _datatype_ _constraints_,...,
 _contstraints_(columnname1,columnname2,...),...
); 

 **constraints** -
UNIQUE ,
CHECK,
NOT NULL,
PRIMARY KEY,
FOREIGN KEY

 **drop table** _tablename_;

 **alter table** _tablename_ **add/modify** ( _columnname datatype constraint, .._ )

 **Triggers** :

** Row level Triggers : executed once for each row into transaction

** Statement-Level Triggers : executes once for each transaction

 **Triggers:**

**create or replace** trigger _triggername_

**before / after** 

**delete / insert / update**

**on** _tablename_

**for each row** 

**when** _condition_

**begin**

**end**

 ![file attached](IMG-20231011-WA0006.jpg) (file attached)
 Normal forms:
 ![file attached](IMG-20231012-WA0010.jpg) (file attached)
 In the first normal form each field contains a single value. A field may not contain a set of values or a nested record.
 ![file attached](IMG-20231012-WA0009.jpg) (file attached)
 2NF: every non-candidate-key attribute depends on the whole candidate key
 ![file attached](IMG-20231012-WA0008.jpg) (file attached)
 ![file attached](IMG-20231012-WA0007.jpg) (file attached)
 BCNF acts differently from 3NF only when there are multiple overlapping candidate keys.
 ![file attached](IMG-20231012-WA0006.jpg) (file attached)
 **Procedures**
 ![file attached](IMG-20231012-WA0012.jpg) (file attached)
 ![file attached](IMG-20231012-WA0014.jpg) (file attached)
 Cursors

 https://www.reddit.com/r/explainlikeimfive/comments/dyheyc/eli5_normal_form_in_databases/
 **1NF**
 Each column stores one value

**2NF**
1. it is in 1NF
2. It does not contain any partial dependencies.

**3NF** 
1. It is 2NF
2. No non prime attributes has any transitive dependency on primary key

 _every_ non-key _attribute_ must provide a fact about **the key** , **the whole key** , and **nothing but the key**
