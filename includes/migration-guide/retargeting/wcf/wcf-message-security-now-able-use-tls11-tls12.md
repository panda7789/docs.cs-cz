---
ms.openlocfilehash: 0a3dc43ebdc58d54675f2264a8ee56d9f4358cd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859116"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a>Zabezpečení zpráv WCF je nyní schopno používat TLS1.1 a TLS1.2

|   |   |
|---|---|
|Podrobnosti|Počínaje rozhraním .NET Framework 4.7 mohou zákazníci konfigurovat tls1.1 nebo TLS1.2 v zabezpečení zpráv WCF kromě SSL3.0 a TLS1.0 prostřednictvím nastavení konfigurace aplikace.|
|Návrh|V rozhraní .NET Framework 4.7 je ve výchozím nastavení zakázána podpora tls1.1 a TLS1.2 v zabezpečení zpráv WCF. Můžete ji povolit přidáním následujícího řádku do <code>&lt;runtime&gt;</code> oddílu souboru app.config nebo web.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7|
|Typ|Změna cílení|
