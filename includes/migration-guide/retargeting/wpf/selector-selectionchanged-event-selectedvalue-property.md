---
ms.openlocfilehash: 0ef39d67cd4335658658f5772b5bce49d827cad0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614597"
---
### <a name="selector-selectionchanged-event-and-selectedvalue-property"></a>Událost SelectionChanged a vlastnost SelectedValue selektoru

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4.7.1, <xref:System.Windows.Controls.Primitives.Selector> vždy aktualizuje hodnotu vlastnosti před vyvoláním <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> události, když se změní její výběr. Tím se vlastnost SelectedValue v souladu s ostatními vlastnostmi výběru ( <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> a <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> ), které jsou před vyvoláním události aktualizovány.<p/>V .NET Framework 4,7 a dřívějších verzích nastala aktualizace SelectedValue před událostí ve většině případů, ale ta se stala po události, kdy Změna výběru byla způsobena změnou <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> Vlastnosti.

#### <a name="suggestion"></a>Návrh

Aplikace, které cílí na .NET Framework 4.7.1 nebo novější, si mohou tuto změnu odhlásit a použít starší chování tak, že do `<runtime>` části konfiguračního souboru aplikace přidáte následující:

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

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
