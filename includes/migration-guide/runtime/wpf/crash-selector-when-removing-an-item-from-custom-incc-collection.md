---
ms.openlocfilehash: 6da589057cebfbf3f67a46b8d49d3a61f037c4c7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622237"
---
### <a name="crash-in-selector-when-removing-an-item-from-a-custom-incc-collection"></a>Chyba v selektoru při odebírání položky z vlastní kolekce INCC

#### <a name="details"></a>Podrobnosti

K <code>T:System.InvalidOperationException</code> tomu může dojít v následujícím scénáři:<ul><li>ItemsSource pro <code>T:System.Windows.Controls.Primitives.Selector</code> je kolekce s vlastní implementací <code>T:System.Collections.Specialized.INotifyCollectionChanged</code> .</li><li>Vybraná položka je odebrána z kolekce.</li><li><code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code>Má <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> =-1 (indikuje neznámou pozici).</li></ul>Zásobník volání výjimky začíná na System. Windows. Threading. Dispatcher. VerifyAccess () na System. Windows. DependencyObject. GetValue (DependencyProperty DP) na System. Windows. Controls. Primitivs. Selector. GetIsSelected (DependencyObject element) Tato výjimka se může vyskytovat v .NET Framework 4,5, pokud má aplikace více než jedno dispečerský podproces. V .NET Framework 4,7 se výjimka může nacházet také v aplikacích s jedním dispečerem vlákna. Problém je vyřešen .NET Framework 4.7.1.

#### <a name="suggestion"></a>Návrh

Upgradujte na .NET Framework 4.7.1.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4,7|
|Typ|Modul runtime|
