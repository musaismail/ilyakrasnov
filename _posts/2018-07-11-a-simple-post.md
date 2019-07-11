---
layout: post
title: שנצליח
author: dan_urbanowicz
date: 2018-07-11T00:12:57.000Z
intro_paragraph: והפעם- בואו נדבר על ```pivot table```
categories: ''
---
**הבעיה שלנו היא ש...**

כולנו מכירים את האפשרות המדהימה באקסל להפוך שורות לעמודות באמצעות ```pivot table```. ב-```MySql``` בניגוד ל-```Databases``` אחרים אין את הפקודה ```Pivot```, אז איך נוכל לעשות את זה בכל זאת? 

**הטיפ שלי**

סוד ההצלחה במקרה הזה טמון בפונקציות אגרגציה על מקרים של ```case```. כלומר, נבחר איזה אגרגציה אנחנו רוצים לעשות ועל איזה מקרה.
במידה ומדובר בערכים מסוג varchar נשתמש בפונקציות האגרגציה ```max/min```.

{% gist 79f97eee6395fc987f3fcd6dcc02628f %}

**בואו ננסה את זה בפועל**

הטבלה שלנו:  
|name|occupation|
|---|---|
|'Naama'| 'Teacher'|
|'Yael'| 'Seller'|
|'Efrat'| 'Seller'|
|'Bar'| 'Programmer'|
|'Sagit'| 'Programmer'|
|'Noam'| 'Teacher'|
|'David'| 'Seller'|
|'Aviv'|'Teacher'|
|'Pnina'| 'Programmer'|
|'Shosh'|'Baker'|


הפקודות שנבצע:

{% gist 7e06b833a3af9ba7a9846faa52bfce96 %}

תוצאה:

|Programmer| Teacher| Seller| Backer|
|---|---|---|---|
|'Bar'|'Aviv'|'David'v'Shosh'|
|'Pnina'|'Naama'|'Efrat'|NULL|
|'Sagit'|'Noam'|'Yael'|NULL|


נוצרה לנו טבלה חדשה המציגה את המקצועות כעמודות ואת שמות האנשים בשורות. ניתן לראות כי בכל אחד מהמקצועות ישנם 3 אנשים בתפקיד מלבד אופה. ולכן, בשורות שמתחת לשמה של האופה היחידה מופיע ```NULL```.


והברכה שלי אליכם..


