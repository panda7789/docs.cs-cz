---
ms.openlocfilehash: c646372104457e8bc5d418744847f3ee771c8d8b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614537"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a>Zabezpečení zpráv WCF teď může používat protokol TLS 1.1 a TLS 1.2.

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4,7 můžou zákazníci kromě nastavení konfigurace aplikace nakonfigurovat protokol TLS 1.1 nebo TLS 1.2 v zabezpečení zpráv WCF i na zabezpečení SSL 3.0 a TLS 1.0.

#### <a name="suggestion"></a>Návrh

Ve výchozím nastavení je v .NET Framework 4,7 podporovaná podpora TLS 1.1 a TLS 1.2 v zabezpečení zpráv WCF. Můžete ji povolit přidáním následujícího řádku do `<runtime>` oddílu app.config nebo web.config souboru:

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" />
</runtime>
```

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4,7         |
| Typ    | Změna cílení |
