---
ms.openlocfilehash: 0f87f9e9b87860da97ce96e18104b44ec4327c91
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621094"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a>WCF připojení PipeConnection bylo. GetHashAlgorithm teď používá SHA256.

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4.7.1 Windows Communication Foundation používá SHA256 hash k vygenerování náhodných názvů pro pojmenované kanály. V .NET Framework 4,7 a starších verzích používala hodnotu hash SHA1.

#### <a name="suggestion"></a>Návrh

Pokud narazíte na problém s kompatibilitou s touto změnou v .NET Framework 4.7.1 nebo novějším, můžete ji odhlásit přidáním následujícího řádku do <code>&lt;runtime&gt;</code> části app.config souboru:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.7.1|
|Typ|Modul runtime|
