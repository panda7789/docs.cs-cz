---
ms.openlocfilehash: 2359dafb9042c13ae75e644d4ea655f53c14e95e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804332"
---
### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a>Vazba WCF s režimem zabezpečení TransportWithMessageCredential

|   |   |
|---|---|
|Podrobnosti|Počínaje rozhraním .NET Framework 4.6.1 lze vazbu WCF, která používá režim zabezpečení TransportWithMessageCredential, nastavit tak, aby přijímali zprávy s nepodepsanými &quot;záhlavími&quot; pro asymetrické klíče zabezpečení. Ve výchozím nastavení &quot;&quot; bude nepodepsaný záhlaví nadále odmítnut v rozhraní .NET Framework 4.6.1. Budou přijaty pouze v případě, že se aplikace přihlásí do tohoto nového režimu operace pomocí konfiguračního přepínače Switch.System.ServiceModel.AllowUnsignedToHeader.|
|Návrh|Vzhledem k tomu, že se jedná o funkci opt-in, neměla by mít vliv na chování stávajících aplikací.<br/>Chcete-li určit, zda bude nové chování použito či nikoli, použijte následující nastavení konfigurace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.AllowUnsignedToHeader=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Průhlednost|
|Version|4.6.1|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li></ul>|
