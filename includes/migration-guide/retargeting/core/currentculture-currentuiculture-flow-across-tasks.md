---
ms.openlocfilehash: efe8a2dd98865f6a24b65ce0f08eb0c574b708f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804437"
---
### <a name="currentculture-and-currentuiculture-flow-across-tasks"></a>CurrentCulture a CurrentUICulture toku mezi úkoly

|   |   |
|---|---|
|Podrobnosti|Počínaje rozhraním .NET Framework <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> 4.6 a <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> jsou <xref:System.Threading.ExecutionContext?displayProperty=name>uloženy ve vlákně , které toky přes asynchronní operace. To znamená, <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> že <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> změny nebo se projeví v úlohách, které jsou později spuštěny asynchronně. To se liší od chování předchozích verzí rozhraní <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> .NET Framework (které by resetovaly a <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> ve všech asynchronních úlohách).|
|Návrh|Aplikace ovlivněné touto změnou může obejít explicitně nastavení požadované <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> nebo <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> jako první operace v asynchronní úlohy. Alternativně staré chování (netekoucí) <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name>může být přihlášeno nastavením následujícího přepínače kompatibility:<pre><code class="lang-csharp">AppContext.SetSwitch(&quot;Switch.System.Globalization.NoAsyncCurrentCulture&quot;, true);&#13;&#10;</code></pre>Tento problém byl opraven WPF v rozhraní .NET Framework 4.6.2. Byla také opravena v rozhraní .NET Frameworks 4.6, 4.6.1 až [KB 3139549](https://support.microsoft.com/kb/3139549). Aplikace zaměřené na rozhraní .NET Framework 4.6 nebo novější <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name>automaticky získají správné chování v aplikacích WPF - ) budou zachovány v rámci operací dispečera.|
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType></li><li><xref:System.Threading.Thread.CurrentCulture?displayProperty=nameWithType></li><li><xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=nameWithType></li><li><xref:System.Threading.Thread.CurrentUICulture?displayProperty=nameWithType></li></ul>|
