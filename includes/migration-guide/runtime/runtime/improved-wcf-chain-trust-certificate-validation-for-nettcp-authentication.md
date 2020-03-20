---
ms.openlocfilehash: e69ed64390504af872fa6785aa0b7d6c4db84ef0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "69671031"
---
### <a name="improved-wcf-chain-trust-certificate-validation-for-nettcp-certificate-authentication"></a>Vylepšené ověřování certifikátu důvěryhodnosti řetězce WCF pro ověřování certifikátů Net.Tcp

|   |   |
|---|---|
|Podrobnosti|Rozhraní .NET Framework 4.7.2 zlepšuje ověřování důvěryhodných certifikátů řetězce při použití ověřování certifikátu se zabezpečením přenosu pomocí wcf. S tímto vylepšením musí být klientské certifikáty, které se používají k ověření na serveru, nakonfigurovány pro ověřování klientů.  Podobně serverové certifikáty, které jsou určeny pro ověřování serveru, musí být nakonfigurovány pro ověřování serveru. S touto změnou, pokud je kořenový certifikát zakázán, ověření řetězu certifikátu se nezdaří. Stejná změna byla provedena také rozhraní .NET Framework 3.5 a novější verze prostřednictvím kumulativní zabezpečení systému Windows. Více informací naleznete [zde](https://support.microsoft.com/help/4055269/security-only-update-for-net-framework-3-5-1-4-5-2-4-6-4-6-1-4-6-2-4-7). Tato změna je ve výchozím nastavení zapnutá a lze ji vypnout nastavením konfigurace.|
|Návrh|<ul><li>Ověřte, zda má certifikace serveru a klienta požadovanou identifikátor EKU OID. Pokud ne, aktualizujte certifikaci.</li><li>Ověřte, zda je kořenový certifikát neplatný. Pokud ano, aktualizujte kořenový certifikát.</li><li>Jak se odhlásit ze změny: Pokud nelze aktualizovat certifikát, můžete obejít porušení změny dočasně s následujícím nastavením konfigurace, Nicméně, odhlášení ze změny opustí váš systém zranitelný vůči problému se zabezpečením.</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;wcf:useLegacyCertificateUsagePolicy&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.2|
|Typ|Modul runtime|
