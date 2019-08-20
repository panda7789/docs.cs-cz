---
title: Explicitní implementace rozhraní – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: 498c45ff1c5837f5dcb0d4a80d0e3bb249abd694
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589215"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a>Implementace explicitního rozhraní (Průvodce programováním v C#)
Pokud [Třída](../../language-reference/keywords/class.md) implementuje dvě rozhraní, která obsahují člena se stejnou signaturou, pak implementace tohoto člena na třídu způsobí, že obě rozhraní budou používat tento člen jako svou implementaci. V následujícím příkladu všechna volání `Paint` vyvolávají stejnou metodu.  
  
 [!code-csharp[csProgGuideInheritance#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#39)]  
  
 Pokud dva členy [rozhraní](../../language-reference/keywords/interface.md) neprovádějí stejnou funkci, může však vést k nesprávné implementaci jednoho nebo obou rozhraní. Je možné implementovat člena rozhraní explicitně – vytvořením členu třídy, který je volán pouze prostřednictvím rozhraní a je specifický pro toto rozhraní. Toho lze dosáhnout pojmenováním člena třídy názvem rozhraní a tečkou. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#40)]  
  
 Člen `IControl.Paint` třídy je k dispozici pouze `IControl` prostřednictvím rozhraní a `ISurface.Paint` je k dispozici pouze `ISurface`prostřednictvím. Implementace obou metod jsou oddělené a nejsou k dispozici přímo na třídě. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#41)]  
  
 Explicitní implementace je také použita k vyřešení případů, kde dvě rozhraní každý deklaruje různé členy stejného názvu, jako je například vlastnost a metoda:  
  
 [!code-csharp[csProgGuideInheritance#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#42)]  
  
 Pro implementaci obou rozhraní musí třída použít explicitní implementaci buď pro vlastnost P, nebo pro metodu P nebo pro obojí, aby nedošlo k chybě kompilátoru. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#43)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Třídy a struktury](../classes-and-structs/index.md)
- [Rozhraní](./index.md)
- [Dědičnost](../classes-and-structs/inheritance.md)
