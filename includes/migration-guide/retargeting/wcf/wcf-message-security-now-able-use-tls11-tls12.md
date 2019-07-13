---
ms.openlocfilehash: 3b7b50700541649a785fa9bbe3ecc56c2697fbfc
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859116"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a>Zabezpečení zpráv WCF je teď možné použít TLS1.1 a TLS1.2

|   |   |
|---|---|
|Podrobnosti|Spuštění v rozhraní .NET Framework 4.7, zákazníci můžou nakonfigurovat TLS1.1 nebo TLS1.2 v zabezpečení zpráv WCF kromě SSL3.0 a protokol TLS 1.0 prostřednictvím nastavení konfigurace aplikace.|
|Doporučení|V rozhraní .NET Framework 4.7 je ve výchozím nastavení zakázána podpora TLS1.1 a TLS1.2 v zabezpečení zpráv WCF. Můžete ji povolit tak, že přidáte následující řádek, který <code>&lt;runtime&gt;</code> část souboru app.config nebo web.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Scope|Edge|
|Version|4.7|
|type|Změna cílení|

