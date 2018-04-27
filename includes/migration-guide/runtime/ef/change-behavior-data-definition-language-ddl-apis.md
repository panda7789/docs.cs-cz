### <a name="change-in-behavior-in-data-definition-language-ddl-apis"></a>Změna v chování v jazyka DDL (Data Definition) rozhraní API

|   |   |
|---|---|
|Podrobnosti|Chování DDL rozhraní API, pokud je zadána AttachDBFilename došlo ke změně následujícím způsobem:<ul><li>Připojovací řetězce nemusí zadejte hodnotu počáteční katalog. Dříve byly požadované AttachDBFilename a počáteční katalog.</li><li>Pokud jsou zadané AttachDBFilename i počáteční katalog a existuje daný soubor MDF, ObjectContext.DatabaseExists metoda vrátí hodnotu true. Dříve vrátila hodnotu false.</li><li>Pokud jsou zadané AttachDBFilename i počáteční katalog a existuje daný soubor MDF, voláním metody ObjectContext.DeleteDatabase odstraní soubory.</li><li>Pokud ObjectContext.DeleteDatabase je volána, když připojovací řetězec Určuje hodnotu AttachDBFilename s MDF, který neexistuje a počáteční katalog, který neexistuje, vyvolá metoda výjimku výjimkou InvalidOperationException. Dříve došlo k výjimce SqlException.</li></ul>|
|Návrh|Tyto změny můžete usnadnit vytvořením nástrojů a aplikací, které používají rozhraní API DDL. Tyto změny mohou ovlivnit kompatibilitu aplikací v následujících situacích:<ul><li>Uživatel zapíše kód, který spouští příkaz DROP DATABASE přímo namísto volání ObjectContext.DeleteDatabase Pokud ObjectContext.DatabaseExists vrací hodnotu true. Tím je prolomen existující kód, pokud není databáze připojena, ale existuje soubor MDF.</li><li>Uživatel zapíše kód, který očekává ObjectContext.DeleteDatabase metoda k vyvolání výjimky SqlException spíše než výjimku InvalidOperationException při počáteční katalog a MDF soubor neexistují.</li></ul>|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|

