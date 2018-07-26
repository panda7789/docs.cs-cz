### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a>Nyní používá SHA256 WCF PipeConnection.GetHashAlgorithm

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.7.1, Windows Communication Foundation používá hodnotu hash SHA256 pro generování náhodných názvů u pojmenovaných kanálů. V rozhraní .NET Framework 4.7 a dřívějších verzích používá hodnotu hash SHA1.|
|Návrh|Pokud narazíte na potíže s kompatibilitou s touto změnou v rozhraní .NET Framework 4.7.1 nebo novější, je můžete odhlásit ho tak, že přidáte následující řádek, který <code>&lt;runtime&gt;</code> části souboru app.config:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.1|
|Typ|Modul runtime|

