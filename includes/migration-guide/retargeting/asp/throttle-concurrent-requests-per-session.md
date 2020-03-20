---
ms.openlocfilehash: 9c3eedb7f7d4cd030a12c141b8630876c1ffdb4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859168"
---
### <a name="throttle-concurrent-requests-per-session"></a>Omezení souběžných požadavků na relaci

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6.2 a starší ASP.NET provádí požadavky se stejným Sessionid postupně a ASP.NET vždy vydává Sessionid prostřednictvím cookies ve výchozím nastavení. Pokud stránka trvá dlouhou dobu reagovat, bude výrazně snížit výkon serveru pouhým stisknutím klávesy F5 v prohlížeči. V opravě jsme přidali čítač pro sledování požadavků ve frontě a ukončení požadavků, pokud překročí zadaný limit. Výchozí hodnota je 50. Pokud je dosaženo limitu, bude do protokolu událostí zaznamenáno upozornění a odpověď HTTP 500 může být zaznamenána do protokolu služby IIS.|
|Návrh|Chcete-li obnovit staré chování, můžete do souboru web.config přidat následující nastavení a odhlásit se z nového chování.<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;aspnet:RequestQueueLimitPerSession&quot; value=&quot;2147483647&quot;/&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7|
|Typ|Změna cílení|
