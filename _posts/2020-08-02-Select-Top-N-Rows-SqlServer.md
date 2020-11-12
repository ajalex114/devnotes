---
title:  "Select Top N Rows from a table in Sql Server" 
categories: [dev]
description: Select Top N Rows from a table in Sql Server
tags: [sql]
--- 

Selecting Top 10 rows is easy. Just do  
``` sql
SELECT TOP 10 * FROM PERSON
```

But what if the number of rows you want to get is dynamic? What if you have a variable `N` for the number of rows to return?  
Try this

``` sql
DECLARE @count INT = 5

SELECT *
FROM <<Table>>
WHERE <condition>
ORDER BY <<column>>
OFFSET 0 ROWS
FETCH FIRST @count ROWS ONLY
```

Hope this helped.

--------------------------

<a align="left" href="https://www.buymeacoffee.com/ajalex" target="_blank">
<img src="{{ "/assets/img/Logos/buymeacoffee-blue.png"  | relative_url }}" alt="Buy me a coffee" align="left" style="height: 60px !important;width: 217px !important;"/>
</a>  

--------------------------
