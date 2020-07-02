---
ms.openlocfilehash: 87dc93ece10eaedbfbabddb5f857d0bcd12e05c4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615692"
---
### <a name="only-tls-10-11-and-12-protocols-supported-in-systemnetservicepointmanager-and-systemnetsecuritysslstream"></a>V System .NET. Třída ServicePointManager a System .NET. Security. SslStream se podporují jenom protokoly TLS 1,0, 1,1 a 1,2.

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4,6 <xref:System.Net.ServicePointManager> <xref:System.Net.Security.SslStream> jsou třídy a povoleny pouze pomocí jednoho z následujících tří protokolů: TLS 1.0, TLS 1.1 nebo TLS 1.2. Protokol SSL 3.0 a šifra šifry nejsou podporované.

#### <a name="suggestion"></a>Návrh

Doporučené zmírnění je upgrade aplikace na straně serveru na TLS 1.0, TLS 1.1 nebo TLS 1.2. Pokud to není možné, nebo pokud jsou klientské aplikace poškozeny, <xref:System.AppContext?displayProperty=fullName> můžete tuto funkci použít k odhlášení z těchto funkcí jedním ze dvou způsobů:

- Programově nastavením kompatibilních přepínačů na <xref:System.AppContext?displayProperty=fullName> , jak je popsáno [zde](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).
- Přidáním následujícího řádku do `<runtime>` části souboru app.config:

```xml
<AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>
```

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.6         |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Net.SecurityProtocolType.Ssl3?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.Ssl2?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.Ssl3?displayProperty=nameWithType>
