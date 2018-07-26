### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a>Probíhá pokus o připojení TCP/IP k databázi systému SQL Server, který se přeloží `localhost` selže

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6 a 4.6.1 probíhá pokus o připojení TCP/IP k databázi systému SQL Server, který se přeloží <code>localhost</code> selže s chybou, &quot;při navazování připojení k serveru SQL Server došlo k chybě související se sítí nebo s instancí. Server nebyl nalezen nebo nebyl přístupný. Ověřte, zda je název instance správný a, SQL Server je nakonfigurován pro povolit vzdálená připojení. (poskytovatel: rozhraní sítě systému SQL, chyba: 26 - Chyba vyhledávání serveru či Instance zadáno)&quot;|
|Návrh|Tento problém byl vyřešen a obnovit předchozí chování v rozhraní .NET Framework 4.6.2. Pro připojení k serveru SQL Server Database, který se přeloží na <code>localhost</code>, proveďte upgrade na rozhraní .NET Framework 4.6.2.|
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Modul runtime|

