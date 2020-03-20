---
ms.openlocfilehash: ee9bba91a2c4e11bd005fedb8adf0c2e7c7b0d3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804549"
---
### <a name="certificate-eku-oid-validation"></a>Ověření IDENTIFIKÁTORU OID KLÍČE CERTIFIKÁTU

|   |   |
|---|---|
|Podrobnosti|Počínaje rozhraním .NET Framework <xref:System.Net.Security.SslStream> 4.6 provedou třídy nebo <xref:System.Net.ServicePointManager> rozšířené ověření identifikátoru objektu (EKU) (OID). Rozšířené využití klíče (EKU) rozšíření je kolekce identifikátorů objektů (ID), které označují aplikace, které používají klíč. Ověření identifikátoru OID klíče používá zpětná volání vzdálených certifikátů k zajištění, že vzdálený certifikát má správné Identifikátory OID pro zamýšlený účel.|
|Návrh|Pokud je tato změna nežádoucí, můžete zakázat ověření identifikátoru EKU certifikátu přidáním [`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) následujícího přepínače do [ \<>AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) v konfiguračním souboru aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontCheckCertificateEKUs=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] Toto nastavení je k dispozici pouze pro zpětnou kompatibilitu. Jeho použití se jinak nedoporučuje.</blockquote> |
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|
