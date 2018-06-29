### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a>WCF PipeConnection.GetHashAlgorithm teď používá SHA256

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.7.1, Windows Communication Foundation využívá algoritmus hash SHA256 Generovat náhodné názvy pro pojmenované kanály. V rozhraní .NET Framework 4.7 a dřívějších verzí použije algoritmus hash SHA1.|
|Návrh|Pokud narazíte na potíže s kompatibilitou s Tato změna na rozhraní .NET Framework 4.7.1 nebo novější, můžete můžete výslovný nesouhlas s ho přidáním následující řádek na <code>&lt;runtime&gt;</code> části souboru app.config:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.1|
|Typ|modul runtime|

