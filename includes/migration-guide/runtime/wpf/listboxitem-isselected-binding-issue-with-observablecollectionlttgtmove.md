---
ms.openlocfilehash: 44cb833fc93caaa79000147421e1c013f755b9cb
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238023"
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
