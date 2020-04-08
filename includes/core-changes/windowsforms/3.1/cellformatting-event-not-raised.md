---
ms.openlocfilehash: b736ab743a628fdcbc53c5ee51551e5dad986885
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888110"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a>Událost CellFormatting není vyvolána, pokud je zobrazen popisek

A <xref:System.Windows.Forms.DataGridView> nyní zobrazuje text buňky a popisky chyb, když je hovered myší a když je vybrán pomocí klávesnice. Pokud je zobrazen popisek, <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> událost není vyvolána.

#### <a name="change-description"></a>Popis změny

Před .NET Core 3.1, <xref:System.Windows.Forms.DataGridView> který <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> měl `true` vlastnost nastavenou na zobrazení popisku pro text buňky a chyby, když byla buňka jehována myší. Popisky nebyly zobrazeny, když byla buňka vybrána pomocí klávesnice (například pomocí klávesy Tab, klávesových zkratek nebo navigace se šipkami). Pokud uživatel upravil buňku a poté, když <xref:System.Windows.Forms.DataGridView> byl ještě v režimu úprav, se <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> pohyboval nad <xref:System.Windows.Forms.DataGridView.CellFormatting> buňkou, která neměla nastavenou vlastnost, byla vyvolána událost, která formátuje text buňky pro zobrazení v buňce.

Chcete-li splnit standardy usnadnění přístupu, <xref:System.Windows.Forms.DataGridView> počínaje .NET Core 3.1, který má <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> vlastnost nastavena na `true` zobrazení popisů pro text buňky a chyby nejen při pohyblivosti buňky, ale také když je vybrána pomocí klávesnice. V důsledku této změny <xref:System.Windows.Forms.DataGridView.CellFormatting> *není* událost vyvolána, když jsou <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> buňky, které nemají <xref:System.Windows.Forms.DataGridView> sadu vlastností, vztyčeny, když je v režimu úprav. Událost není vyvolána, protože obsah buňky s odkazem je zobrazen jako popisek namísto zobrazení v buňce.

#### <a name="version-introduced"></a>Zavedená verze

3.1

#### <a name="recommended-action"></a>Doporučená akce

Refaktorovat jakýkoli kód, <xref:System.Windows.Forms.DataGridView.CellFormatting> který <xref:System.Windows.Forms.DataGridView> závisí na události, zatímco je v režimu úprav.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádný

<!-- 

### Affected APIs

Not detectable via API analysis.

-->
