---
ms.openlocfilehash: 710d1517397f423fa40cc0c4a26c3499aac6179e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620082"
---
### <a name="calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a>Volání položek. aktualizace ovládacího prvku ListBox, ListView nebo DataGrid se zvolenými položkami může způsobit, že se v elementu objeví duplicitní položky.

#### <a name="details"></a>Podrobnosti

V .NET Framework 4,5 se voláním ListBox. Items. Refresh z kódu, když jsou vybrané položky v, <xref:System.Windows.Controls.ListBox?displayProperty=fullName> může způsobit, že vybrané položky budou duplikovány v seznamu. K podobnému problému dochází u <xref:System.Windows.Controls.ListView?displayProperty=fullName> a <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> . Toto je opraveno v .NET Framework 4,6.

#### <a name="suggestion"></a>Návrh

K tomuto problému může dojít v případě, že jste před <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=fullName> voláním vyvolali nevybrané položky a pak je znovu vyberete po dokončení volání. Případně byl tento problém opravený v .NET Framework 4,6 a může se řešit upgradem na verzi .NET Framework.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Windows.Data.CollectionView.Refresh?displayProperty=nameWithType></li></ul>|
