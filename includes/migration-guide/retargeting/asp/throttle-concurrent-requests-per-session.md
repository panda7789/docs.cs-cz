---
ms.openlocfilehash: b521f4163bf5bf4a369d0eec12dae503703a976e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614436"
---
### <a name="throttle-concurrent-requests-per-session"></a>Omezit souběžné požadavky na relaci

#### <a name="details"></a>Podrobnosti

V .NET Framework 4.6.2 a dříve ASP.NET spouští požadavky se stejným identifikátorem SessionID sekvenčně a ASP.NET vždy vystavuje identifikátor SessionID prostřednictvím souborů cookie ve výchozím nastavení. Pokud bude odpověď trvat dlouhou dobu, významně sníží výkon serveru pouhým stisknutím klávesy <kbd>F5</kbd> v prohlížeči. V této opravě jsme přidali čítač, který sleduje požadavky ve frontě a ukončí žádosti, když překročí zadaný limit. Výchozí hodnota je 50. Pokud je dosaženo limitu, bude zaznamenáno upozornění v protokolu událostí a odpověď HTTP 500 může být zaznamenána v protokolu služby IIS.

#### <a name="suggestion"></a>Návrh

Chcete-li obnovit původní chování, můžete do souboru web.config přidat následující nastavení, abyste se odhlásili od nového chování.

```xml
<appSettings>
    <add key="aspnet:RequestQueueLimitPerSession" value="2147483647"/>
</appSettings>
```

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4,7         |
| Typ    | Změna cílení |
