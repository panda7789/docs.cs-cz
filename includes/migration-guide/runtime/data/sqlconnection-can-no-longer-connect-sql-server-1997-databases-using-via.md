### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a>SqlConnection můžete už připojení k SQL serveru 1997 nebo databází pomocí adaptéru VIA

|   |   |
|---|---|
|Podrobnosti|Připojení k databázím SQL Server pomocí [virtuální adaptér rozhraní (VIA) protokol](https://technet.microsoft.com/library/ms191229%28v=sql.105%29.aspx) již nejsou podporovány. Protokol použitý k připojení k databázi systému SQL Server je viditelný v připojovacím řetězci. Připojení VIA bude obsahovat prostřednictvím:&lt;servername&gt;. Pokud tato aplikace se připojuje k SQL přes protokol než VIA (tcp: nebo np: například), pak bude došlo k žádné narušující změně. Navíc připojení k SQL serveru 7 (1997) nejsou podporovány.|
|Návrh|Protokol VIA se již nepoužívá, takže alternativní protokolu by měla použít pro připojení k databázím SQL. Nejběžnější protokol použitý je protokol TCP/IP. Pokyny pro povolení protokolu TCP/IP naleznete [zde](https://msdn.microsoft.com/library/bb909712.aspx). Pokud databázi je dostupný pouze v intranetu, protokol sdílené kanály poskytnout lepší výkon při pomalém sítě.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)?displayProperty=nameWithType></li></ul>|

