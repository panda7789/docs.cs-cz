---
ms.openlocfilehash: 22c67c687f5581c181acc4aeab8910c4467fd424
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858455"
---
### <a name="calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a>Volání Items.Refresh WPF ListBox, ListView nebo prvek DataGrid s vybraných položek může způsobit duplicitní položky se zobrazí v elementu

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.5, když jsou vybrané položky v volání ListBox.Items.Refresh z kódu <xref:System.Windows.Controls.ListBox?displayProperty=name> může způsobit, že vybrané položky, které chcete zkopírovat do seznamu. Dochází k podobnému problému s <xref:System.Windows.Controls.ListView?displayProperty=name> a <xref:System.Windows.Controls.DataGrid?displayProperty=name>. Tento problém je vyřešený v rozhraní .NET Framework 4.6.|
|Doporučení|Tento problém může být pracoval kolem programově zrušením výběru položek před <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=name> nazývá a potom znovu vyberete je po dokončení volání. Tento problém nebo chyba byla opravena v rozhraní .NET Framework 4.6 a může vyřešit upgradem na verzi rozhraní .NET Framework.|
|Scope|Vedlejší|
|Version|4.5|
|type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Data.CollectionView.Refresh?displayProperty=nameWithType></li></ul>|

