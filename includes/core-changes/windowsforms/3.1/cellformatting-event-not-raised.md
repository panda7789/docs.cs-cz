---
ms.openlocfilehash: add3ff8faed2e7fab245e5b6f1b9158b7bdd06f5
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567344"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a>Pokud je zobrazený popis, událost CellFormatting se neaktivuje.

<xref:System.Windows.Forms.DataGridView> nyní zobrazuje text buňky a popisky chyb, když je najede myší a když je vyberete prostřednictvím klávesnice. Pokud se zobrazí popis, událost <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> se neaktivuje.

#### <a name="change-description"></a>Změnit popis

Před rozhraním .NET Core 3,1 se <xref:System.Windows.Forms.DataGridView>, která měla vlastnost <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> nastavená na `true`, ukázala popis pro text buňky a chyby, když buňka nacházela myší. Při výběru buňky prostřednictvím klávesnice (například pomocí klávesy TAB, klávesových zkratek nebo navigace pomocí šipky) nebyly zobrazeny popisy tlačítek. Pokud uživatel upravil buňku a poté, <xref:System.Windows.Forms.DataGridView> byla v režimu úprav ponechána nad buňkou, která nemá nastavenou vlastnost <xref:System.Windows.Forms.DataGridViewCell.ToolTipText>, byla vyvolána událost <xref:System.Windows.Forms.DataGridView.CellFormatting> pro formátování textu buňky pro zobrazení v buňce.

Aby se dosáhlo standardů přístupnosti, počínaje platformou .NET Core 3,1, <xref:System.Windows.Forms.DataGridView>, která má vlastnost <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> nastavenou na `true`, se zobrazí popisy textu buňky a chyby, které nejsou jenom v případě, že je buňka najetí myší, ale také když se vybere přes klávesnici. V důsledku této změny se událost <xref:System.Windows.Forms.DataGridView.CellFormatting> *nevygeneruje* , když se buňky, které nemají sadu vlastností <xref:System.Windows.Forms.DataGridViewCell.ToolTipText>, nepřesunou myší, zatímco <xref:System.Windows.Forms.DataGridView> je v režimu úprav. Událost není vyvolána, protože obsah buňky najetí myší se zobrazí jako popisek namísto zobrazení v buňce.

#### <a name="version-introduced"></a>Představená verze

3,1

#### <a name="recommended-action"></a>Doporučená akce

Refaktorujte jakýkoli kód, který závisí na události <xref:System.Windows.Forms.DataGridView.CellFormatting>, zatímco <xref:System.Windows.Forms.DataGridView> je v režimu úprav.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Nedá se detekovat přes analýzu rozhraní API.

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
