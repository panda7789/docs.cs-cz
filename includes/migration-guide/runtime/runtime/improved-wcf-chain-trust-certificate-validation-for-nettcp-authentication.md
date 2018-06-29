### <a name="improved-wcf-chain-trust-certificate-validation-for-nettcp-certificate-authentication"></a>Vylepšené WCF řetězu vztahu důvěryhodnosti ověření certifikátu pro ověřování pomocí certifikátu Net.Tcp

|   |   |
|---|---|
|Podrobnosti|Rozhraní .NET framework 4.7.2 zlepšuje ověření certifikátu důvěryhodnosti řetězu při použití ověřování certifikátů pomocí zabezpečení přenosu s použitím technologie WCF. Díky tomuto vylepšení klientské certifikáty, které se používají k ověření na serveru musí být nakonfigurován pro ověřování klientů.  Podobně jako certifikáty serveru, které jsou pro ověřování serveru musí být nakonfigurován pro ověřování serveru. Díky této změně pokud kořenový certifikát je zakázaná, ověřování řetězu certifikátů se nezdaří. Stejné změna byla také provedená na rozhraní .NET Framework 3.5 a novější verze prostřednictvím zabezpečení systému Windows kumulativní aktualizaci. Další informace můžete najít [zde](https://support.microsoft.com/en-us/help/4055269/security-only-update-for-net-framework-3-5-1-4-5-2-4-6-4-6-1-4-6-2-4-7). Tuto změnu ve výchozím nastavení zapnutý a může být vypnuto nastavení konfigurace.|
|Návrh|<ul><li>Pokud vaše certifikační server a klient má požadované OID rozšířeného použití klíče ověřte. Pokud ne, aktualizace vaší certifikační.</li><li>Ověřte, jestli kořenový certifikát je neplatný. Pokud ano, aktualizujte kořenový certifikát.</li><li>Postupy pro vyjádření výslovného nesouhlasu změnu: Pokud nelze aktualizovat certifikát, můžete obejít narušující změně dočasně s následujícím nastavením konfigurace, ale zrušení změn ponechá systému citlivé na zabezpečení problém.</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;wcf:useLegacyCertificateUsagePolicy&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.2|
|Typ|modul runtime|

