---
ms.openlocfilehash: 8f4ee44e8432bae3537c6f064f564b9f044a7c33
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802475"
---
### <a name="crash-in-selector-when-removing-an-item-from-a-custom-incc-collection"></a>Při odebrání položky z vlastní kolekce INCC k chybě v oblasti pro výběr

|   |   |
|---|---|
|Podrobnosti|<code>T:System.InvalidOperationException</code> Může dojít v následujících situacích:<ul><li>Vlastnost ItemsSource pro <code>T:System.Windows.Controls.Primitives.Selector</code> je kolekce s vlastní implementace <code>T:System.Collections.Specialized.INotifyCollectionChanged</code>.</li><li>Vybraná položka je odebrán z kolekce.</li><li><code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> Má <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> = -1 (značí, že neznámé místo).</li></ul>Zásobník volání výjimky začíná System.Windows.Threading.Dispatcher.VerifyAccess() na na System.Windows.Controls.Primitives.Selector.GetIsSelected (DependencyObject System.Windows.DependencyObject.GetValue (Vlastnost DependencyProperty distribučního bodu) Element) této výjimce může dojít v rozhraní .NET Framework 4.5, pokud má aplikace více než jedno vlákno dispečera. V rozhraní .NET Framework 4.7 výjimky může vzniknout také v aplikacích s jedním vláknem a Dispečerem. Problém je vyřešen v rozhraní .NET Framework 4.7.1.|
|Doporučení|Upgrade na rozhraní .NET Framework 4.7.1.|
|Scope|Vedlejší|
|Version|4.7|
|type|Modul runtime|

