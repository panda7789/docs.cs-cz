---
ms.openlocfilehash: 318609c15d2e0b9a7ee59b38463735b33ef87974
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803665"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a>Nyní používá SHA256 WCF PipeConnection.GetHashAlgorithm

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.7.1, Windows Communication Foundation používá hodnotu hash SHA256 pro generování náhodných názvů u pojmenovaných kanálů. V rozhraní .NET Framework 4.7 a dřívějších verzích používá hodnotu hash SHA1.|
|Doporučení|Pokud narazíte na potíže s kompatibilitou s touto změnou v rozhraní .NET Framework 4.7.1 nebo novější, je můžete odhlásit ho tak, že přidáte následující řádek, který <code>&lt;runtime&gt;</code> části souboru app.config:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.1|
|Type|Modul runtime|
