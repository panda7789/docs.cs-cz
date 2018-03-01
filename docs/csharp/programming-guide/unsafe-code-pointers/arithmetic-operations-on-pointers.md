---
title: "Aritmetické operace na ukazatelích (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 54c439aab8b6cd34a796db8d31f9eabeefddf9f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a>Aritmetické operace na ukazatelích (Průvodce programováním v C#)
Toto téma popisuje použití aritmetické operátory `+` a  **-**  k manipulaci s ukazatele.  
  
> [!NOTE]
>  Nelze provést žádné aritmetické operace na ukazatelích void.  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a>Sčítání a odečítání číselných hodnot do nebo z ukazatele  
 Můžete přidat hodnotu `n` typu [int](../../../csharp/language-reference/keywords/int.md), [Celé_číslo](../../../csharp/language-reference/keywords/uint.md), [dlouho](../../../csharp/language-reference/keywords/long.md), nebo [ulong](../../../csharp/language-reference/keywords/ulong.md) na ukazatel, `p`, libovolného typu, s výjimkou `void*`. Výsledek `p+n` je výsledkem přidání ukazatele `n * sizeof(p) to the address of p`. Podobně `p-n` je ukazatel vyplývající z odečtením `n * sizeof(p)` z adresy `p`.  
  
## <a name="subtracting-pointers"></a>Odečtení ukazatele  
 Můžete také odečtena ukazatele stejného typu. Výsledek je vždy typu `long`. Například pokud `p1` a `p2` jsou ukazatelé typu `pointer-type*`, pak výraz `p1-p2` výsledkem:  
  
 `((long)p1 - (long)p2)/sizeof(pointer_type)`  
  
 Žádné výjimky jsou generovány, pokud doména ukazatele Přetečení aritmetické operace a výsledek závisí na implementaci.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Nezabezpečený kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [Výrazy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)  
 [Manipulace s ukazateli](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [Typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [nezabezpečený](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
