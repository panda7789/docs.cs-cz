### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a>Povolit kódování Unicode v identifikátory URI, které se podobají UNC sdílené složky

|   |   |
|---|---|
|Podrobnosti|V <xref:System.Uri?displayProperty=fullName>sestavením souboru identifikátory URI obsahující oba UNC název sdílené složky a znaky znakové sady Unicode již nebude v identifikátoru URI se neplatný vnitřní stav. Chování se změní, pouze pokud všechny tyto jsou splněny:<ul><li>Identifikátor URI obsahuje schéma <code>file:</code> a je následována čtyři nebo více lomítek.</li><li>Název hostitele začíná podtržítkem nebo jiný nerezervované symbol.</li><li>Identifikátor URI obsahuje znaky kódování Unicode.</li></ul>|
|Doporučení|Aplikace pracující s identifikátory URI obsahující konzistentně Unicode mohli případně použít toto chování Pokud chcete zakázat odkazy na sdílené složky UNC. Tyto aplikace by měly používat <xref:System.Uri.IsUnc> místo.|
|Rozsah|Edge|
|Version|4.7.2|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|

