### <a name="sqlvariant-data-uses-sqlvariant-collation-rather-than-database-collation"></a>SQL_VARIANT data používá kolaci sql_variant spíše než řazení databáze

|   |   |
|---|---|
|Podrobnosti|<code>sql_variant</code> použití dat <code>sql_variant</code> spíše než řazení databáze.|
|Návrh|Tato změna adresuje možné poškození dat, pokud se řazení databáze liší od <code>sql_variant</code> kolace. Aplikace využívající poškozená data mohou selhat.|
|Rozsah|Transparentní|
|Version|4.5|
|Typ|Modul runtime|

