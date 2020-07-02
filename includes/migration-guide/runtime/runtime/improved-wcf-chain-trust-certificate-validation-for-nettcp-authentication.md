---
ms.openlocfilehash: 4a0f866bc11a06ea6fcd4ab3a8320bbb6ffa5d91
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621076"
---
### <a name="improved-wcf-chain-trust-certificate-validation-for-nettcp-certificate-authentication"></a>Vylepšené ověřování certifikátu důvěryhodnosti řetězu WCF pro ověřování certifikátů NET. TCP

#### <a name="details"></a>Podrobnosti

.NET Framework 4.7.2 vylepšuje ověřování certifikátů důvěryhodnosti řetězu při použití ověřování certifikátů s zabezpečením přenosu pomocí WCF. S tímto vylepšením je nutné pro ověřování klientů nakonfigurovat klientské certifikáty, které se používají k ověřování na serveru.  Podobně serverové certifikáty, které jsou pro ověřování serveru, musí být nakonfigurovány pro ověřování serveru. V případě této změny je-li kořenový certifikát zakázán, ověření řetězu certifikátů se nezdařilo. Stejná změna byla také provedena v .NET Framework 3,5 a novějších verzích prostřednictvím souhrnu zabezpečení systému Windows. Další informace najdete [tady](https://support.microsoft.com/help/4055269/security-only-update-for-net-framework-3-5-1-4-5-2-4-6-4-6-1-4-6-2-4-7). Tato změna je ve výchozím nastavení zapnutá a dá se vypnout nastavením konfigurace.

#### <a name="suggestion"></a>Návrh

<ul><li>Ověřte, zda má server a certifikace klienta požadované identifikátory objektu EKU. V takovém případě aktualizujte certifikaci.</li><li>Ověřte, zda je kořenový certifikát neplatný. V takovém případě aktualizujte kořenový certifikát.</li><li>Jak se odhlásit ze změny: Pokud certifikát nemůžete aktualizovat, můžete dočasnou změnu dočasně obejít s následujícím nastavením konfiguračního. Pokud ale nechcete, aby se váš systém mohl zvýšit, dojde k potížím se zabezpečením.</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;wcf:useLegacyCertificateUsagePolicy&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.7.2|
|Typ|Modul runtime|
