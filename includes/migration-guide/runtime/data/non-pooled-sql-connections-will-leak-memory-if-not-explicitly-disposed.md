### <a name="non-pooled-sql-connections-will-leak-memory-if-not-explicitly-disposed"></a>Ve fondu bez připojení SQL bude nastat únik paměti není-li explicitně zlikvidován.

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.5 není ve fondu připojení SQL, které nejsou přístupné explicitně (pomocí uvolnění, zavřete, nebo pomocí) bude nastat únik paměti|
|Návrh|Tento problém vyřešen v rozhraní .NET Framework 4.5 servisní aktualizace. Aktualizujte prosím rozhraní .NET Framework 4.5, nebo upgradujte na verzi rozhraní .NET Framework 4.5.1 nebo novější, pokud chcete tento problém vyřešit. Alternativně může být tento problém vyhnout při použití <xref:System.Data.SqlClient.SqlConnection?displayProperty=name> v &#39;pomocí&#39; vzorů (což je osvědčeným postupem) nebo explicitně voláním Dispose nebo uzavřít, když připojení se už nepotřebuje.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String%2CSystem.Data.SqlClient.SqlCredential)?displayProperty=nameWithType></li></ul>|

