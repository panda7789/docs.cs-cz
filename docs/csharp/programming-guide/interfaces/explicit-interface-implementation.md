---
title: "Implementace explicitního rozhraní (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b746a69484b73a4212c729e02a1256ee1c83ea41
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="explicit-interface-implementation-c-programming-guide"></a>Implementace explicitního rozhraní (Průvodce programováním v C#)
Pokud [třída](../../../csharp/language-reference/keywords/class.md) implementuje dvě rozhraní, které obsahují člen se stejným podpisem, pak implementace tohoto člena k třídě způsobí, že obě rozhraní pro použití tohoto člena jako jejich provádění. V následujícím příkladu, všechna volání do `Paint` vyvolání stejnou metodu.  
  
 [!code-csharp[csProgGuideInheritance#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_1.cs)]  
  
 Pokud dva [rozhraní](../../../csharp/language-reference/keywords/interface.md) členy neprovádět stejnou funkci, ale to může vést k nesprávné implementace jedno nebo obě rozhraní. Je možné implementovat člena rozhraní explicitně – vytvoření člena třídy, která je volána pouze přes rozhraní a je specifická pro toto rozhraní. To se provádí pojmenování člen třídy s názvem rozhraní a období. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_2.cs)]  
  
 Člen třídy `IControl.Paint` je k dispozici prostřednictvím pouze `IControl` rozhraní, a `ISurface.Paint` je k dispozici prostřednictvím `ISurface`. Implementace obě metody jsou samostatné a ani jeden z nich je k dispozici přímo na třídu. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_3.cs)]  
  
 Explicitní implementace se také používá k překladu případech, kde dvě rozhraní deklarovat jiné členy se stejným názvem, jako je například vlastnosti a metody:  
  
 [!code-csharp[csProgGuideInheritance#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_4.cs)]  
  
 Pokud chcete implementovat obě rozhraní, třída má použít explicitní implementace pro vlastnost P nebo metoda P nebo obojí, aby se zabránilo chybě kompilátoru. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#43](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_5.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Rozhraní](../../../csharp/programming-guide/interfaces/index.md)  
 [Dědičnost](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
