### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a>Vazby WCF s režim zabezpečení TransportWithMessageCredential

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.6.1, vazby WCF, který používá režim zabezpečení TransportWithMessageCredential se dá nastavit pro příjem zpráv s nepodepsané &quot;k&quot; hlavičky pro zabezpečení asymetrické klíče. Ve výchozím nastavení, nepodepsané &quot;k&quot; bude pokračovat hlaviček zamítnutí v rozhraní .NET Framework 4.6.1. Jsou pouze přijaty pokud aplikace požádá do tento nový režim operace pomocí Switch.System.ServiceModel.AllowUnsignedToHeader konfigurace přepínače.|
|Návrh|Protože se jedná o funkci přihlášení, by neměly ovlivnit chování existující aplikace.<br/>Chcete-li určit, zda se má použít nové chování, nebo Ne, použijte následující nastavení konfigurace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.AllowUnsignedToHeader=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Transparentní|
|Version|4.6.1|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li></ul>|

