---
ms.openlocfilehash: ccdf232d743c9e270b6ed21f698998eb95a97399
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621088"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a>Výchozí hodnota MsmqSecureHashAlgorithm WCF je teď SHA256.

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4.7.1 je výchozí algoritmus podepisování zprávy ve službě WCF pro zprávy MSMQ SHA256. V .NET Framework 4,7 a starších verzích je výchozí algoritmus podepisování zprávy SHA1.

#### <a name="suggestion"></a>Návrh

Pokud narazíte na problémy s kompatibilitou s touto změnou .NET Framework 4.7.1 nebo novějším, můžete tuto změnu zrušit přidáním následujícího řádku do <code>&lt;runtime&gt;</code> části app.config souboru:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.7.1|
|Typ|Modul runtime|
