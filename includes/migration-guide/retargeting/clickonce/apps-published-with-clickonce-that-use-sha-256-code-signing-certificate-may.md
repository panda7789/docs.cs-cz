### <a name="apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a>Publikování s ClickOnce aplikace, které používají certifikát pro podpis kódu a SHA-256 může dojít k selhání v systému Windows 2003

|   |   |
|---|---|
|Podrobnosti|Spustitelný soubor je podepsán SHA256. Dřív byla podepsána pomocí SHA1 bez ohledu na to, jestli certifikát pro podpis kódu byl SHA-1 nebo SHA-256. To platí pro:<ul><li>Všechny aplikace vytvořené pomocí sady Visual Studio 2012 nebo novější.</li><li>Aplikace vytvořené s nástroji Visual Studio 2010 nebo starší na systémy se nachází rozhraní .NET Framework 4.5.</li></ul>Kromě toho pokud se nachází na rozhraní .NET Framework 4.5 nebo novější, ClickOnce manifest jsou také podepsány pomocí algoritmu SHA-256 pro certifikáty SHA-256, bez ohledu na verzi rozhraní .NET Framework, vůči které jeho kompilace.|
|Návrh|Změna v podepisování ClickOnce spustitelné ovlivňuje pouze systémy Windows Server 2003; vyžadují nainstalované KB 938397. Změna v podepsání manifestu pomocí algoritmu SHA-256, i v případě, že aplikace cílí na rozhraní .NET Framework 4.0 nebo starší verze zavádí závislostí modulu runtime v rozhraní .NET Framework 4.5 nebo novější.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Změna orientace|

