---
ms.openlocfilehash: 0e949cbdeda99dd7b94e919b903a21171a57f527
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614492"
---
### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a>Vazba WCF s režimem zabezpečení TransportWithMessageCredential

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4.6.1 může být vazba WCF, která používá režim zabezpečení TransportWithMessageCredential, nastavená tak, aby přijímala zprávy s nepodepsanými &quot; &quot; hlavičkami pro asymetrické zabezpečovací klíče. Ve výchozím nastavení &quot; &quot; budou v .NET Framework 4.6.1 nadále odmítány nepodepsané do hlaviček. Budou přijaty pouze v případě, že se aplikace výslovný do tohoto nového režimu provozu pomocí Switch.System. AllowUnsignedToHeader konfigurační přepínač ServiceModel.

#### <a name="suggestion"></a>Návrh

Vzhledem k tomu, že se jedná o funkci výslovného souhlasu, nemělo by to mít vliv na chování stávajících aplikací.<br/>Chcete-li určit, zda je použito nové chování, nebo ne, použijte následující nastavení konfigurace:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.ServiceModel.AllowUnsignedToHeader=true" />
</runtime>
```

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Průhlednost |
| Verze | 4.6.1       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
