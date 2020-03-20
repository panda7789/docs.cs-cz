---
ms.openlocfilehash: 5b531dc23feb311a797823dfa2a4d853859f9e18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "68235582"
---
### <a name="only-tls-10-11-and-12-protocols-supported-in-systemnetservicepointmanager-and-systemnetsecuritysslstream"></a>Pouze protokoly Tls 1.0, 1.1 a 1.2 podporované v system.net.servicepointmanagera a system.net.security.sslstream

|   |   |
|---|---|
|Podrobnosti|Počínaje rozhraním .NET Framework 4.6 mohou třídy <xref:System.Net.ServicePointManager> a <xref:System.Net.Security.SslStream> používat pouze jeden z následujících tří protokolů: Tls1.0, Tls1.1 nebo Tls1.2. Protokol SSL3.0 a šifra RC4 nejsou podporovány.|
|Návrh|Doporučené zmírnění je upgrade aplikace na straně sever na Tls1.0, Tls1.1 nebo Tls1.2. Pokud to není možné, nebo pokud klientské <xref:System.AppContext?displayProperty=name> aplikace jsou rozbité, třídy lze odhlásit z této funkce v jednom ze dvou způsobů:<ol><li>Programovým nastavením compat zapne <xref:System.AppContext?displayProperty=name>na , jak je vysvětleno [zde](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</li><li>Přidáním následujícího řádku <code>&lt;runtime&gt;</code> do části souboru app.config:</li></ol><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableSchUseStrongCrypto=true&quot;/&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Net.SecurityProtocolType.Ssl3?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl2?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl3?displayProperty=nameWithType></li></ul>|
