### <a name="only-tls-10-11-and-12-protocols-supported-in-systemnetservicepointmanager-and-systemnetsecuritysslstream"></a>Pouze protokoly Tls 1.0, 1.1 a 1.2 podporovaných System.Net.ServicePointManager a System.Net.Security.SslStream

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.6 <xref:System.Net.ServicePointManager> a <xref:System.Net.Security.SslStream> třídy jsou povoleny pouze chcete použít jeden z těchto tří protokolů: protokol TLS 1.0, Tls1.1 nebo Tls1.2. SSL3.0 protokolu a šifer RC4 nejsou podporovány.|
|Návrh|Upgrade aplikace straně serveru pro protokol TLS 1.0, Tls1.1 nebo Tls1.2 je doporučené omezení rizik. Pokud to není proveditelné, nebo pokud jsou přerušená, klientské aplikace <xref:System.AppContext?displayProperty=name> třídy lze tuto funkci v některém ze dvou způsobů:<ol><li>Prostřednictvím kódu programu nastavením compat Zapne <xref:System.AppContext?displayProperty=name>, jak je vysvětleno [zde](http://blogs.msdn.com/b/dotnet/archive/2015/04/29/net-announcements-at-build-2015.aspx#dotnet46)</li><li>Přidejte následující řádek, který <code>&lt;runtime&gt;</code> část souboru app.config: <code>&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableSchUseStrongCrypto=true&quot;/&gt;</code>;</li></ol>|
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Mění se cílení|
|Ovlivněné rozhraní API|<ul><li><xref:System.Net.SecurityProtocolType.Ssl3?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl2?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl3?displayProperty=nameWithType></li></ul>|

