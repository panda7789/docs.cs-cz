---
ms.openlocfilehash: 4a34a64eba72ea24c1d830566565ce4fbee8e5b7
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720987"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a>Pokud je zobrazený popis, událost CellFormatting se neaktivuje.

V <xref:System.Windows.Forms.DataGridView> této části se při stisknutí myši a při výběru přes klávesnici zobrazuje text buňky a popisky chyb. Pokud je zobrazen popis tlačítka, <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> událost není vyvolána.

#### <a name="change-description"></a>Popis změny

Před rozhraním .NET Core 3,1, u <xref:System.Windows.Forms.DataGridView> kterého byla <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> vlastnost nastavena na hodnotu `true` zobrazenou pomocí tlačítka pro text buňky a chyby, když byla buňka najeďte myší. Při výběru buňky prostřednictvím klávesnice (například pomocí klávesy TAB, klávesových zkratek nebo navigace pomocí šipky) nebyly zobrazeny popisy tlačítek. Pokud uživatel buňku upravil a potom <xref:System.Windows.Forms.DataGridView> v režimu úprav byl najeďte na buňku, která sadu vlastností nevytvořila, <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> <xref:System.Windows.Forms.DataGridView.CellFormatting> byla vyvolána událost, která naformátuje text buňky pro zobrazení v buňce.

Aby splňoval standard pro usnadnění přístupu, počínaje rozhraním .NET Core 3,1, <xref:System.Windows.Forms.DataGridView> které má <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> vlastnost nastavenou na, se `true` zobrazí popisy tlačítek pro text buňky a chyby, které nejsou jenom v případě, že je buňka najetí myší, ale také když se vybere přes klávesnici. V důsledku této změny se <xref:System.Windows.Forms.DataGridView.CellFormatting> událost neaktivuje, pokud *not* jsou buňky, které nemají <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> sadu vlastností, nepřesunuty, když <xref:System.Windows.Forms.DataGridView> je v režimu úprav. Událost není vyvolána, protože obsah buňky najetí myší se zobrazí jako popisek namísto zobrazení v buňce.

#### <a name="version-introduced"></a>Představená verze

3.1

#### <a name="recommended-action"></a>Doporučená akce

Refaktorujte jakýkoli kód, který závisí na <xref:System.Windows.Forms.DataGridView.CellFormatting> události, zatímco <xref:System.Windows.Forms.DataGridView> je v režimu úprav.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!-- 

#### Affected APIs

Not detectable via API analysis.

-->
