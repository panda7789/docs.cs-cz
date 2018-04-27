### <a name="only-tls-10-11-and-12-protocols-supported-in-systemnetservicepointmanager-and-systemnetsecuritysslstream"></a>Pouze protokoly Tls 1.0, 1.1 a 1.2 podporované v System.Net.ServicePointManager a System.Net.Security.SslStream

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.6 <xref:System.Net.ServicePointManager> a <xref:System.Net.Security.SslStream> třídy jsou povoleny pouze pomocí jednoho z následujících tří protokolů: Tls1.0, Tls1.1 nebo Tls1.2. Protokol SSL3.0 a šifrovací algoritmus RC4 nejsou podporovány.|
|Návrh|Doporučené omezení rizik se k upgradu aplikace na straně serveru Tls1.0, Tls1.1 nebo Tls1.2. Pokud to není možné, nebo pokud klientských aplikací jsou poškozená, <xref:System.AppContext?displayProperty=name> třídu lze použít pro vyjádření výslovného nesouhlasu tuto funkci v některém ze dvou způsobů:<ol><li>Prostřednictvím kódu programu nastavením compat přepne <xref:System.AppContext?displayProperty=name>, jak je popsáno [sem](http://blogs.msdn.com/b/dotnet/archive/2015/04/29/net-announcements-at-build-2015.aspx#dotnet46)</li><li>Přidáním následující řádek na <code>&lt;runtime&gt;</code> v souboru app.config: <code>&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableSchUseStrongCrypto=true&quot;/&gt;</code>;</li></ol>|
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.Net.SecurityProtocolType.Ssl3?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl2?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl3?displayProperty=nameWithType></li></ul>|

