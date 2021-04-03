---
layout: post
title:  Reorganize table w/o PL/SQL
date:   2021-03-27 00:00:00 +0800
categories: Database
tag: SQL
---
When it comes to reorganize tables in Oracle database to achieve normalization in relationship, there could be different strategies, mostly depending on the type of relation between tables.
<br>
For LUT, either use distinct selection to create a new table directly, or put the selection in the cursor and loop to directly insert values.
<br>
For scenarios like below, there should be a selection of the top ranked entries, plus a further LUT filter. 
<hr>
#### Snippet of Unnormalized Data
![Snippet of Unnormalized Data]({{ '/styles/images/20210327_01.png' | prepend: site.baseurl  }})
<br>
<br>
For each property, there could be multiple purchases or assessment. The data has been grouped on property ID and ordered by descending dates.
<br>
Now we need to extract a LUT for the names who are the current owners(rank top for each property).
<br>
#### PL/SQL
Whenever a new property ID is identified, it means the corresponding dates are the latest ones and the owner name is a qualified candidate for the table of current owners.
```
For row IN cursor LOOP
    SELECT COUNT(*) INTO cnt_prop
    FROM property
    WHERE prop_id LIKE row.prop_id;
    
    IF cnt_prop = 0 THEN
        SELECT COUNT(*) INTO cnt_ow
        FROM owner
        WHERE name LIKE row.name;
        
        IF cnt_ow = 0 THEN
        ...
```
#### SQL
It could be done by using SQL only, but the amount of tweaking makes it less efficient than in other circumstances.
```
CREATE TABLE owner2 AS
    SELECT DISTINCT a.prop_id, name, address, city, province, pcode, phone FROM assn3 a
    WHERE purchase_date = (SELECT MAX(purchase_date)   FROM assn3 b WHERE b.prop_id = a.prop_id)
        AND
        assessment_date = (SELECT MAX(assessment_date) FROM assn3 b WHERE b.prop_id = a.prop_id);
ALTER TABLE owner2 DROP COLUMN prop_id;
...
```



