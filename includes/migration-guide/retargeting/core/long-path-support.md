### <a name="long-path-support"></a>Podpora dlouhá cesta

|   |   |
|---|---|
|Podrobnosti|Počínaje aplikací rozhraní .NET Framework 4.6.2, dlouhé cesty (z až 32 znaků tisíc) jsou podporovány cílených a 260 znaků (nebo <code>MAX_PATH</code>) odebrala se omezení délky cesty. Pro aplikace, které jsou překompilovat, jehož cílem je rozhraní .NET Framework 4.6.2, code cesty, které dříve došlo <xref:System.IO.PathTooLongException?displayProperty=name> protože překročil cesty 260 znaků nyní vyvolá <xref:System.IO.PathTooLongException?displayProperty=name> pouze za následujících podmínek:<ul><li>Délka cesty je větší než <xref:System.Int16.MaxValue> (32 767) znaků.</li><li>Operační systém vrátí <code>COR_E_PATHTOOLONG</code> nebo jeho ekvivalent.</li></ul>Pro aplikace, které cílí na rozhraní .NET Framework 4.6.1 a starší verze, modul runtime automaticky vyvolá <xref:System.IO.PathTooLongException?displayProperty=name> vždy, když cestu větší než 260 znaků.|
|Návrh|Pro aplikace, které cílí na rozhraní .NET Framework 4.6.2, se můžete rozhodnout skončila podpora dlouhá cesta Pokud není žádoucí přidáním následujícího <code>&lt;runtime&gt;</code> část vaší <code>app.config</code> souboru:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Pro aplikace, které cílí na starší verze rozhraní .NET Framework, ale spustit v rozhraní .NET Framework 4.6.2 nebo novější, můžete se rozhodnout v dlouho cesta podporu přidáním následujícího <code>&lt;runtime&gt;</code> část vaší <code>app.config</code> souboru:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.BlockLongPaths=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Typ|Změna orientace|

