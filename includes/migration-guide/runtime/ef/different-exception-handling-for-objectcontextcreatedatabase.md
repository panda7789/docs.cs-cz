### <a name="different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a>Zpracování pro metody ObjectContext.CreateDatabase a DbProviderServices.CreateDatabase různých výjimek

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET 4.5, v případě selhání vytvoření databáze <code>CreateDatabase</code> metody se pokusí o odpojení prázdná databáze. Pokud tuto operace úspěšná, původní <xref:System.Data.SqlClient.SqlException?displayProperty=name> se rozšíří (místo <xref:System.InvalidOperationException?displayProperty=name> , vždy byla vydána v rozhraní .NET 4.0)|
|Návrh|Při zachytávání <xref:System.InvalidOperationException?displayProperty=name> při provádění <xref:System.Data.Objects.ObjectContext.CreateDatabase> nebo <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)>, SQLExceptions by měl nyní také být zachycena.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)?displayProperty=nameWithType></li></ul>|

