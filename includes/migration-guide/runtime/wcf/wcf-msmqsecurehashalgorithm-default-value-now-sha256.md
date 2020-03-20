---
ms.openlocfilehash: ce8e162e11802de1b06bfbc63d5c55de67ef23df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857203"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a>WCF MsmqSecureHashAlgorithm výchozí hodnota je nyní SHA256

|   |   |
|---|---|
|Podrobnosti|Počínaje rozhraním .NET Framework 4.7.1 je výchozím algoritmem podepisování zpráv v wcf pro zprávy Msmq SHA256. V rozhraní .NET Framework 4.7 a starších verzích je výchozí algoritmus podepisování zpráv SHA1.|
|Návrh|Pokud s touto změnou narazíte na problémy s kompatibilitou v rozhraní .NET Framework 4.7.1 <code>&lt;runtime&gt;</code>nebo novějším, můžete změnu odhlásit přidáním následujícího řádku do části souboru app.config:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.1|
|Typ|Modul runtime|
