### <a name="wcf-transport-security-supports-certificates-stored-using-cng"></a>Zabezpečení přenosu WCF podporuje certifikáty uložené pomocí CNG

|   |   |
|---|---|
|Podrobnosti|Počínaje aplikací cílených rozhraní .NET Framework 4.6.2, zabezpečení přenosu WCF podporuje certifikáty uložené pomocí knihovny kryptografie systému Windows (CNG). Tato podpora je omezena na certifikáty s veřejným klíčem, který má v délka exponentu delší než 32 služby bits. Pokud aplikace cílí rozhraní .NET Framework 4.6.2, tato funkce je ve výchozím. V dřívějších verzích rozhraní .NET Framework, pokus o použití X509 certifikáty s CSG zprostředkovatele úložiště klíčů vyvolá výjimku.|
|Návrh|Aplikace, které jsou na rozhraní .NET Framework 4.6.2 spuštěny cílové rozhraní .NET Framework 4.6.1 a starší ale můžete povolit podporu pro certifikáty CNG přidáním následující řádek na <code>&lt;runtime&gt;</code> v souboru app.config nebo web.config:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableCngCertificates=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>To lze také provést programově následujícím kódem:<pre><code class="language-cs">private const string DisableCngCertificates = @&quot;Switch.System.ServiceModel.DisableCngCertificate&quot;;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, false);&#13;&#10;</code></pre><pre><code class="language-vb">Const DisableCngCertificates As String = &quot;Switch.System.ServiceModel.DisableCngCertificates&quot;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, False)&#13;&#10;</code></pre>Všimněte si, že se z důvodu této změny, všechna kód, který závisí na pokus o inicializaci zabezpečené komunikace s certifikátem CNG selhání zpracování výjimek, budou již spuštěny.|
|Rozsah|Vedlejší|
|Version|4.6.2|
|Typ|Změna orientace|

