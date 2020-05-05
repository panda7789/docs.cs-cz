---
ms.openlocfilehash: b736ab743a628fdcbc53c5ee51551e5dad986885
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888110"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a>Pokud je zobrazený popis, událost CellFormatting se neaktivuje.

V <xref:System.Windows.Forms.DataGridView> této části se při stisknutí myši a při výběru přes klávesnici zobrazuje text buňky a popisky chyb. Pokud je zobrazen popis tlačítka, <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> událost není vyvolána.

#### <a name="change-description"></a>Popis změny

Před rozhraním .NET Core 3,1, <xref:System.Windows.Forms.DataGridView> u kterého byla <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> vlastnost nastavena na `true` hodnotu zobrazenou pomocí tlačítka pro text buňky a chyby, když byla buňka najeďte myší. Při výběru buňky prostřednictvím klávesnice (například pomocí klávesy TAB, klávesových zkratek nebo navigace pomocí šipky) nebyly zobrazeny popisy tlačítek. Pokud uživatel buňku upravil a potom v režimu úprav <xref:System.Windows.Forms.DataGridView> byl najeďte na buňku, která sadu <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> vlastností nevytvořila, byla vyvolána <xref:System.Windows.Forms.DataGridView.CellFormatting> událost, která naformátuje text buňky pro zobrazení v buňce.

Aby splňoval standard pro usnadnění přístupu, počínaje rozhraním .NET Core <xref:System.Windows.Forms.DataGridView> 3,1, které <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> má vlastnost nastavenou na, se `true` zobrazí popisy tlačítek pro text buňky a chyby, které nejsou jenom v případě, že je buňka najetí myší, ale také když se vybere přes klávesnici. V <xref:System.Windows.Forms.DataGridView.CellFormatting> důsledku této *změny se událost neaktivuje* , pokud jsou buňky, které nemají sadu <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> vlastností, nepřesunuty, když <xref:System.Windows.Forms.DataGridView> je v režimu úprav. Událost není vyvolána, protože obsah buňky najetí myší se zobrazí jako popisek namísto zobrazení v buňce.

#### <a name="version-introduced"></a>Představená verze

3.1

#### <a name="recommended-action"></a>Doporučená akce

Refaktorujte jakýkoli kód, který závisí na <xref:System.Windows.Forms.DataGridView.CellFormatting> události, zatímco <xref:System.Windows.Forms.DataGridView> je v režimu úprav.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!-- 

### Affected APIs

Not detectable via API analysis.

-->
