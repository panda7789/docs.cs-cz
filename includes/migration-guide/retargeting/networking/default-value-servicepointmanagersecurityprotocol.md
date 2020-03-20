---
ms.openlocfilehash: 122a5ab3e2def7c19d3d523881fcb15df4dbca26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "68235497"
---
### <a name="default-value-of-servicepointmanagersecurityprotocol-is-securityprotocoltypesystemdefault"></a>Výchozí hodnota ServicePointManager.SecurityProtocol je SecurityProtocolType.System.Default

|   |   |
|---|---|
|Podrobnosti|Počínaje aplikacemi, které cílí na rozhraní .NET <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> Framework <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType>4.7, je výchozí hodnota vlastnosti . Tato změna umožňuje síťovým rozhraním API rozhraní .NET Framework založeným na sslstreamu (například FTP, HTTPS a SMTP) dědit výchozí protokoly zabezpečení z operačního systému namísto použití pevně zakódovaných hodnot definovaných rozhraním .NET Framework. Výchozí hodnota se liší podle operačního systému a libovolné vlastní konfigurace prováděné správcem systému. Informace o výchozím protokolu SChannel v každé verzi operačního systému Windows naleznete [v tématu Protokoly v protokolu TLS/SSL (Schannel SSP)](https://docs.microsoft.com/windows/desktop/SecAuthN/protocols-in-tls-ssl--schannel-ssp-).</p>U aplikací, které cílí na starší verzi rozhraní <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> .NET Framework, závisí výchozí hodnota vlastnosti na verzi cíleného rozhraní .NET Framework. Další informace naleznete v [části Obnovení cílení na změny pro migraci z rozhraní .NET Framework 4.5.2 až 4.6.](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#networking)|
|Návrh|Tato změna ovlivňuje aplikace, které cílí na rozhraní .NET Framework 4.7 nebo novější verze. <br>Pokud dáváte přednost použití definovaného protokolu, spíše než spoléhání se na <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> výchozí systém, můžete explicitně nastavit hodnotu vlastnosti.<br>Pokud je tato změna nežádoucí, můžete se od ní odhlásit přidáním nastavení konfigurace do části [ \<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace. Následující příklad ukazuje <code>&lt;runtime&gt;</code> oddíl i <code>Switch.System.Net.DontEnableSystemDefaultTlsVersions</code> přepínač opt-out:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableSystemDefaultTlsVersions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType></li></ul>|
