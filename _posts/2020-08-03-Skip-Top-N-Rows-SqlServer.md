---
title:  "Skip Top N Rows from a table in Sql Server" 
categories: [dev]
description: Skip Top N Rows from a table in Sql Server
tags: [sql]
--- 

What if you want to skip Top `N` rows while doing a `select` statement in `sql server`?
Try this

``` sql
DECLARE @count INT = 5

SELECT *
FROM <<Table>>
WHERE <condition>
ORDER BY <<column>>
OFFSET @count ROWS
```

Hope this helped.

--------------------------

<a align="left" href="https://www.buymeacoffee.com/ajalex" target="_blank">
<img src="{{ "/assets/img/Logos/buymeacoffee-blue.png"  | relative_url }}" alt="Buy me a coffee" align="left" style="height: 60px !important;width: 217px !important;"/>
</a>  

--------------------------
