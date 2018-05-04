### <a name="workflow-checksums-changed-from-md5-to-sha1"></a>Kontrolní součty pracovní postup změnil z MD5, SHA1

|   |   |
|---|---|
|Podrobnosti|Pro podporu ladění pomocí sady Visual Studio, generuje modulu runtime pracovního postupu kontrolního součtu pro instanci pracovního postupu pomocí algoritmu hash. V rozhraní .NET Framework 4.6.2 a starší verze algoritmu hash kontrolního součtu pracovního postupu používá algoritmus MD5, který chybu způsobil problémy s podporou standardu FIPS v systémech. Od verze 4.7 rozhraní .NET Framework, se algoritmus SHA1. Pokud váš kód obsahuje trvalé tyto kontrolní součty, budou kompatibilní.|
|Návrh|Pokud váš kód se nepodařilo načíst instance pracovního postupu, protože došlo k chybě kontrolního součtu, zkuste nastavení <code>AppContext</code> přepínač &quot;Switch.System.Activities.UseMD5ForWFDebugger&quot; na hodnotu true. V kódu:<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Activities.UseMD5ForWFDebugger&quot;, true);&#13;&#10;</code></pre>Nebo v konfiguraci:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Activities.UseMD5ForWFDebugger=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7|
|Typ|Změna orientace|

