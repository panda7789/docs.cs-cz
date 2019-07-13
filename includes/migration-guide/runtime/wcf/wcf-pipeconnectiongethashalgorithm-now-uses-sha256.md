---
ms.openlocfilehash: 71f61f23a8b17459610d253766a99e594f09428e
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857209"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a>Nyní používá SHA256 WCF PipeConnection.GetHashAlgorithm

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.7.1, Windows Communication Foundation používá hodnotu hash SHA256 pro generování náhodných názvů u pojmenovaných kanálů. V rozhraní .NET Framework 4.7 a dřívějších verzích používá hodnotu hash SHA1.|
|Doporučení|Pokud narazíte na potíže s kompatibilitou s touto změnou v rozhraní .NET Framework 4.7.1 nebo novější, je můžete odhlásit ho tak, že přidáte následující řádek, který <code>&lt;runtime&gt;</code> části souboru app.config:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Scope|Vedlejší|
|Version|4.7.1|
|type|Modul runtime|

