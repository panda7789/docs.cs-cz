---
ms.openlocfilehash: a2d4b7592727ca20ee79867094d6972eb9c4baed
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857203"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a>WCF MsmqSecureHashAlgorithm výchozí hodnota je nyní SHA256

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.7.1, výchozí zprávu podpisový algoritmus ve službě WCF pro zprávy služby Msmq je SHA256. V rozhraní .NET Framework 4.7 a dřívějších verzích je výchozí zprávu podpisový algoritmus SHA1.|
|Doporučení|Pokud narazíte na problémy s kompatibilitou s touto změnou v rozhraní .NET Framework 4.7.1 nebo novější, je můžete odhlásit změny tak, že přidáte následující řádek, který <code>&lt;runtime&gt;</code>části souboru app.config:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Scope|Vedlejší|
|Version|4.7.1|
|type|Modul runtime|

