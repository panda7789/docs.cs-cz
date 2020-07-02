---
ms.openlocfilehash: dfdb62e8dd6db67d4fd12aba93928f4615e3f284
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614605"
---
### <a name="tabcontrol-selectionchanged-event-and-selectedcontent-property"></a>Událost TabControl SelectionChanged a vlastnost SelectedContent

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4.7.1 <xref:System.Windows.Controls.TabControl> aktualizuje hodnotu vlastnosti před vyvoláním <xref:System.Windows.Controls.TabControl.SelectedContent> <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> události, když se změní její výběr. V .NET Framework 4,7 a starších verzích se po události stala aktualizace SelectedContent.

#### <a name="suggestion"></a>Návrh

Aplikace, které cílí na .NET Framework 4.7.1 nebo novější, si mohou tuto změnu odhlásit a použít starší chování tak, že do `<runtime>` části konfiguračního souboru aplikace přidáte následující:

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

Aplikace, které cílí na .NET Framework 4,7 nebo starší, ale běží na .NET Framework 4.7.1 nebo novějším, můžou nové chování povolit přidáním následujícího řádku do `<runtime>` oddílu souboru Application. Configuration:

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.7.1       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType>
