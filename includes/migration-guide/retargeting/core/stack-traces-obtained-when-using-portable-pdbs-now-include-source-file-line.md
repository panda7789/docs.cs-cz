### <a name="stack-traces-obtained-when-using-portable-pdbs-now-include-source-file-and-line-information-if-requested"></a>Trasování zásobníku získané při použití přenosných PDB teď zahrnují informace o zdroji souboru a řádku, pokud požadovaný

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.7.2, trasování zásobníku získané při použití přenosných PDB obsahovat zdrojový soubor a řádku informace o vyžádání. V verze starší než rozhraní .NET Framework 4.7.2, zdrojový soubor a řádku informace budou k dispozici při použití přenosné soubory PDB, i když explicitně požadována.|
|Návrh|Pro aplikace, které cílí na rozhraní .NET Framework 4.7.2, se můžete rozhodnout mimo informace o zdrojovém souboru a řádku při použití přenosných soubory PDB, pokud není žádoucí přidáním následujícího <code>&lt;runtime&gt;</code> část vaší <code>app.config</code> souboru:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Pro aplikace, které cílí na starší verze rozhraní .NET Framework, ale spustit v rozhraní .NET Framework 4.7.2 nebo novější, můžete se rozhodnout v informace o zdrojovém souboru a řádku při použití přenosných PDB přidáním následujícího <code>&lt;runtime&gt;</code> část vaší <code>app.config</code>souboru:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7.2|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.Diagnostics.StackTrace.%23ctor(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Boolean)?displayProperty=nameWithType><li><xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Int32,System.Boolean)?displayProperty=nameWithType></li></ul>|

