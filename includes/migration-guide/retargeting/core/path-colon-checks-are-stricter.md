### <a name="path-colon-checks-are-stricter"></a>Cesta dvojtečkou kontroly jsou přísnější

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6.2 počet změn, byly provedeny pro podporu dříve nepodporované cesty (jak v délku a format). Kontroly syntaxe oddělovače (dvojtečka) správné jednotky byly provedeny více správné, což mělo za následek straně blokování některé cesty identifikátoru URI několik rozhraní API v vyberte cestu kde používají tolerovat.|
|Návrh|Pokud předávání identifikátorů URI pro ovlivněné rozhraní API, upravte řetězec, který má být právní cesta první.<ul><li>Schéma ručně odebrat z adresy URL (například odebrat <code>file://</code> z adresy URL)</li><li>Předat identifikátor URI, která <xref:System.Uri> třídu a použijte <xref:System.Uri.LocalPath></li></ul>Alternativně můžete zamítnutí novou cestu normalizaci nastavením <code>Switch.System.IO.UseLegacyPathHandling</code> AppContext přepínače na hodnotu true.|
|Rozsah|Edge|
|Version|4.6.2|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType></li><li><xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType></li></ul>|

