---
ms.openlocfilehash: a14395895c6be586c862d1b49aa6bf6669e4203a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "68238008"
---
### <a name="calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a>Volání položek.Aktualizace na WPF ListBox, ListView nebo DataGrid s vybranými položkami může způsobit, že se v prvku zobrazí duplicitní položky

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.5 může volání ListBox.Items.Refresh <xref:System.Windows.Controls.ListBox?displayProperty=name> z kódu, zatímco položky jsou vybrány v a může způsobit, že vybrané položky mají být duplikovány v seznamu. K podobnému problému <xref:System.Windows.Controls.ListView?displayProperty=name> <xref:System.Windows.Controls.DataGrid?displayProperty=name>dochází u a . To je opraveno v rozhraní .NET Framework 4.6.|
|Návrh|Tento problém může být vyřešen programově zrušením <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=name> výběru položek před voláním a jejich opětovným výběrem po dokončení volání. Alternativně tento problém byl opraven v rozhraní .NET Framework 4.6 a může být vyřešen upgradem na tuto verzi rozhraní .NET Framework.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Data.CollectionView.Refresh?displayProperty=nameWithType></li></ul>|
