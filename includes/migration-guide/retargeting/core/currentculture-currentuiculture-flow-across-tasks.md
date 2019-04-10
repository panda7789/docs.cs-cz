---
ms.openlocfilehash: efe8a2dd98865f6a24b65ce0f08eb0c574b708f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234378"
---
### <a name="currentculture-and-currentuiculture-flow-across-tasks"></a>CurrentCulture a CurrentUICulture téct přes úlohy

|   |   |
|---|---|
|Podrobnosti|Počínaje .NET Framework 4.6 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> a <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> se ukládají do vlákna <xref:System.Threading.ExecutionContext?displayProperty=name>, který průchodu asynchronních operací. To znamená, že se změní na <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> nebo <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> se projeví v úlohách, které jsou dále běží asynchronně. Tím se liší od chování z předchozích verzí rozhraní .NET Framework (což by resetování <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> a <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> ve všech asynchronních úloh).|
|Doporučení|Touto změnou ovlivněny aplikace může obejít explicitním nastavením požadovaný <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> nebo <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> jako první operace asynchronní úlohy. Alternativně staré chování (ne průchodu <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name>) může být přihlášení ke službě tak, že nastavíte následující přepínače kompatibility:<pre><code class="lang-csharp">AppContext.SetSwitch(&quot;Switch.System.Globalization.NoAsyncCurrentCulture&quot;, true);&#13;&#10;</code></pre>Tento problém byl vyřešen ve WPF v rozhraní .NET Framework 4.6.2. Také jsme opravili .NET Framework 4.6, 4.6.1 prostřednictvím [KB 3139549](https://support.microsoft.com/kb/3139549). Aplikace cílené na rozhraní .NET Framework 4.6 nebo novější, automaticky získá správné chování v aplikaci WPF – <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name>) by zachovaná napříč operace dispečera.|
|Rozsah|Vedlejší|
|Version|4.6|
|Type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType></li><li><xref:System.Threading.Thread.CurrentCulture?displayProperty=nameWithType></li><li><xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=nameWithType></li><li><xref:System.Threading.Thread.CurrentUICulture?displayProperty=nameWithType></li></ul>|
