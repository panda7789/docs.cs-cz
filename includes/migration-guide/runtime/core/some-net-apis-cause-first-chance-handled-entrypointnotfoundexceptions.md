### <a name="some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a>Některé rozhraní API technologie .NET příčina první příležitosti EntryPointNotFoundExceptions (zpracovává)

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.5, malý počet metod rozhraní .NET začal vyvolání první příležitosti <xref:System.EntryPointNotFoundException?displayProperty=name>s. Tyto výjimky byly zpracovány v rozhraní .NET Framework, ale by mohlo způsobit narušení testovací automatizaci, která neočekávali, první možnosti výjimky. Pokud je povoleno HighVersionLie došlo k přerušení tyto stejné rozhraní API některé ApiVerifier scénáře.|
|Návrh|Tato chyba může zabránit upgrade rozhraní .NET Framework 4.5.1. Alternativně můžete aktualizovat, test automatizace není rozdělit na first chance <xref:System.EntryPointNotFoundException?displayProperty=name>s.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)?displayProperty=nameWithType></li></ul>|

