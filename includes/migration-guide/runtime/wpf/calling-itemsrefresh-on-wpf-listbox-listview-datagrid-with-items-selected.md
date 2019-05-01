---
ms.openlocfilehash: de73145273ad5aa5c19de55525417cfc3305b86d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62088461"
---
### <a name="calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a>Volání Items.Refresh WPF ListBox, ListView nebo prvek DataGrid s vybraných položek může způsobit duplicitní položky se zobrazí v elementu

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.5, když jsou vybrané položky v volání ListBox.Items.Refresh z kódu <xref:System.Windows.Controls.ListBox?displayProperty=name> může způsobit, že vybrané položky, které chcete zkopírovat do seznamu. Dochází k podobnému problému s <xref:System.Windows.Controls.ListView?displayProperty=name> a <xref:System.Windows.Controls.DataGrid?displayProperty=name>. Tento problém je vyřešený v rozhraní .NET Framework 4.6.|
|Doporučení|Tento problém může pracoval kolem položek před zrušením programově <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=name> nazývá a potom znovu vyberete je po dokončení volání. Tento problém nebo chyba byla opravena v rozhraní .NET Framework 4.6 a může vyřešit upgradem na verzi rozhraní .NET Framework.|
|Rozsah|Vedlejší|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Data.CollectionView.Refresh?displayProperty=nameWithType></li></ul>|
