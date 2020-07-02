---
ms.openlocfilehash: 78faa5f4008b41bac75c94ce09a58c8227e5b485
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614452"
---
### <a name="currentculture-and-currentuiculture-flow-across-tasks"></a>Tok CurrentCulture a CurrentUICulture napříč úkoly

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4,6 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> a <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> jsou uloženy v vlákně <xref:System.Threading.ExecutionContext?displayProperty=fullName> , které pokračuje v rámci asynchronních operací. To znamená, že se změny <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> nebo <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> se projeví v úlohách, které se později spouštějí asynchronně. To se liší od chování předchozí verze .NET Framework (která by se obnovila <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> a <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> ve všech asynchronních úlohách).

#### <a name="suggestion"></a>Návrh

Aplikace ovlivněné touto změnou se mohou obejít tak, že explicitně nastaví požadovanou <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> nebo <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> jako první operaci v asynchronní úloze. Další možností je, že staré chování (bez toku <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> ) může být zahozeno nastavením následujícího přepínače kompatibility:

```csharp
AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true);
```

Tento problém vyřešila WPF v .NET Framework 4.6.2. Byla také opravena v rozhraní .NET Framework 4,6, 4.6.1 až [KB 3139549](https://support.microsoft.com/kb/3139549). Aplikace cílené na .NET Framework 4,6 nebo novějším budou automaticky dostávat správné chování v aplikacích WPF- <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> ) by se zachovaly napříč operacemi dispečera.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.6         |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType>
- <xref:System.Threading.Thread.CurrentCulture?displayProperty=nameWithType>
- <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=nameWithType>
- <xref:System.Threading.Thread.CurrentUICulture?displayProperty=nameWithType>
