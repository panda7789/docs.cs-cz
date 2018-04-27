### <a name="icontobitmap-successfully-converts-icons-with-png-frames-into-bitmap-objects"></a>Ikony s PNG rámce Icon.ToBitmap úspěšně převede na objekty rastrového obrázku

|   |   |
|---|---|
|Podrobnosti|Počínaje aplikací, které se zaměřují rozhraní .NET Framework 4.6 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda úspěšně převede ikony s PNG rámce do objektů rastrového obrázku. V aplikacích, které cílí na rozhraní .NET Framework 4.5.2 a dřívějších verzích <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda vrátí <xref:System.ArgumentOutOfRangeException> výjimka, pokud má objekt ikonu rámce PNG. Tato změna ovlivňuje aplikace, která jsou překompilovat, jehož cílem je rozhraní .NET Framework 4.6 a které implementují zvláštní zpracování pro <xref:System.ArgumentOutOfRangeException> která se vyvolá, když má ikonu objekt rámce PNG. Při spuštění v rozhraní .NET Framework 4.6, převod proběhne úspěšně, <xref:System.ArgumentOutOfRangeException> je už ne vyvolána, a proto už volána obslužná rutina výjimky.|
|Návrh|Pokud je toto chování žádoucí, můžete zachovat předchozí chování přidáním následující elementu, který chcete <code>&lt;runtime&gt;</code> části souboru app.config:<pre><code class="language-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true&quot; /&gt;&#13;&#10;</code></pre>Pokud již obsahuje soubor app.config <code>AppContextSwitchOverrides</code> elementu, nová hodnota má být sloučena s atribut value takto:<pre><code class="language-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true;&lt;previous key&gt;=&lt;previous value&gt;&quot; /&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.Drawing.Icon.ToBitmap?displayProperty=nameWithType></li></ul>|

