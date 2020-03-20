---
ms.openlocfilehash: 44cb833fc93caaa79000147421e1c013f755b9cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "68238023"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a>ListBoxItem IsSelected problém vazby&lt;&gt;s ObservableCollection T . Přesunout

|   |   |
|---|---|
|Podrobnosti|Volání <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> nebo v kolekci <xref:System.Windows.Controls.ListBox?displayProperty=name> vázané na vybrané položky může vést k <xref:System.Windows.Controls.ListBox?displayProperty=name> nevyzpytatelnému chování s budoucím výběrem nebo zrušením výběru položek.|
|Návrh|Volání <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=name> <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=name> a <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> místo toho bude tento problém vyřešit. Alternativně tento problém byl opraven v rozhraní .NET Framework 4.6 a může být vyřešen upgradem na tuto verzi rozhraní .NET Framework.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
