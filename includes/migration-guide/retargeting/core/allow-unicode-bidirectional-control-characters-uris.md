### <a name="allow-unicode-bidirectional-control-characters-in-uris"></a>Povolit řídicí znaky Unicode obousměrné v identifikátorech URI

|   |   |
|---|---|
|Podrobnosti|Určuje kódování Unicode několik speciální řídicí znaky, které určuje orientaci textu. V předchozích verzích rozhraní .NET Framework tyto znaky se nesprávně chyběly všechny identifikátory URI i v případě, že byly k dispozici v jejich procentuálně zakódovaný formuláře. Aby bylo možné lépe postupujte podle [RFC 3987](http://tools.ietf.org/html/rfc3987), umožňujeme teď tyto znaky v identifikátorech URI. Pokud najít nekódovaných v identifikátoru URI, jsou procentuálně zakódovaný. Pokud najít procentuálně zakódovaný jsou ponechané jako-je.|
|Návrh|U aplikací s cílovou verzí rozhraní .NET Framework počínaje 4.7.2 Podpora kódování Unicode obousměrné znaky ve výchozím nastavení zapnutá. Pokud tuto změnu nežádoucí, můžete jej zakázat přidáním následujícího kódu [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) přepněte <code>&lt;runtime&gt;</code> oddílu konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Pro aplikace, které jsou cíleny na starší verze rozhraní .NET Framework, ale jsou spuštěny v rozhraní .NET Framework 4.7.2 počínaje verzí podpora je ve výchozím nastavení zakázané obousměrné znaky kódování Unicode. Můžete ji povolit tak, že přidáte následující [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) přepněte <code>&lt;runtime&gt;</code> oddílu konfiguračního souboru aplikace::<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.2|
|Typ|Mění se cílení|
|Ovlivněné rozhraní API|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|

