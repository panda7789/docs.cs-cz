### <a name="sqlvariant-data-uses-sqlvariant-collation-rather-than-database-collation"></a>SQL_VARIANT data používá kolaci sql_variant spíše než kolaci databáze

|   |   |
|---|---|
|Podrobnosti|<code>sql_variant</code> používá data <code>sql_variant</code> kolace spíše než kolaci databáze.|
|Návrh|Tato změna řeší poškození dat. Pokud se liší od kolaci databáze <code>sql_variant</code> kolace. Aplikace využívající poškozená data mohou selhat.|
|Rozsah|Transparentní|
|Version|4.5|
|Typ|modul runtime|

