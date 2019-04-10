---
ms.openlocfilehash: b761cb699c4677f815835cdab9c6aa3039f5bb38
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235324"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectiontmove"></a>IsSelected objektu ListBoxItem vazby problém s kolekci ObservableCollection\<T >. Přesunutí

|   |   |
|---|---|
|Podrobnosti|Volání <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> nebo <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> na vázán na kolekci <xref:System.Windows.Controls.ListBox?displayProperty=name> s vybraných položek může vést k nepředvídatelnému chování budoucí výběru nebo unselection z <xref:System.Windows.Controls.ListBox?displayProperty=name> položky.|
|Doporučení|Volání <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=name> a <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=name> místo <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> bude tento problém obejít. Tento problém nebo chyba byla opravena v rozhraní .NET Framework 4.6 a může vyřešit upgradem na verzi rozhraní .NET Framework.|
|Rozsah|Vedlejší|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
