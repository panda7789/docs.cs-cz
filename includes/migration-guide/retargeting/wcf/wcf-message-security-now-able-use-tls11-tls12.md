### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a>Zabezpečení zpráv WCF je teď možné používat TLS1.1 a TLS1.2

|   |   |
|---|---|
|Podrobnosti|Od verze 4.7 rozhraní .NET Framework, zákazníci mohou nakonfigurovat TLS1.1 nebo TLS1.2 v zabezpečení zpráv WCF kromě SSL3.0 a TLS1.0 prostřednictvím nastavení konfigurace aplikace.|
|Návrh|V 4.7 rozhraní .NET Framework podpora TLS1.1 a TLS1.2 v zabezpečení zpráv WCF ve výchozím nastavení vypnutá. Můžete ji povolit přidáním následující řádek <code>&lt;runtime&gt;</code> v souboru app.config nebo web.config:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7|
|Typ|Změna orientace|

