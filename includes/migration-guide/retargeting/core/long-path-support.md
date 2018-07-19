### <a name="long-path-support"></a>Podpora dlouhé cesty

|   |   |
|---|---|
|Podrobnosti|Počínaje aplikací využívajících rozhraní .NET Framework 4.6.2, dlouhé cesty (z až 32 znaků tis.) jsou podporované a 260 znaků (nebo <code>MAX_PATH</code>) omezení délky cesty byl odebrán. Pro aplikace, které jsou rekompilovány cílit na rozhraní .NET Framework 4.6.2, kód cesty, které se dřív vyvolala <xref:System.IO.PathTooLongException?displayProperty=name> protože cesty překročila 260 znaků se vyvolají <xref:System.IO.PathTooLongException?displayProperty=name> pouze za následujících podmínek:<ul><li>Je větší než délka cesty <xref:System.Int16.MaxValue> (32 767) znaků.</li><li>Operační systém vrátí <code>COR_E_PATHTOOLONG</code> nebo jeho ekvivalent.</li></ul>Pro aplikace, které jsou cíleny na rozhraní .NET Framework 4.6.1 a starší verze, modul runtime automaticky vyvolá <xref:System.IO.PathTooLongException?displayProperty=name> vždy, když cesty delší než 260 znaků.|
|Návrh|Pro aplikace, které cílí .NET Framework 4.6.2, můžete zrušit podporu dlouhé cesty Pokud není žádoucí, přidáním následujícího <code>&lt;runtime&gt;</code> část vaší <code>app.config</code> souboru:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Pro aplikace, které cílí dřívějších verzích rozhraní .NET Framework ale spustit v rozhraní .NET Framework 4.6.2 nebo novější, můžete přejít na dlouhé cestě podporu přidáním následujícího kódu do <code>&lt;runtime&gt;</code> část vaší <code>app.config</code> souboru:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Typ|Mění se cílení|

