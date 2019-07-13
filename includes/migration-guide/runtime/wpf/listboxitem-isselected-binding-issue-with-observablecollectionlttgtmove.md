---
ms.openlocfilehash: 778b6973b0a08e89471f9a4aa31a077da2d30c16
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858399"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a>IsSelected objektu ListBoxItem vazby problém s kolekci ObservableCollection&lt;T&gt;. Přesunutí

|   |   |
|---|---|
|Podrobnosti|Volání <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> nebo <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> na vázán na kolekci <xref:System.Windows.Controls.ListBox?displayProperty=name> s vybraných položek může vést k nepředvídatelnému chování budoucí výběru nebo unselection z <xref:System.Windows.Controls.ListBox?displayProperty=name> položky.|
|Doporučení|Volání <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=name> a <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=name> místo <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> bude tento problém obejít. Tento problém nebo chyba byla opravena v rozhraní .NET Framework 4.6 a může vyřešit upgradem na verzi rozhraní .NET Framework.|
|Scope|Vedlejší|
|Version|4.5|
|type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|

