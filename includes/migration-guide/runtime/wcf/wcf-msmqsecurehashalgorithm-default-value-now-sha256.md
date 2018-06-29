### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a>WCF MsmqSecureHashAlgorithm výchozí hodnota je teď SHA256

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.7.1, výchozí zprávu podpisový algoritmus ve WCF pro zprávy služby Msmq je SHA256. V rozhraní .NET Framework 4.7 a dřívějších verzí je výchozí zprávu podpisový algoritmus SHA1.|
|Návrh|Pokud narazíte na problémy s kompatibilitou se tato změna na rozhraní .NET Framework 4.7.1 nebo novější, můžete můžete výslovný nesouhlas s změnu přidáním následující řádek na <code>&lt;runtime&gt;</code>části souboru app.config:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.1|
|Typ|modul runtime|

