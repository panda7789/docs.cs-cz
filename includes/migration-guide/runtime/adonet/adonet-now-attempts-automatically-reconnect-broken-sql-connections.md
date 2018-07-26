### <a name="adonet-now-attempts-to-automatically-reconnect-broken-sql-connections"></a>ADO.NET teď pokusí automaticky znovu připojila, přerušení připojení SQL

|   |   |
|---|---|
|Podrobnosti|Od rozhraní .NET Framework 4.5.1, rozhraní .NET Framework se pokusí automaticky znovu připojila, přerušení připojení SQL. I když to budou obvykle vytvořit obdobné aplikace spolehlivější, existují hraniční případy, kdy aplikace potřebuje vědět, že se ztratí připojení, tak, aby se provedlo určitou akci při opětovné připojení.|
|Návrh|Pokud tato funkce nežádoucí z důvodu kompatibility, je možné ho zakázat nastavením <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=name> vlastnost připojovacího řetězce (nebo <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=name>) na hodnotu 0.|
|Rozsah|Edge|
|Version|4.5.1|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Data.IDbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Configuration.ConnectionStringSettings.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor(System.Boolean)?displayProperty=nameWithType></li></ul>|

