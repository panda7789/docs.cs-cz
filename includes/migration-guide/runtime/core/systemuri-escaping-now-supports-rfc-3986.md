### <a name="systemuri-escaping-now-supports-rfc-3986"></a>Uvozovací znaky System.Uri teď podporuje RFC 3986

|   |   |
|---|---|
|Podrobnosti|Identifikátor URI uvozovací znaky se změnilo v rozhraní .NET Framework 4.5 na podporu [RFC 3986](http://tools.ietf.org/html/rfc3986). Určité změny zahrnují:<ul><li><xref:System.Uri.EscapeDataString(System.String)?displayProperty=name> řídicí sekvence vyhrazené znaky podle RFC 3986.</li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=name> není vyhnuli vyhrazené znaky.</li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=name> nevyvolá výjimku, pokud zjistí neplatnou řídicí sekvenci.</li><li>Nerezervované řídicí znaky nejsou uvozeny řídicími znaky.</li></ul>|
|Návrh|<ul><li>Aktualizace aplikací není závislý na <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=name> má být vyvolána v případě neplatnou řídicí sekvenci. Takové pořadí musí být rozpoznány přímo teď.</li><li>Podobně očekávejte, že řetězce Escaped a Neuvozené URI a Data se může lišit z rozhraní .NET Framework 4.0 a rozhraní .NET Framework 4.5 a nesmí být porovnána přímo mezi verzemi rozhraní .NET. Místo toho se má analyzovat a normalized v jedné verzi rozhraní .NET, než jsou provedeny všechny porovnání.</li></ul>|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Uri.EscapeDataString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=nameWithType></li></ul>|

