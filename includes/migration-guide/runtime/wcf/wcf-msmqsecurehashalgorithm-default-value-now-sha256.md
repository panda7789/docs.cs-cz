---
ms.openlocfilehash: ce8e162e11802de1b06bfbc63d5c55de67ef23df
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803728"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a>WCF MsmqSecureHashAlgorithm výchozí hodnota je nyní SHA256

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.7.1, výchozí zprávu podpisový algoritmus ve službě WCF pro zprávy služby Msmq je SHA256. V rozhraní .NET Framework 4.7 a dřívějších verzích je výchozí zprávu podpisový algoritmus SHA1.|
|Doporučení|Pokud narazíte na problémy s kompatibilitou s touto změnou v rozhraní .NET Framework 4.7.1 nebo novější, je můžete odhlásit změny tak, že přidáte následující řádek, který <code>&lt;runtime&gt;</code>části souboru app.config:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.1|
|Type|Modul runtime|
