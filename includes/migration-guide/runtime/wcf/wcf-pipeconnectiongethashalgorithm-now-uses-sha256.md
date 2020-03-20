---
ms.openlocfilehash: 318609c15d2e0b9a7ee59b38463735b33ef87974
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857209"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a>WCF PipeConnection.GetHashAlgorithm nyní používá SHA256

|   |   |
|---|---|
|Podrobnosti|Počínaje rozhraním .NET Framework 4.7.1 používá nadace Windows Communication Foundation k generování náhodných názvů pojmenovaných kanálů hash SHA256. V rozhraní .NET Framework 4.7 a starších verzích používala hašiš SHA1.|
|Návrh|Pokud s touto změnou narazíte na problém s kompatibilitou v rozhraní .NET Framework 4.7.1 <code>&lt;runtime&gt;</code> nebo novějším, můžete ji odhlásit přidáním následujícího řádku do části souboru app.config:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.1|
|Typ|Modul runtime|
