### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a>Pokusu o připojení TCP/IP k databázi systému SQL Server, který se přeloží na `localhost` selže

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6 a 4.6.1, pokusu o připojení TCP/IP k databázi systému SQL Server, který se přeloží na <code>localhost</code> selže s chybou, &quot;chyby související se sítí nebo konkrétní instancí došlo při navazování připojení k systému SQL Server. Server nebyl nalezen nebo není přístupný. Ověřte, zda je název instance správný a zda systém SQL Server je nakonfigurován k povolení vzdálených připojení. (Zprostředkovatel: rozhraní sítě systému SQL, chyba: 26 - chyba vyhledání Server nebo instanci zadáno)&quot;|
|Návrh|Tento problém byl vyřešen a obnovit předchozí chování v rozhraní .NET Framework 4.6.2. Pro připojení k systému SQL Server Database, který se přeloží na <code>localhost</code>, upgradujte na verzi rozhraní .NET Framework 4.6.2.|
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|modul runtime|

