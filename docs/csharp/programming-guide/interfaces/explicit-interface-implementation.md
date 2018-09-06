---
title: Implementace explicitního rozhraní (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: 4296591875d9843d44a81adfd5937532bcd7fe94
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43892782"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a>Implementace explicitního rozhraní (Průvodce programováním v C#)
Pokud [třídy](../../../csharp/language-reference/keywords/class.md) implementuje dvě rozhraní, které obsahují člena se stejnou signaturou, pak implementace člena třídy způsobí, že obě rozhraní pro použití tohoto člena jako jejich provádění. V následujícím příkladu, všechna volání do `Paint` volání stejné metody.  
  
 [!code-csharp[csProgGuideInheritance#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_1.cs)]  
  
 Pokud dvě [rozhraní](../../../csharp/language-reference/keywords/interface.md) členy nebudete provádět má stejnou funkci, ale to může vést k nesprávná implementace jedno nebo obě rozhraní. Je možné implementovat člen rozhraní, explicitně – vytvoření člena třídy, která je jen volá prostřednictvím rozhraní a je specifické pro rozhraní. Toho lze dosáhnout pojmenování člena třídy se název rozhraní a tečku. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_2.cs)]  
  
 Člen třídy `IControl.Paint` je dostupná jenom `IControl` rozhraní, a `ISurface.Paint` je dostupná jenom `ISurface`. Implementace obě metody jsou oddělené a ani je k dispozici přímo ve třídě. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_3.cs)]  
  
 Explicitní implementaci se také používá k překladu případy, ve kterém dvě rozhraní deklarovat jiné členy se stejným názvem, jako jsou vlastnosti a metody:  
  
 [!code-csharp[csProgGuideInheritance#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_4.cs)]  
  
 Třídy musí implementovat obě rozhraní, použijte explicitní implementaci buď pro vlastnost P nebo metoda P, nebo obojí, aby se zabránilo chybu kompilátoru. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#43](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_5.cs)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Rozhraní](../../../csharp/programming-guide/interfaces/index.md)  
- [Dědičnost](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
