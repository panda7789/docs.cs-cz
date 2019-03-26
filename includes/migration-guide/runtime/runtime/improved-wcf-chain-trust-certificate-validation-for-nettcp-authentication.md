---
ms.openlocfilehash: e12ba8eb53e6725ebc2e1d87edff3a6a3ce2116b
ms.sourcegitcommit: 5d9f4b805787f890ca6e0dc7ea30a43018bc9cbb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2019
ms.locfileid: "58467476"
---
### <a name="improved-wcf-chain-trust-certificate-validation-for-nettcp-certificate-authentication"></a>Vylepšené WCF řetězu vztahu důvěryhodnosti ověření certifikátu pro ověřování pomocí certifikátu Net.Tcp

|   |   |
|---|---|
|Podrobnosti|Rozhraní .NET framework 4.7.2 zlepšuje ověřování řetězu důvěryhodných certifikátů při ověřování pomocí certifikátů pomocí zabezpečení přenosu s použitím technologie WCF. Díky tomuto vylepšení je třeba nastavit klientské certifikáty, které se používají k ověřování na server pro ověřování klientů.  Podobně certifikáty serveru, které jsou pro ověřování serveru musí být nakonfigurovaný pro ověřování serveru. Díky této změně pokud kořenový certifikát je zakázaná, ověřování řetězu certifikátů se nezdaří. Stejné změny byl také proveden rozhraní .NET Framework 3.5 a novějších verzích prostřednictvím zabezpečení Windows souhrn. Další informace najdete [tady](https://support.microsoft.com/en-us/help/4055269/security-only-update-for-net-framework-3-5-1-4-5-2-4-6-4-6-1-4-6-2-4-7). Tato změna je ve výchozím a můžete vypnout pomocí nastavení konfigurace.|
|Doporučení|<ul><li>Ověřte, jestli má certifikace serveru a klienta vyžaduje OID rozšířeného použití klíče. V opačném případě aktualizujte vaše certifikace.</li><li>Ověřte, jestli kořenový certifikát je neplatný. Pokud ano, aktualizace kořenového certifikátu.</li><li>Jak se odhlásit ze změny: Pokud certifikát nelze aktualizovat, dočasně rozbíjející změnu lze obejít s následujícím nastavením konfigurace, ale nesouhlasu s generováním změnu ponechá systému citlivé na potíže se zabezpečením.</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;wcf:useLegacyCertificateUsagePolicy&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.2|
|Type|Modul runtime|

