### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a>Povolit kódování Unicode v URI, které vypadat podobně jako sdílené složky UNC

|   |   |
|---|---|
|Podrobnosti|V <xref:System.Uri?displayProperty=fullName>, sestavením souboru identifikátory URI obsahující obě UNC název sdílené složky a znaky znakové sady Unicode již nebude v identifikátoru URI se neplatný vnitřní stav. Chování se změní, pouze pokud všechny tyto jsou splněny:<ul><li>Identifikátor URI má schéma <code>file:</code> a následuje čtyři nebo více lomítka.</li><li>Název hostitele začíná podtržítkem nebo další symbol vyhrazena.</li><li>Identifikátor URI obsahuje znaky kódování Unicode.</li></ul>|
|Návrh|Práce s identifikátory URI obsahující konzistentně Unicode aplikace mít opačném případě může toto chování tak, aby zakázala odkazy na sdílené složky UNC. Tyto aplikace by měly používat <xref:System.Uri.IsUnc> místo.|
|Rozsah|Edge|
|Version|4.7.2|
|Typ|modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|

