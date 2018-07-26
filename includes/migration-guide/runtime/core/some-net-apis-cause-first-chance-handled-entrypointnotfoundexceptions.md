### <a name="some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a>První možnost některá rozhraní API pro .NET příčina EntryPointNotFoundExceptions (zpracování)

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.5, začal malý počet metod rozhraní .NET, vyvolání první příležitosti <xref:System.EntryPointNotFoundException?displayProperty=name>s. Tyto výjimky se zpracovávají v rámci rozhraní .NET Framework, ale může poškodit automatizace testů, který nebyl očekáván první příležitosti výjimky. Tato stejná rozhraní API přerušením, dokud některé scénáře ApiVerifier HighVersionLie je povolená.|
|Návrh|Upgradem na rozhraní .NET Framework 4.5.1 se lze vyvarovat této chyby. Můžete také aktualizovat automatizace testů tak, že nedojde k narušení na první odpovídající <xref:System.EntryPointNotFoundException?displayProperty=name>s.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)?displayProperty=nameWithType></li></ul>|

