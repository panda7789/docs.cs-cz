### <a name="apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a>Mohou být neúspěšné aplikacím publikovaným pomocí ClickOnce, které používají certifikát pro podpis kódu SHA-256, Windows 2003

|   |   |
|---|---|
|Podrobnosti|Spustitelný soubor je podepsán SHA256. Dříve byla podepsána pomocí SHA1 bez ohledu na to, zda byl certifikát pro podpis kódu SHA-1 nebo SHA-256. To platí pro:<ul><li>Všemi aplikacemi sestavenými pomocí sady Visual Studio 2012 nebo novější.</li><li>Aplikace vytvořené pomocí sady Visual Studio 2010 nebo starší na systémy s .NET Framework 4.5, který je k dispozici.</li></ul>Kromě toho pokud je k dispozici rozhraní .NET Framework 4.5 nebo novější, ClickOnce – manifest jsou také podepsány pomocí algoritmu SHA-256 pro certifikáty SHA-256, bez ohledu na verzi rozhraní .NET Framework, proti kterému byl zkompilován.|
|Návrh|Tato změna podepisování ClickOnce spustitelný soubor má vliv pouze systémy Windows Server 2003; vyžadují, aby byla instalace KB 938397. Zavádí změnu v hodnotě podepisování manifest pomocí algoritmu SHA-256, i když aplikace cílí na rozhraní .NET Framework 4.0 nebo dřívější verze závislosti modulu runtime v rozhraní .NET Framework 4.5 nebo novější verze.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Mění se cílení|

