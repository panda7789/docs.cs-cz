### <a name="icontobitmap-successfully-converts-icons-with-png-frames-into-bitmap-objects"></a>Ikony PNG snímky Icon.ToBitmap úspěšně převede na objekty rastrový obrázek

|   |   |
|---|---|
|Podrobnosti|Počínaje aplikací určených pro rozhraní .NET Framework 4.6 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda úspěšně převede ikon s použitím PNG snímků na objekty rastrového obrázku.<p/>V aplikacích, které jsou cíleny na rozhraní .NET Framework 4.5.2 a starší verze <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> vyvolá metoda výjimku <xref:System.ArgumentOutOfRangeException> výjimku, pokud má objekt ikony PNG snímků.<p/>Tato změna ovlivní aplikace, které jsou rekompilovány cílit na rozhraní .NET Framework 4.6 a které implementují zvláštní zacházení <xref:System.ArgumentOutOfRangeException> , která je vyvolána, když má objekt ikony PNG snímků. Při spuštění v rozhraní .NET Framework 4.6, převod je úspěšný, <xref:System.ArgumentOutOfRangeException> je už ne vyvolána, a proto je již vyvolána obslužná rutina výjimky.|
|Doporučení|Pokud toto chování nežádoucí, můžete zachovat předchozí chování tak, že přidáte následující element na <code>&lt;runtime&gt;</code> části souboru app.config:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true&quot; /&gt;&#13;&#10;</code></pre>Pokud již obsahuje soubor app.config <code>AppContextSwitchOverrides</code> elementu, nová hodnota mají sloučit s hodnotou atributu takto:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true;&lt;previous key&gt;=&lt;previous value&gt;&quot; /&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Drawing.Icon.ToBitmap?displayProperty=nameWithType></li></ul>|

