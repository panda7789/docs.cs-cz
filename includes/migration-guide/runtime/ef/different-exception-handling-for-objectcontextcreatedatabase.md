### <a name="different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a>Zpracování metody ObjectContext.CreateDatabase a DbProviderServices.CreateDatabase různých výjimek

|   |   |
|---|---|
|Podrobnosti|Počínaje .NET Framework 4.5, pokud se vytváření databáze nezdaří, <code>CreateDatabase</code> metody se pokusí zrušit prázdnou databázi. Pokud operace proběhne úspěšně, původní <xref:System.Data.SqlClient.SqlException?displayProperty=name> se rozšíří (místo <xref:System.InvalidOperationException?displayProperty=name> , která byla vždy vyvolána v rozhraní .NET Framework 4.0)|
|Návrh|Při zachytávání <xref:System.InvalidOperationException?displayProperty=name> při provádění <xref:System.Data.Objects.ObjectContext.CreateDatabase> nebo <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)>, SQLExceptions by měl nyní také být zachycena.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)?displayProperty=nameWithType></li></ul>|

