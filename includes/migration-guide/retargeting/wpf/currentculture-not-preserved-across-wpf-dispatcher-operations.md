---
ms.openlocfilehash: bd656478a55856e676853e57f3e7386ea0aa0211
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614544"
---
### <a name="currentculture-is-not-preserved-across-wpf-dispatcher-operations"></a>CurrentCulture se nezachová přes operace dispečera WPF.

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4,6 se změny <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> nebo <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> provedené v rámci a na <xref:System.Windows.Threading.Dispatcher?displayProperty=fullName> konci této operace dispečera ztratí. Podobně se změny <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> nebo <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> provedou mimo operaci dispečera se nemusí projevit, když se tato operace provede. Prakticky řečeno, to znamená, že <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> a <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> změny nemusí tok mezi zpětnými VOLÁNÍMI uživatelského rozhraní WPF a jiným kódem v aplikaci WPF. Důvodem je změna v <xref:System.Threading.ExecutionContext?displayProperty=fullName> tom, že tyto příčiny <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> a <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> budou uloženy v kontextu spuštění počínaje aplikacemi, které cílí na .NET Framework 4,6. Operace dispečera WPF ukládá kontext spuštění, který se používá k zahájení operace a obnovení předchozího kontextu po dokončení operace. Vzhledem k tomu, že <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> a <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> jsou nyní součástí tohoto kontextu, nejsou změny v rámci operace dispečera zachovány mimo operaci.

#### <a name="suggestion"></a>Návrh

Aplikace ovlivněné touto změnou mohou obejít jejich uložením požadovaného <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> nebo <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> v poli a kontrolou všech subjektů dispečera operace (včetně obslužných rutin zpětného volání událostí uživatelského rozhraní), které <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> jsou správné a <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> nastaveny. Alternativně platí, že ExecutionContext Změna základní změny této aplikace WPF ovlivní jenom aplikace cílené na .NET Framework 4,6 nebo novější. Toto přerušení se dá vyhnout tím, že zacílíte na .NET Framework 4.5.2. aplikace, které cílí na .NET Framework 4,6 nebo novější, můžou problém vyřešit také nastavením následujícího přepínače kompatibility:

<pre><code class="lang-csharp">AppContext.SetSwitch(&quot;Switch.System.Globalization.NoAsyncCurrentCulture&quot;, true);&#13;&#10;</code></pre>

Tento problém vyřešila WPF v .NET Framework 4.6.2. Byla také opravena v rozhraní .NET Framework 4,6, 4.6.1 až [KB 3139549](https://support.microsoft.com/kb/3139549). Aplikace cílené na .NET Framework 4,6 nebo novějším budou automaticky dostávat správné chování v aplikacích WPF- <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> ) by se zachovaly napříč operacemi dispečera.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.6         |
| Typ    | Změna cílení |
