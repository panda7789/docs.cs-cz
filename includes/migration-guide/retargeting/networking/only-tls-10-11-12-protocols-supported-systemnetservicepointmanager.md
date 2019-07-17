---
ms.openlocfilehash: 5b531dc23feb311a797823dfa2a4d853859f9e18
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68235582"
---
### <a name="only-tls-10-11-and-12-protocols-supported-in-systemnetservicepointmanager-and-systemnetsecuritysslstream"></a>Pouze protokoly Tls 1.0, 1.1 a 1.2 podporovaných System.Net.ServicePointManager a System.Net.Security.SslStream

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.6 <xref:System.Net.ServicePointManager> a <xref:System.Net.Security.SslStream> třídy jsou povoleny pouze chcete použít jeden z těchto tří protokolů: Protokol TLS 1.0, Tls1.1 nebo Tls1.2. SSL3.0 protokolu a šifer RC4 nejsou podporovány.|
|Doporučení|Upgrade aplikace straně serveru pro protokol TLS 1.0, Tls1.1 nebo Tls1.2 je doporučené omezení rizik. Pokud to není proveditelné, nebo pokud jsou přerušená, klientské aplikace <xref:System.AppContext?displayProperty=name> třídy lze tuto funkci v některém ze dvou způsobů:<ol><li>Prostřednictvím kódu programu nastavením compat Zapne <xref:System.AppContext?displayProperty=name>, jak je vysvětleno [tady](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</li><li>Přidejte následující řádek, který <code>&lt;runtime&gt;</code> část souboru app.config:</li></ol><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableSchUseStrongCrypto=true&quot;/&gt;&#13;&#10;</code></pre>|
|Scope|Vedlejší|
|Version|4.6|
|type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Net.SecurityProtocolType.Ssl3?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl2?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl3?displayProperty=nameWithType></li></ul>|
