### <a name="change-in-behavior-in-data-definition-language-ddl-apis"></a>Změna v chování v jazyka DDL (Data Definition) rozhraní API

|   |   |
|---|---|
|Podrobnosti|Chování DDL rozhraní API, pokud je zadána AttachDBFilename došlo ke změně následujícím způsobem:<ul><li>Připojovací řetězce nemusí zadejte hodnotu počáteční katalog. Dříve byly požadované AttachDBFilename a počáteční katalog.</li><li>Pokud jsou zadané AttachDBFilename i počáteční katalog a daný soubor MDF existuje, <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> metoda vrátí <code>true</code>. Dříve, vrátí <code>false</code>.</li><li>Pokud jsou zadané AttachDBFilename i počáteční katalog a existuje daný soubor MDF, volání <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> metoda odstraní soubory.</li><li>Pokud <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> je volána, když připojovací řetězec Určuje hodnotu AttachDBFilename s MDF, který neexistuje a počáteční katalog, který neexistuje, vyvolá metoda <xref:System.InvalidOperationException> výjimka. Dříve, došlo <xref:System.Data.SqlClient.SqlException> výjimka.</li></ul>|
|Návrh|Tyto změny můžete usnadnit vytvořením nástrojů a aplikací, které používají rozhraní API DDL. Tyto změny mohou ovlivnit kompatibilitu aplikací v následujících situacích:<ul><li>Uživatel zapíše kód, který provede <code>DROP DATABASE</code> příkaz přímo místo volání <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> Pokud <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> vrátí <code>true</code>. Tím je prolomen existující kód, pokud není databáze připojena, ale existuje soubor MDF.</li><li>Uživatel zapíše kód, který se očekává <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> metoda k vyvolání <xref:System.Data.SqlClient.SqlException> místo <xref:System.InvalidOperationException> při počáteční katalog a MDF soubor neexistují.</li></ul>|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|modul runtime|

