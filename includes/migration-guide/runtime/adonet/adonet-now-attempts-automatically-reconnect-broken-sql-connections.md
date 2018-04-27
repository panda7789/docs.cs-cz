### <a name="adonet-now-attempts-to-automatically-reconnect-broken-sql-connections"></a>ADO.NET se nyní pokusí automaticky znovu připojit přerušení připojení SQL

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.5.1, rozhraní .NET Framework se pokusí automaticky znovu připojit přerušení připojení SQL. I když obvykle bude aplikace větší spolehlivost, ale existují případy edge, ve kterých se aplikace potřebuje vědět, že připojení bylo přerušeno, takže některé akce na opětovné připojení může trvat.|
|Návrh|Pokud je tato funkce není žádoucí, z důvodu kompatibility, lze ji vypnout nastavením <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=name> vlastnosti připojovacího řetězce (nebo <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=name>) na hodnotu 0.|
|Rozsah|Edge|
|Version|4.5.1|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Data.IDbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Configuration.ConnectionStringSettings.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor(System.Boolean)?displayProperty=nameWithType></li></ul>|

