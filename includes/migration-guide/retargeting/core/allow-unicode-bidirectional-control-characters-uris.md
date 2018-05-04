### <a name="allow-unicode-bidirectional-control-characters-in-uris"></a>Povolit řídicí znaky Unicode obousměrného na identifikátory URI

|   |   |
|---|---|
|Podrobnosti|Unicode určuje několik speciální řídicí znaky, které slouží k zadání orientaci textu. V předchozích verzích rozhraní .NET Framework tyto znaky se nesprávně odstraní a ze všech identifikátory URI i v případě, že byly v jejich formuláře kódovaná v procentech. Aby bylo možné lépe postupujte podle [RFC 3987](http://tools.ietf.org/html/rfc3987), jsme teď povolit tyto znaky v identifikátory URI. Když se najde nekódovaných v identifikátoru URI, jsou kódováním procent. Když se najde kódováním procent jsou ponechané jako-je.|
|Návrh|Pro aplikace, které cílové verze rozhraní .NET Framework počínaje 4.7.2 podpora pro Unicode obousměrné znaky je ve výchozím nastavení povolené. Pokud tato změna není žádoucí, můžete ji zakázat přidáním následující [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) přepnout <code>&lt;runtime&gt;</code> oddílu konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Pro aplikace, které cílí na starší verze rozhraní .NET Framework, ale běží v rámci verze od verze rozhraní .NET Framework 4.7.2, podporu obousměrného znaků Unicode ve výchozím nastavení vypnutá. Můžete ji povolit přidáním následující [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) přepnout <code>&lt;runtime&gt;</code> oddílu konfiguračního souboru aplikace::<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.2|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|

