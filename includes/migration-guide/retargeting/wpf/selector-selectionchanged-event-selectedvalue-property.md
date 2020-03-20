---
ms.openlocfilehash: e6c93a1bc31c041f36fca3704bca32012a2b42ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859030"
---
### <a name="selector-selectionchanged-event-and-selectedvalue-property"></a>Výběr voličeZměněno a Vlastnost SelectedValue

|   |   |
|---|---|
|Podrobnosti|Počínaje rozhraním .NET Framework 4.7.1, a <xref:System.Windows.Controls.Primitives.Selector> <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> vždy aktualizuje <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> hodnotu své vlastnosti před vyvoláním události při změně jejího výběru. Díky SelectedValue vlastnost konzistentní s ostatními<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>vlastnostmi výběru ( a ), které jsou aktualizovány před vyvoláním události.<p/>V rozhraní .NET Framework 4.7 a starší verze aktualizace SelectedValue došlo před událostí ve většině případů, ale došlo <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> po události, pokud změna výběru byla způsobena změnou vlastnosti.|
|Návrh|Aplikace, které cílí na rozhraní .NET Framework 4.7.1 nebo novější, se <code>&lt;runtime&gt;</code> můžou odhlásit z této změny a používat starší chování přidáním následujícího textu do části konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Aplikace, které cílí na rozhraní .NET Framework 4.7 nebo starší, ale jsou spuštěny v rozhraní .NET <code>&lt;runtime&gt;</code> Framework 4.7.1 nebo novějším, mohou nové chování povolit přidáním následujícího řádku do části souboru .configuration aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.1|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType></li></ul>|
