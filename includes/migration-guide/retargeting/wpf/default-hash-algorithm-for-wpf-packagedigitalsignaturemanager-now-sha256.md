---
ms.openlocfilehash: d3e0a61601f60a389b662f6f74934b6e6dc6e663
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614588"
---
### <a name="the-default-hash-algorithm-for-wpf-packagedigitalsignaturemanager-is-now-sha256"></a>Výchozí algoritmus hash pro WPF PackageDigitalSignatureManager je teď SHA256.

#### <a name="details"></a>Podrobnosti

`System.IO.Packaging.PackageDigitalSignatureManager`Poskytuje funkce pro digitální podpisy ve vztahu k balíčkům WPF.  V .NET Framework 4,7 a starších verzích byl jako algoritmus SHA1 použit výchozí algoritmus ( <xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType> ) použitý k podepisování částí balíčku.  Vzhledem k nedávnému vlivu zabezpečení na SHA1 se tato výchozí hodnota změnila na SHA256 počínaje 4.7.1em .NET Framework.  Tato změna má vliv na všechna podepisování balíčků, včetně dokumentů XPS.

#### <a name="suggestion"></a>Návrh

Vývojář, který chce tuto změnu využít při cílení na verzi architektury, .NET Framework 4.7.1 nebo vývojář, který vyžaduje předchozí funkce při cílení na .NET Framework 4.7.1 nebo vyšší, může správně nastavit následující příznak AppContext.  Hodnota true způsobí, že se jako výchozí algoritmus používá SHA1. Výsledkem nepravdivého výsledku v SHA256.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.UseSha1AsDefaultHashAlgorithmForDigitalSignatures=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.7.1       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>
