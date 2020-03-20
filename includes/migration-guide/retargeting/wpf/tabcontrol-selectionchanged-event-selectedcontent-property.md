---
ms.openlocfilehash: 923105114c9e8da02c61c842cc02bed1ead3eddc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859013"
---
### <a name="tabcontrol-selectionchanged-event-and-selectedcontent-property"></a>TabControl SelectionZměněn událost a Vlastnost SelectedContent

|   |   |
|---|---|
|Podrobnosti|Počínaje rozhraním .NET Framework 4.7.1 aktualizuje <xref:System.Windows.Controls.TabControl> <xref:System.Windows.Controls.TabControl.SelectedContent> hodnotu své <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> vlastnosti před vyvoláním události při změně jejího výběru. V rozhraní .NET Framework 4.7 a starších verzích došlo po události k aktualizaci selectedcontent.|
|Návrh|Aplikace, které cílí na rozhraní .NET Framework 4.7.1 nebo novější, se <code>&lt;runtime&gt;</code> můžou odhlásit z této změny a používat starší chování přidáním následujícího textu do části konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Aplikace, které cílí na rozhraní .NET Framework 4.7 nebo starší, ale jsou spuštěny v rozhraní .NET <code>&lt;runtime&gt;</code> Framework 4.7.1 nebo novějším, mohou nové chování povolit přidáním následujícího řádku do části souboru .configuration aplikace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.1|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType></li></ul>|
