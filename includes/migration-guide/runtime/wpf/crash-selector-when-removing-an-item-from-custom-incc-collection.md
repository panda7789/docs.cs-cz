---
ms.openlocfilehash: a573a78109036b87201b53f72aa8dba6755e7a21
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802475"
---
### <a name="crash-in-selector-when-removing-an-item-from-a-custom-incc-collection"></a>Selhání v selectoru při odebírání položky z vlastní kolekce INCC

|   |   |
|---|---|
|Podrobnosti|Může <code>T:System.InvalidOperationException</code> dojít v následujícím scénáři:<ul><li>ItemsSource pro <code>T:System.Windows.Controls.Primitives.Selector</code> a je kolekce s <code>T:System.Collections.Specialized.INotifyCollectionChanged</code>vlastní implementaci .</li><li>Vybraná položka bude odebrána z kolekce.</li><li>Má <code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> = -1 (označující neznámou polohu).</li></ul>Zásobník volání výjimky začíná na adrese System.Windows.Threading.Dispatcher.VerifyAccess() na adrese System.Windows.DependencyObject.GetValue(DependencyProperty dp) na adrese System.Windows.Controls.Primitives.Selector.GetIsSelected(DependencyObject Element)Tato výjimka může dojít v rozhraní .NET Framework 4.5, pokud aplikace má více než jeden podproces dispečera. V rozhraní .NET Framework 4.7 může dojít k výjimce také v aplikacích s jedním podprocesem dispečera. Problém je vyřešen v rozhraní .NET Framework 4.7.1.|
|Návrh|Upgrade na rozhraní .NET Framework 4.7.1.|
|Rozsah|Vedlejší|
|Version|4.7|
|Typ|Modul runtime|
